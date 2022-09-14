---
title: "Generate a Hypertec Cloud API key"
slug: generate-hypertec-cloud-api-key
---


When working with the Hypertec Cloud API, you will need to generate an API key for use with your code.  API keys provide a convenient method for your application to identify itself to a service when making calls to the service's API.

Any Hypertec Cloud user may generate an API key.  A user's API keys will have the same level of privilege that the user has.  There is no limit to the number of API keys that a user may generate.  It is recommended to take advantage of this by generating an API key for each application that will be accessing the system.

To manage your API keys, navigate to the user menu on the upper right of the page, click on *My profile*, then click on the item labeled *API credentials*.

### List existing API keys and endpoints

![API credentials screen](/assets/cca-cloudmc-api-key-en-01.png)

The *API credentials* screen lists all existing keys under the **API keys** section.  The name of each key, the IP address from which it was used last, and the time and date it was last used are displayed.

To rename a key, click the icon labeled *Edit API key* icon on the far right side of the desired entry.

The endpoint for making API calls to the system is displayed above the list of keys.  Click the clipboard icon to copy the URL into your clipboard.

### Generate a new API key

![API key generated](/assets/cca-cloudmc-api-key-en-02.png)

1. From the *API credentials* screen, click the button labeled *Generate API key*.
1. Enter a name for the new key into the **Name** text field.  You may wish to give the key a name which reflects the application it will be used for.  Click *Generate*.
1. You will be returned to the *API credentials* screen.  A notification will appear with the new API key hidden.
   - You **must** retrieve the new key from this notification.  Once the notification is dismissed, there is no way to display the API key again.
   - Click the eye symbol to reveal the API key.
   - Click the clipboard icon to copy the API key into your clipboard.
1. The API key is now ready for use.  Store it in a secure location.

### Revoke an API key

1. From the *API credentials* screen, click the icon labeled *Revoke API key* on the far right side of the desired entry.
1. A confirmation dialog box will appear.  Click *Revoke*.
1. The API key will be revoked immediately and is no longer valid for use.
