---
tags: [Python/Database]
title: Connect using AccessToken
created: '2023-05-25T03:24:23.181Z'
modified: '2023-05-25T03:36:45.055Z'
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

