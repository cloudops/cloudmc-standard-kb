---
title: "List all roles for an environment"
slug: automation-list-roles-for-environment
---


This article will show you how to retrieve all the available roles for a given environment.

## Before you begin

-   You will need a valid API key
-   You must have access to the target environment
-   You must have the environment ID for the target environment

## API call

```bourne
curl --request GET \
  --url  https://{endpoint-url}/api/v2/roles?default_scope=ENV&environment_id={environment-id} \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Result

-   The response will contain all environment roles available in the specified environment
-   You may now search through the response to identify the desired role in the `data/name` and `data/id` fields

## Discussion

To find the environment ID, log into the Web UI and navigate to the service which contains the target environment. In the list of environments, identify the target environment, click on the Hidden Actions menu at the far right, and select **Copy environment ID**.

The environment ID can also be retrieved via the API.

