---
tags: [Azure, Development/SQL Server]
title: Creating an Azure AD User in SQL Server
created: '2023-06-08T04:33:58.533Z'
modified: '2023-06-11T23:35:52.656Z'
---

# Creating an Azure AD User in SQL Server

```sql
use GasLFH
CREATE LOGIN [david.hirschfeld@shell.com] FROM EXTERNAL PROVIDER
CREATE USER [david.hirschfeld@shell.com] FROM EXTERNAL PROVIDER
ALTER ROLE db_datareader ADD MEMBER [david.hirschfeld@shell.com];
ALTER ROLE db_datawriter ADD MEMBER [david.hirschfeld@shell.com];
GRANT INSERT ON GasForecast.dbo.MIRN TO [david.hirschfeld@shell.com];

SELECT name, type_desc, type, is_disabled
FROM sys.server_principals
WHERE type_desc like 'external%'
ORDER BY name
```

