---
tags: [Azure]
title: Mount Azure Files SMB Share in Windows Explorer
created: '2023-01-23T11:46:08.615Z'
modified: '2023-01-24T01:03:59.050Z'
---

# Mount Azure Files SMB Share in Windows Explorer


```powershell
$connectTestResult = Test-NetConnection -ComputerName myaccount.file.core.windows.net -Port 445
if ($connectTestResult.TcpTestSucceeded) {
    # Save the password so the drive will persist on reboot
    cmd.exe /C "cmdkey /add:`"myaccount.file.core.windows.net`" /user:`"localhost\myaccount`" /pass:`"******/******`""
    # Mount the drive
    New-PSDrive -Name J -PSProvider FileSystem -Root "\\myaccount.file.core.windows.net\jupyter" -Persist
} else {
    Write-Error -Message "Unable to reach the Azure storage account via port 445. Check to make sure your organization or ISP is not blocking port 445, or use Azure P2S VPN, Azure S2S VPN, or Express Route to tunnel SMB traffic over a different port."
}
```

```powershell
$resource_group = "AZ-AS-RGP-VN-N-SEQ01619-jupyter-e2b9c1"
$account_name = "azasstavnnseq01619zca13"
$account_key = $(az storage account keys list -g $resource_group -n $account_name --query [0].value --output tsv)

$secure_key = ConvertTo-SecureString -String $account_key -AsPlainText -Force
$creds = New-Object System.Management.Automation.PSCredential -ArgumentList ("Azure\${account_name}", $secure_key)
$drive = New-PSDrive -Name J -PSProvider FileSystem -Root "\\\${account_name}.file.core.windows.net\jupyter" -Credential $creds -Persist
```

