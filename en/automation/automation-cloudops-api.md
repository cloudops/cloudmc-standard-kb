---
title: "Automating tasks with the CloudOps API"
slug: cloudops-api
---


This article is a beginner's introduction to the CloudOps REST API, providing details on how to access it, and also builds context for the other articles in the Automation category.

## Overview

For certain simple tasks, you may find it useful to execute them without having to log into the CloudOps Web user interface. For example, you may need to repeatedly:

-   Sync the knowledge base after making changes to the content
-   Generate a monthly report with identical criteria and filters
-   Add new users as members to a specific environment

In these cases, executing a single API call without having to log into the Web UI can save you time and effort. Furthermore, you can use any scheduling tool to trigger your API calls automatically whenever you wish.

As an API-driven orchestration platform, CloudOps provides access to all functionality via its REST API. Any feature that is accessible via the Web UI can be accessed via the API. All calls to the API are secured via HTTPS connections, and an API key that is unique to your account.

The articles in the Automation category provide a starting point for users who have limited or no prior experience using API tools. It is not meant to replace the full API documentation. Instead, it is a friendly and forgiving guide to using the API, with plenty of examples and which avoids having to install any software. Each example can be edited to fit your particular situation, and can even be used together to build automated workflows.

## What to expect

To make this guide accessible to the widest audience, the examples presented in these articles use an industry-standard utility called cURL. This program is included on all macOS, Linux, and Windows systems. It is a command that can be pasted into a terminal window for macOS and Linux users, or into a command prompt or PowerShell window for Windows users. When the cURL command is run, it will connect to the CloudOps API using your user account, send your API call as request to the CloudOps system, and then it will print out the response that CloudOps returned.

The cURL command presented with each example is meant to be copied from the article and pasted into a text editor. In the text editor, you can replace text within the braces with the required values, and then paste the modified command into you terminal or command prompt. For example, a cURL command to list all environments you have access to with your user account might look like this:

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/environments \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

To prepare this example for execution, you will copy the full text from the article and paste it into a text editor. For readability, the cURL command is broken into multiple lines using the backslash \('`\`'\) symbol to force a line-wrap. \(Windows users please be sure to read the [Windows users only](automation-cloudops-api.md#section_ihn_gt1_qgc) section, because you will need to use a different symbol to accomplish this.\) Notice that there are two markers, which act as placeholders for the data you will supply: `{endpoint-url}`, and `{api-key}`. You will replace these markers \(including the surrounding braces\) with the relevant values, as explained in the [API key](automation-cloudops-api.md#api-key) and [API endpoint](automation-cloudops-api.md#api-endpoint) sections.

When working with any API, there is always going to be some technical aspect to the functionality. However, when executing simple tasks, many details can be safely ignored. For example, when you execute your API task \(often referred to as "making an API call"\), the system will return a response which will contain a lot of text. This text will be in a standard format called JSON.

This wall of text may seem daunting and unrecognizable. There will be a lot of symbols, such as brackets and parentheses. Although these symbols are important because they help to structure the response, but luckily they can be ignored for the most part, because they are not the data you need. Particularly if you are simply executing an operation, all you might be looking for is a value that says `OK`, to indicate that the operation succeeded.

Similarly, the response may contain a lot of extraneous data. For example, the API call above returns many fields with values. It is not just a list of environments, it includes parameters about each listed environment. To identify each environment, you will have to inspect the response to find the value you need. This is where it becomes important to take the response, put it into a text editing tool, and use the Find feature to locate the target date. For more complex responses with a large amount of data, you may wish to use a text editor which can reformat a JSON document to make the response more human-readable.

## Windows users only

Windows users, please note that you will have to edit the examples before they can be used, due to how Windows treats special characters.

-   If you are using a **command prompt** \(`cmd.exe`\) window: Replace the backslash with a carat symbol \('`^`'\)
-   If you are using a **PowerShell** window: Replace the backslash with a space and a backtick symbol \('```\)

**Attention:** In both cases, the carat or the backtick must be the last character on the line.

## API key

In order to use the CloudOps API, you will start by logging into the system and creating an API key for your requests. The API key acts as the credentials that cURL will send to CloudOps to authenticate itself using your user account.

The following article provides the steps on creating a new API key:

-   [Generate a CloudOps API key](../how-to/how-to-cloudmc-api-key.md)

Once you have generated your API key, store it in a safe place, because the system will never display it to you again. Use your API key to replace the `{api-key}` marker in the example cURL commands.

## API endpoint

In addition to the API keys, the API credentials section of the User Settings panel will also list the URL to use when connecting to an endpoint. See the [API Credentials](api-credentials.md) article for full details.

## API documentation

For full documentation of the API, including the structure of requests and responses, available functionality, and a listing of all endpoints, see the Develop section of the CloudOps Documentation Home:

-   [Develop](https://docs.cloudops.com/#/develop/)

