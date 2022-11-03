---
tags: [Development, Development/SQL Server]
title: List Permissions by User
created: '2022-11-02T07:00:04.707Z'
modified: '2022-11-02T07:01:06.874Z'
---

# List Permissions by User

```sql
select
	  principal.name,
    permission.class_desc,
    permission.permission_name,
    permission.state_desc
from
	  sys.database_permissions permission
inner join
	  sys.database_principals principal
on
	  permission.grantee_principal_id = principal.principal_id 
where
	  principal.name = 'username'
```

