---
tags: [Kubernetes/AKS]
title: Querying Pod Logs in Azure Monitor
created: '2022-11-30T02:28:45.150Z'
modified: '2022-11-30T02:31:52.882Z'
---

# Querying Pod Logs in Azure Monitor

* https://blog.coffeeapplied.com/using-azure-monitor-logs-with-azure-kubernetes-service-aks-c0b0625295d1

```kusto
let startTimestamp = ago(1h);
KubePodInventory
| where TimeGenerated > startTimestamp
| project ContainerID, PodName=Name
| distinct ContainerID, PodName
| join
(
    ContainerLog
    | where TimeGenerated > startTimestamp
)
on ContainerID
// at this point before the next pipe, columns from both tables are available to be "projected". Due to both 
// tables having a "Name" column, we assign an alias as PodName to one column which we actually want
| project TimeGenerated, PodName, LogEntry, LogEntrySource
| order by TimeGenerated desc
```
