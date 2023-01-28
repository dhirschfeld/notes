---
tags: [Python, Python/Database]
title: Stringify an SQLAlchemy Query
created: '2022-11-23T22:50:17.083Z'
modified: '2023-01-28T05:38:53.755Z'
---

# Stringify an SQLAlchemy Query

* https://docs.sqlalchemy.org/en/20/faq/sqlexpressions.html#rendering-bound-parameters-inline
* https://copdips.com/2020/06/compiling-sqlalchemy-query-to-nearly-real-raw-sql-query.html


```python
def compile_query(query, *, dialect: str):
    from sqlalchemy.sql.compiler import SQLCompiler
    dialect = get_dialect(dialect)
    compiled = SQLCompiler(dialect, query)
    SQL = str(compiled)
    params = compiled.params
    if dialect.positional:
        params = tuple(params[key] for key in compiled.positiontup)
    return SQL, params


def get_dialect(dialect: str) -> Dialect:
    from sqlalchemy.dialects import mssql
    if dialect == 'mssql':
        return mssql.dialect()
    elif dialect == 'turbocbc':
        dialect = mssql.dialect()
        dialect.default_paramstyle = 'qmark'
        dialect.paramstyle = 'qmark'
        dialect.positional = True
        return dialect
    else:
        msg = (
            f"Dialect `{dialect}` is not implemented!\n"
            "Valid dialects are {mssql|turbodbc}"
        )
        raise NotImplementedError(msg)
```
