---
title: "Get knowledge base ID"
slug: automation-get-knowledge-base-id
---


This article will show you how to find the ID of the knowledge base for your home organization.

## Before you begin

-   You will need a valid API key
-   You must have the **Reseller** role, or a custom role with the **Knowledge base: Manage** permission scoped to your home organization
-   A valid source Git repository containing a CloudOps knowledge base must already be configured for your home organization

## API call

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/effective \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Result

-   The response will contain the full content of the knowledge base
-   You may now search through the response to identify the identifier of the knowledge base in the `data/id` field

**Attention:** Be aware that the response will contain values in `data/sources/id`, `data/categories/id`, `data/categories/translations/id`, and in `data/categories/articles/translations/id`. These are NOT the identifiers of the knowledge base.

## Discussion

This API call is a good example of where a huge amount of data is returned, but you only need one value. The response will contain the text for all articles, in all categories, in all languages. You will have to search through the JSON-formatted response to find the desired knowledge base ID. Although this may seem like a daunting task when you initially see the solid wall of text that the API call returns, there are tools which make it much easier to find your value.

Depending on the text editor you are using, it may have a JSON-formatting feature already built in. You can copy the response out of your terminal or command window, paste it into the text editor, and execute the relevant command to format the JSON content to make it more human-readable.

If your text editor does not include JSON formatting, there are publicly available tools which are free to use online. You can paste the block of text, and the tool will return it properly formatted.

Once the JSON has been formatted, it becomes easier to work with manually. Each line has a single name/value pair, separated by a colon. Lists are broken up, with the name of the list on one line, then each name/value pair in the list indented on the following lines. The beginning and end of the list are identified by opening and closing braces or square brackets. This structure makes it easier to see how the different parts of the data are related. \(The difference between braces and square brackets is important, but not relevant for this discussion.\)

In the case of the knowledge base, we wish to look at the top of the response, which is a list called `data`. Inside of this list, we see a set of indented lines, some of which contain name/value pairs, and some of which are other lists. These lists will be further indented. Because we are looking for the value associated with the `data/id` name, we can ignore any values that are further indented. We only need to look at the names that are directly in the `data` list.

Using this method, we can quickly find the name/value pair for the knowledge base identifier. The name/value pair will look something like this: `"id": "b9b69be1-36c8-473a-8400-494eba40343c",`. You can copy the value `b9b69be1-36c8-473a-8400-494eba40343c` out of the text editor or JSON formatting tool you are using, and store that knowledge base identifier for use with other API calls.

