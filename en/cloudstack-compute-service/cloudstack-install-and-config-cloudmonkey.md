---
title: "CloudStack: Install and configure CloudMonkey"
slug:  cloudstack-install-and-config-cloudmonkey
---


Apache CloudMonkey is a Command Line Interface written in Python to interact with Apache CloudStack APIs.

This tool is useful to automate Virtual infrastructure in CloudStack or to manage it thru the CLI. Apache CloudMonkey can be installed on various operating systems such as Linux and macOS, it only requires Python 2.7+ to be installed.

### Installation and Configuration

1. To install Apache CloudStack follow the [official project installation instruction](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI).
1. Retrieve your API credentials following the steps in [How to obtain service API keys](../how-to/how-to-obtain-service-api-keys.md)
  - Note the API endpoint, the API key, and the Secret key, as this will be used to created the CloudMonkey configuration file
  - Note the ProjectID as this will be required to perform API calls later
1. Create the CloudMonkey configuration file (`~/.cloudmonkey/config`) using your API credentials using following content, replacing the text in angle brackets with the values you noted above:

```
[core]
profile = cloudstack-service
asyncblock = true
paramcompletion = true

[ui]
color = true
prompt = >
display = json

[cloudstack-service]
url = <API_endpoint>
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <API_key>
secretkey = <Secret_key>

```

### Connect to the CloudStack service

Launch the CLI with the command `cloudmonkey`, then use the CLI command `sync` to confirm CloudMonkey is connected to the CloudStack API.

```
user1$ cloudmonkey
Apache CloudStack cloudmonkey 5.3.3. Type help or ? to list commands.

Using management server profile: cloudstack-service

(cloudstack-service) > sync
247 APIs discovered and cached
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0 filter=name,id
```


<!-- >To connect to compute-on.cloud.ca API, use the CLI command `set profile compute-on` followed by `sync`. -->
