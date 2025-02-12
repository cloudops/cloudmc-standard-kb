---
title: "Authentication with CloudOps"
slug: authentication
---


### Authentication and user accounts in CloudOps

A user account allows a person to access the CloudOps console and manage virtual resources.  User accounts are always associated with an organization, and are accessed by navigating to *Administration* -> *Users*.  CloudOps provides three ways to manage user accounts, providing extensible support for various login mechanisms:

   - **Internal:**  The default mechanism for managing user accounts.  Credentials are stored in CloudOps's internal database.
   - **LDAP:**  CloudOps supports authentication through an LDAP server, including Microsoft Active Directory.
   - **OpenID Connect:**  Provides authentication for CloudOps user accounts through one or more external identity providers.

Internal and LDAP authentication are enabled at the organization level, by a user account with the *Administrator* role or any other role with the *Organizations: Manage* permission.  Each sub-organization within an organization can use either internal or LDAP authentication, as desired.

Support for [OpenID Connect](https://en.wikipedia.org/wiki/OpenID_Connect) enables CloudOps to authenticate users with external identity providers using the OAuth 2.0 protocol.  This allows federated authentication and simplifies single sign-on integration of CloudOps with other applications.  OpenID Connect is a system-wide feature and can be enabled by a user account with the *Reseller* role or any role with the *Authentication: Manage* permission.  When an external identity provider is configured, CloudOps presents a button on the login page to enable a user to sign in using that provider.

CloudOps provides for **two-factor authentication** (2FA) on any user account.  If 2FA is enabled on an account, after entering a valid username and password, or after a successful login through OpenID Connect, the user logging in will then be asked to enter a valid token from their authenticator application.  See [Enable Two-Factor Authentication](../administration/enable-two-factor-authentication.md).

<!-- ## Acting as an identity provider

Information on SAML with link to SAML article. -->

## Configuring authentication

When using internal authentication, no additional configuration is necessary.  

<!-- Link to LDAP article -->

For details on configuring external identity providers, see [Authenticating with OpenID Connect](../administration/openid-connect.md).
