---
title: "Install and configure CloudMonkey"
slug:  install-and-config-cloudmonkey
---


Apache CloudMonkey is a Command Line Interface written in Python to interact with Apache CloudStack APIs.

This tool is useful to automate Virtual infrastructure in Hypertec Cloud or to manage it thru the CLI. Apache CloudMonkey can be installed on various operating systems such as Linux and macOS, it only requires Python 2.7+ to be installed.

### Installation and Configuration

1. To install Apache CloudStack follow the [official project installation instruction](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI).
1. Retrieve your API credentials from Hypertec Cloud by going to the User menu in the upper right corner, and clicking on **API credentials**.
  - Note the API endpoint, the API key, and the Secret key, as this will be used to created the CloudMonkey configuration file
  - Note the ProjectID define in the Service Connection page as this  ProjectID will be required to perform API calls later.
1. Create the cloudmonkey configuration file (`~/.cloudmonkey/config`) using your API credentials for cloud.ca using following content:

```
[core]
profile = compute-qc
asyncblock = true
paramcompletion = true

[ui]
color = true
prompt = >
display = json

[compute-qc]
url = https://compute-qc.cloud.ca/client/api
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <COMPUTE_QUEBEC_API_key>
secretkey = <COMPUTE_QUEBEC_Secret_key>

[compute-on]
url = https://compute-on.cloud.ca/client/api
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <COMPUTE_ONTARIO_API_key>
secretkey = <COMPUTE_ONTARIO_Secret_key>
```

### Connect to Hypertec Cloud

Launch the CLI with the command `cloudmonkey`, then use the CLI command `sync` to confirm CloudMonkey is connected to the Hypertec Cloud API.

```
user1$ cloudmonkey
Apache CloudStack cloudmonkey 5.3.3. Type help or ? to list commands.

Using management server profile: compute-qc

(compute-qc) > sync
247 APIs discovered and cached
(compute-qc) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0
(compute-qc) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0 filter=name,id
```


To connect to compute-on.cloud.ca API, use the CLI command `set profile compute-on` followed by `sync`.