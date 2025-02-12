---
title: "Native authentication policies"
slug: native-authentication-policies
---


## Overview

Resellers can control which domains can be used for native CloudOps user accounts, and also set certain minimum requirements for passwords. This feature is called a `native authentication policy`, and each organization can configure its own policy, or use the default policy. A sub-organization will inherit the policy of its parent, and it cannot be overridden.

To manage these features for a specific organization, navigate to **Administration** \> **Organizations**, click on the target organization, then navigate to **Authentication policies** \> **Native**.

![Screenshot of Native Authentication Policies page](/assets/native-authentication-policy-en.png)

## Denied domains

CloudOps native accounts use an email address as the username. The `Denied domains` feature allows a reseller to specify domain names that are not allowed. It accepts a comma-separated list of domain names. Users that attempt to set a password or to log in using an email address with this domain name will be denied.

## Password complexity policy

Resellers can define a password complexity policy for an organization. The policy applies only to passwords for native CloudOps accounts created in that organization. It does not impact accounts managed by LDAP or OIDC. Minimum requirements for passwords can include:

-   Length
-   Lower- or upper-case characters
-   Numbers
-   Special characters such as asterisks, ampersands, and others
