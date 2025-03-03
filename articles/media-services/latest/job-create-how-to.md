---
title: Create a job with Media Services 
description: The article shows how to create a Job using different methods.
services: media-services
author: IngridAtMicrosoft
manager: femila
ms.service: media-services
ms.topic: how-to
ms.date: 03/01/2022
ms.author: inhenkel
---

# Create a job

[!INCLUDE [media services api v3 logo](./includes/v3-hr.md)]

In Media Services v3, when you submit Jobs to process your videos, you have to tell Media Services where to find the input video. One of the options is to specify an HTTPS URL as a job input (as shown in this article). 

## Prerequisites

[Create a Media Services account](./account-create-how-to.md).

## [Portal](#tab/rest/)

[!INCLUDE [task general transform creation](./includes/task-create-job-portal.md)]

## [CLI](#tab/cli/)

## Example script

When you run `az ams job start`, you can set a label on the job's output. The label can later be used to identify what this output asset is for. 

- If you assign a value to the label, set ‘--output-assets’ to “assetname=label”
- If you do not assign a value to the label, set ‘--output-assets’ to “assetname=”.
  Notice that you add "=" to the `output-assets`. 

```azurecli
az ams job start \
  --name testJob001 \
  --transform-name testEncodingTransform \
  --base-uri 'https://nimbuscdn-nimbuspm.streaming.mediaservices.windows.net/2b533311-b215-4409-80af-529c3e853622/' \
  --files 'Ignite-short.mp4' \
  --output-assets testOutputAssetName= \
  -a amsaccount \
  -g amsResourceGroup 
```

You get a response similar to this:

```
{
  "correlationData": {},
  "created": "2019-02-15T05:08:26.266104+00:00",
  "description": null,
  "id": "/subscriptions/<id>/resourceGroups/amsResourceGroup/providers/Microsoft.Media/mediaservices/amsaccount/transforms/testEncodingTransform/jobs/testJob001",
  "input": {
    "baseUri": "https://nimbuscdn-nimbuspm.streaming.mediaservices.windows.net/2b533311-b215-4409-80af-529c3e853622/",
    "files": [
      "Ignite-short.mp4"
    ],
    "label": null,
    "odatatype": "#Microsoft.Media.JobInputHttp"
  },
  "lastModified": "2019-02-15T05:08:26.266104+00:00",
  "name": "testJob001",
  "outputs": [
    {
      "assetName": "testOutputAssetName",
      "error": null,
      "label": "",
      "odatatype": "#Microsoft.Media.JobOutputAsset",
      "progress": 0,
      "state": "Queued"
    }
  ],
  "priority": "Normal",
  "resourceGroup": "amsResourceGroup",
  "state": "Queued",
  "type": "Microsoft.Media/mediaservices/transforms/jobs"
}
```

---
