---
tags: [Python/Database]
title: Connect using AccessToken
created: '2023-05-25T03:24:23.181Z'
modified: '2023-06-06T01:58:22.095Z'
---

# Connect using AccessToken

```python
import os
from urllib.parse import quote_plus
import pandas as pd
import sqlalchemy as sa


cs = (
  f"database={database};"
  f"server=tcp:{server},1433;"
  "driver={ODBC Driver 18 for SQL Server};"
  "encrypt=yes;"
  "trustservercertificate=no;"
  "connection timeout=30;"
  f"uid={uid};"
  "authentication=ActiveDirectoryInteractive"
)
engine = sa.create_engine(f"mssql+pyodbc:///?odbc_connect={quote_plus(cs)}")
with engine.connect() as conn:
    df = pd.read_sql("select * from dbo.GasForecastModel", conn)
```

```python
import struct
from azure.identity import AzureCliCredential

credential = AzureCliCredential()
token = credential.get_token('https://database.windows.net/.default')

# The ACCESSTOKEN is a variable-length structure consisting of a 4-byte length
# followed by length bytes of opaque data that form the access token. Because
# of how SQL Server handles access tokens, one obtained via an OAuth 2.0 JSON
# response must be expanded so that each byte is followed by a zero padding byte
# https://learn.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver16#authenticating-with-an-access-token
N = 2*len(token.token)
odbc_token = bytearray(N + 4)
odbc_token[:4] = struct.pack("=i", N)
odbc_token[4::2] = bytes(token.token, "utf-8")
SQL_COPT_SS_ACCESS_TOKEN = 1256

cs = (
  f"database={database};"
  f"server=tcp:{server},1433;"
  "driver={ODBC Driver 18 for SQL Server};"
  "encrypt=yes;"
  "trustservercertificate=no;"
  "connection timeout=30;"
)
with pyodbc.connect(cs, attrs_before={SQL_COPT_SS_ACCESS_TOKEN: odbc_token}) as conn:
    res, = conn.execute("select system_user").fetchall()[0]
    print(res)
```

* https://docs.sqlalchemy.org/en/20/dialects/mssql.html#connecting-to-databases-with-access-tokens

```python
engine = sa.create_engine(f"mssql+pyodbc:///?odbc_connect={quote_plus(cs)}")

@sa.event.listens_for(engine, "do_connect")
def provide_token(dialect, conn_rec, cargs, cparams):
    cargs[0] = cargs[0].replace(";Trusted_Connection=Yes", "")
    # create token credential
    raw_token = credential.get_token('https://database.windows.net/.default').token.encode("utf-16-le")
    token_struct = struct.pack(f"<I{len(raw_token)}s", len(raw_token), raw_token)
    # apply it to keyword arguments
    cparams["attrs_before"] = {SQL_COPT_SS_ACCESS_TOKEN: token_struct}
```


```python
import os
import struct
import sys
from urllib.parse import quote_plus

import pandas as pd
import sqlalchemy as sa


def provide_token(dialect, conn_rec, cargs, cparams):
    """A hook to alter an `sqlalchemy` connection to add the
    `AzureCliCredential` token.
    """
    global credential
    token = credential.get_token('https://database.windows.net/.default')
    odbc_token = token.token.encode("utf-16-le")
    odbc_token = struct.pack(f"<I{len(odbc_token)}s", len(odbc_token), odbc_token)
    SQL_COPT_SS_ACCESS_TOKEN = 1256
    cparams["attrs_before"] = {SQL_COPT_SS_ACCESS_TOKEN: odbc_token}
    cargs[0] = cargs[0].replace(";Trusted_Connection=Yes", "")


def get_engine(**kwargs) -> sa.engine.Engine:
    """Creates an `sqlalchemy.engine.Engine` instance using
    `ActiveDirectoryInteractive` authentication on Windows and
    `AzureCliCredential` on Linux.

    Parameters
    ----------
    kwargs : dict
        Connection kwargs to override the default values

    """
    default_server = os.environ.get(
        "DB_OUTDB_HOST",
        "seautnspwr-dev-sqlmi.9a5dbe35ce37.database.windows.net"
    )
    server = kwargs.pop("server", default_server)
    connection_kwargs = dict(
        driver="{ODBC Driver 18 for SQL Server}",
        server=f"tcp:{server},1433",
        database="GasLFH",
        encrypt="yes",
        trustservercertificate="no",
    )
    connection_kwargs["connection timeout"] = 30
    if sys.platform == "win32":
        connection_kwargs["authentication"] = "ActiveDirectoryInteractive"
        connection_kwargs["uid"] = f"{os.environ['USERNAME']}@shell.com"

    connection_kwargs = {**connection_kwargs, **kwargs}
    cs = ";".join(f"{key}={value}" for key, value in connection_kwargs.items())
    engine = sa.create_engine(f"mssql+pyodbc:///?odbc_connect={quote_plus(cs)}")
    if sys.platform != "win32":
        from azure.identity import AzureCliCredential
        global credential
        credential = AzureCliCredential()
        sa.event.listens_for(engine, "do_connect")(provide_token)

    return engine
```



