---
tags: [Python/Database]
title: sqlalchemy Create Table
created: '2023-06-13T07:07:15.043Z'
modified: '2023-06-13T07:08:47.070Z'
---

# `sqlalchemy` Create Table

```python

import sqlalchemy as sa
from sqlalchemy.dialects.mssql import DATETIME2 as DateTime


meta = sa.MetaData()


table = sa.Table(
    "MyTable",
    meta,
    sa.Column(
        "insert_timestamp",
        DateTime,
        primary_key=True,
        server_default=sa.sql.func.now(),
        comment="The timestamp when the value was inserted.",
    ),
    sa.Column(
        "published_by",
        sa.String(64),
        server_default=sa.text("lower(system_user)"),
        comment="The UID which inserted the value.",
    ),
    sa.Column(
        "provider",
        sa.String(64),
        primary_key=True,
        comment="The provider.",
    ),
    sa.Column(
        "value",
        sa.Float(53),
        nullable=False,
        comment="The value.",
    ),
    schema="forecast",
)
```
