---
title: "StackPath Service:  Managing EdgeRules"
slug: stackpath-service-managing-edgerules
---


StackPath provides *EdgeRules* to give you control over how requests to your site are handled.  StackPath has four pre-defined EdgeRules that can be enabled, and also allows you to create custom EdgeRules to meet the specific needs of your site.

EdgeRules are available only when the CDN service is enabled for a site.  

that inspect requests to see if they match certain conditions, and matching requests will have actions applied to them.

Required permissions

Navigate to the StackPath service, click on *Sites*, and click on the desired site.  When the *Overview* page appears, click on the *EdgeRules* item on the left.

### View EdgeRules

### Predefined EdgeRules

#### Force WWW connections
#### Custom robots.txt file
#### Pseudo-streaming
#### Referrer protection

StackPath provides four commonly used rules as predefined EdgeRules.

- **Force WWW connections:** redirect http://acme.com to http://www.acme.com.  Be aware that this would redirect http://portal.acme.com to http://www.portal.acme.com.
- **Custom robots.txt file:**  easily create and maintain a robots.txt file through the ui
- **Pseduo-streaming:**  Allows a client to specify a seek point in a file.  
- **Referrer protection:**  Allows you to specify a set of domains from which users will be allowed to connect from, as identified by the `Referer` header.  You can choose to allow empty referer headers. Requests not meeting these conditions will be blocked.

### Custom EdgeRules

The predefined EdgeRules cover only a small set of cases.  You can create custom EdgeRules to specifically target traffic that is of interest to you.

The interface will present a text field for the name.  A condition type can be selected.  Upon selecting a condition type, the interface will display the options appropriate for the condition type.  Additionally, once a condition type is selected, the interface will display an action to select for the EdgeRule.  Depending on the selected action, the interface will show the appropriate options for the action.

### EdgeRule conditions

Conditions may inspect one of five different attributes for an EdgeRule.

- **URL:**  The EdgeRule will to attempt to match a search pattern against the URL, which includes the protocol, hostname, path, and query parameters.  When defining the pattern, you may use:
   - A **simple string** for a direct match.  If the exact string is found in the URL, the pattern will match.  The asterisk (*) may be used as a wildcard to match zero or more characters.
   - A **regular expression**.  The pattern should be enclosed within a pair of forward slashes (/).  If the regular expression finds at least one match, the condition will be triggered.
- **Header:**  Looks at entire header line.
   - A **simple string** for a direct match.  If the exact string is found in the header line, the pattern will match.  The asterisk (*) may be used as a wildcard to match zero or more characters.
   - A **regular expression**.  The pattern should be enclosed within a pair of forward slashes (/).  If the regular expression finds at least one match, the condition will be triggered.
- **HTTP method:**  Match against the request method.  Select one or more methods from the popup menu.
- **Status code:**  Comma-separated list of HTTP status codes.
- **Cookie:**  Looks at cookie name and value.
   - A **simple string** for a direct match.  If the exact string is found in the cookie, the pattern will match.  The asterisk (*) may be used as a wildcard to match zero or more characters.
   - A **regular expression**.  The pattern should be enclosed within a pair of forward slashes (/).  If the regular expression finds at least one match, the condition will be triggered.


### EdgeRule actions

An EdgeRule may specify one of four general types of actions to execute when the condition is met.

- **Header rules:**
- **Caching rules:**
- **Redirect rules:**
- **URL signing:**

#### Header rules

1. Add response header
   - Added to response from CDN to end user
   - Enter the header name into the **Key** field.
   - Enter the desired value in to the **Value** field
1. Add header to CDN
   - Add to request from user to CDN
   - Enter the header name into the **Key** field.
   - Enter the desired value in to the **Value** field
1. Add header to origin
   - Add to request from CDN to origin server
   - Enter the header name into the **Key** field.
   - Enter the desired value in to the **Value** field
1. Modify header
   - Modify value of existing header <- Where?  In the request?
1. Hide header
   - From where?  The request?
   - Enter the name of the header to hide in the **Header** field

#### Caching rules

1. Cache -- specify a TTL
1. Do not cache
1. Never expire
1. Bypass cache -- How is this different from Do not cache?  The only example in the SP// docs I can find is https://stackpath.dev/docs/bypass-cache-on-url, which uses Do not cache lol

#### Redirect rules

When the condition is met, returns a 301 Redirect to the specified URL.

#### URL signing

Not clear what happens here?

URL Signing policies allow you to restrict access to your content by configuring a "shared secret" with StackPath. This "shared secret" is used to apply an MD5 hashing algorithm on the URL to validate the signature supplied on the request. Since the "shared secret" is only known by the publisher and StackPath, URL signatures cannot be generated by unauthorized users.

- Passphrase
- Passphrase field
- MD5 token field
- TTL field
- IP address filter
- URL signature path length (optional)

### List of general variables

| Variable name | Description |
| -- | ---- |
| %server.ip% | The IP address of the server |
| %server.fqdn% | The fully-qualified domain name of the server |
| %server.name% | The hostname of the server |
| %server.pop% | The Point of Presence of the server |
| %server.region% | The region where the server is located |
| %server.platform% | The Server Platform Name |
| %server.epoch% | The Server Time |
| %client.ip% | The Client IP |
| %client.request.protocol% | The protocol of the request (http/https) |
| %client.request.host% | The hostname in the Host header of the request |
| %client.request.fullurl% | Full URL of request (including protocol and host name) |
| %client.request.fullfilepath% | Full File Path from request (without qs param) |
| %client.request.params% | Query Parameters from request (with leading ?) |
| %client.request.pathonly% | Only Path (without filename) from request |
| %client.request.filename% | Only filename from request |
| %client.geoip.areaCode% | The telephone area code |
| %client.geoip.city% | The city or town name |
| %client.geoip.continentCode% | The two-character code for the continent |
| %client.geoip.countryCode% | The two-character ISO-3166-1 country code |
| %client.geoip.countryCode3% | The three-character country code |
| %client.geoip.countryName% | The country name |
| %client.geoip.dmaCode% | Designated Market Area code |
| %client.geoip.latitude% | The latitude |
| %client.geoip.longitude% | The longitude |
| %client.geoip.postalCode% | The postal code |
| %client.geoip.regionCode% | A two character ISO-3166-2 or FIPS 1-=4 code for state/region |
| %client.geoip.regionName% | The region name |
| %client.geoip.timeZone% | The time zone is generated from IANA time zone database (e.g., America/New_York) |
| %query.separator% | The query separator character |
| %function.random(min, max)% | Random Number Generator |

### See also

### External links
