---
title: "Sync the knowledge base"
slug: automation-sync-knowledge-base
---


This article will show you how to sync the knowledge base for your home organization using the CloudOps API.

## Before you begin

-   You will need a valid API key
-   You must have the **Reseller** role, or a custom role with the **Knowledge base: Manage** permission scoped to your home organization
-   A valid source Git repository containing a CloudOps knowledge base must already be configured for your home organization
-   You must have the ID for your home organization's knowledge base

## API call

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/{knowledgebase-id}/sync \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Result

-   The response will contain the full content of the existing knowledge base
-   The `data/state` field will contain the value `"SYNCHING"`

## Discussion

Upon executing this API call, the system will return the full content of the existing knowledge base. Subsequently, it will pull the latest from the Git repository and update the knowledge base. This is a long-running operation and will take a few minutes to complete. In the Web UI, you will see the operation listed in the Notifications panel. There is no way in the API to see if the sync is completed at this time.

