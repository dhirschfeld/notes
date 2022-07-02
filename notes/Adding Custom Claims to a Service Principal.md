---
deleted: true
tags: [Azure/AD]
title: Adding Custom Claims to a Service Principal
created: '2021-04-08T03:29:44.544Z'
modified: '2021-04-08T23:53:46.194Z'
---

# Adding Custom Claims to a Service Principal

* https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-claims-mapping
* https://goodworkaround.com/2019/11/15/adding-custom-attributes-to-the-azure-ad-openid-connect-id-token/

e.g. adding a custom policy to include the `sAMAccountName` claim to a service principal token:
```powershell
$policyTemplate = @"
{
    "ClaimsMappingPolicy": {
        "Version": 1,
        "IncludeBasicClaimSet": "true",
        "ClaimsSchema": [
            {
                "Source": "user",
                "ID": "onpremisessamaccountname",
                "JwtClaimType": "samid"
            }
        ]
    }
}
"@
$policy = New-AzureADPolicy -Type "ClaimsMappingPolicy" -Definition ($policyTemplate) -DisplayName "sAMAccountName"
$servicePrincipal = Get-AzureADServicePrincipal -SearchString JupyterHub
Add-AzureADServicePrincipalPolicy -Id $servicePrincipal.ObjectId -RefObjectId $policy.Id
```
***Note:*** you need to also set `"acceptMappedClaims": true` in the application (json) manifest

Requires the `AzureAdPreview` module (which only works in old PowerShell, not PowerShell Core):
```powershell
Install-Module -Name AzureADPreview
Import-Module AzureADPreview
Connect-AzureAD -Confirm
```

