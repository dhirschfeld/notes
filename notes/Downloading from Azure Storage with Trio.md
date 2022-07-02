---
tags: [Python, Python/trio]
title: Downloading from Azure Storage with Trio
created: '2022-06-08T13:36:50.871Z'
modified: '2022-06-08T13:38:01.571Z'
---

# Downloading from Azure Storage with Trio

```python
from azure.core.pipeline.transport import TrioRequestsTransport, RequestsTransport, AsyncioRequestsTransport
from adlfs.spec import AzureBlobFileSystem
from azure.storage.blob.aio import BlobServiceClient 
from azure.identity.aio import DefaultAzureCredential, ManagedIdentityCredential

transport = AsyncioRequestsTransport()
credential = ManagedIdentityCredential(transport=transport)
client = BlobServiceClient("https://smcaesta75af57.blob.core.windows.net", credential=credential, transport=transport)
q = client.get_container_client('weather-metra/observations/TEMPERATURE')
s = q.download_blob("obs_20220403120000_temperature.csv")
await s
```
