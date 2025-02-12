---
title: "Authenticating with OpenID Connect"
slug: openid-connect
---


### Overview of OpenID Connect

OpenID Connect (OIDC) is an authentication system based on OAuth 2.0, and is currently the most widely adopted external authentication system.

With OpenID Connect configured, an individual can log into their CloudOps account using valid credentials from an external identity provider. Additionally, if an organization has configured a custom domain, CloudOps can optionally create a new user account automatically for an individual who logs in successfully using the external identity provider, based on the domain of the email address the user is logging in with.  This facilitates easier user management for enterprises and integration into a single sign-on (SSO) environment.

When OIDC login is configured, a button will appear on the login page allowing a user to initiate a login via the external provider.  Importantly, if a CloudOps account is configured to use two-factor authentication, the user will be asked for their 2FA token after a successful OIDC login.

### How to configure an external OpenID Connect provider

Integrating CloudOps with an OpenID Connect provider is a three-step process, described in the following sections:
   - Configure the identity provider
   - Configure CloudOps
   - Submit a **callback URL** to the provider

A user with the **Reseller** role, or any other role which has the *Authentication: Manage* permission, may add an OpenID Connect identity provider.

Navigate to *System* -> *Authentication* to get to the *Authentication* page, where all configured identity providers are listed.

#### Configure identity provider

The first step when integrating with an identity provider is to configure a client for CloudOps within your OpenID Connect identity provider.  Follow your identity provider's procedure for configuring a client, and obtain the client credentials required by CloudOps:
   - Issuer URL
   - Client ID
   - Client secret

#### Configure CloudOps

1. Click *Add identity provider*.  The *Add identity provider* page will appear.
![Identity provider page](/assets/oidc-add-1-en.png)
1. *OpenID Connect (OIDC)* is currently the only option for **Type**.
1. Choose a provider from the pop-up menu labeled **Provider**.  Any identity provider that has already been configured will appear greyed-out in the menu.
![Select identity provider](/assets/oidc-add-2-en.png)
1. Fields for the information required to connect to the identity provider will appear.
![Details for identity provider](/assets/oidc-add-3-en.png)
1. Enter the required details you obtained from the identity provider.
1. Optionally, if you have multiple external identity providers configured, you may control the order in which they appear on the login page by assigning them a **display order**.  The providers appear sorted in ascending order of their display order values.  Entries with no display order set will be listed at the end, in alphabetical order.
1. Click *Submit*.
1. The *Authentication* page appears and the new provider is listed.  Additionally, the CloudOps login page now presents users with a button to sign on with the identity provider.

#### Submit callback URL to provider

To complete the integration with the identity provider, CloudOps will generate a callback URL to pass to the provider:

1. From the *Authentication* page, select the *Action* menu to the right of your configured identity provider.  Select *Copy callback URL*.
1. In your identity provider's configuration, navigate to the client, and enter the callback URL to the list of authorized redirect URLs.
1. CloudOps will now authenticate properly through your identity provider.

### Automatic account creation

If desired, CloudOps can automatically create an account for an individual who is signing in with valid credentials from the external identity provider but who does not already have an account in CloudOps.

This setting is applied at the organization level, allowing an organization to opt out of this feature.  The organization must have at least one [custom domain](https://cloudops.github.io/cloudmc-docs/#/reseller/custom-domains) configured.  CloudOps will match domain name of the email address used to log in against the selected custom domain to determine the organization in which to create the end-user account.

1. Click on *Organizations* in the sidebar.
1. Locate the desired organization, and click on the three-dot *Action* menu on the far right of the entry.
1. Select *Manage security*.
1. The *Native authentication policy* screen will appear.  Click on the item labeled *OIDC*, then click the *Edit* button at the upper right of the page.
1. Check the box titled **Allow automatic end-user account creation upon successful OIDC login**.  Two sections will appear, **Associated domains** and **Primary role**.
1. Select one or more domains to enable automatic account creation.
1. Select the role which automatically created accounts will be assigned.
-  Only roles at your level of privilege and below will be listed.  This is to prevent unintended privilege escalation.
1. Click *Submit* to save the configuration.  Automatic end-user account creation is now enabled.
