---
title: "Enable two-factor authentication"
slug: enable-2fa
---


This article introduces the concept of two-factor authentication, and describes how to enable and disable this feature for your account.

## Detailed overview

Two-factor authentication, also known as multi-factor authentication, 2FA, or MFA, provides unambiguous identification of a user by means of two separate pieces of identification. The first component is something that the user must know, such as a password or a passphrase. The second component is something that the user must have, for example, a one-time token. This mechanism helps to prove to the system that you are who you say you are.

It is generally recommended to always enable 2FA for your Hypertec Cloud account. Once 2FA is configured, when logging in you will be prompted for the one-time token:

![Screenshot of the Hypertec Cloud login page prompting for a one-time token](/assets/enable-2fa-login-en.png)

To generate a one-time token, you will need to install a token generator application, either on your smartphone or on your workstation. There are many applications that can work with Hypertec Cloud's 2FA system, such as LastPass, 1Password, Google Authenticator, Microsoft Authenticator, and others. Please refer to the documentation provided by the vendor of your software for installation and configuration information.

## Enabling two-factor authentication

### Before you begin

-   You must have a token generator installed and configured

### Procedure

1.  Click on the **User menu** \> **My profile** \> **Security**. The User menu is in the upper right corner of the Hypertec Cloud menu bar.

2.  Scroll to the bottom of the page and click on the button titled **Enable two-factor authentication \(2FA\)**.

    ![Screenshot of the Security page, focused on the Enable two-factor authentication button](/assets/enable-2fa-enablebutton-en.png)

3.  You will be prompted for your password, enter it and then click **Confirm**.

4.  Use your token generator to scan the QR code that appears on the screen.

    Verify that your token generator accepted the QC code and is generating a one-time token.

5.  Enter the one-time token from your token generator into the provided text field.

    ![Screenshot of the Security page, focused on the QR code and token entry](/assets/enable-2fa-qrcode-en.png)

6.  Click **Enable**.

    A list of backup codes will be displayed. Store them in a safe place. In the event that you lose access to your token generator, use one of these codes to log into the system and re-enable 2FA with a new token generator.

    ![Screenshot of the Security page, focused on the backup codes](/assets/enable-2fa-codes-en.png)


### Results

-   Two-factor authentication is now enabled on your Hypertec Cloud account
-   Upon your next login, after verifying your username and password the system will prompt you to enter the one-time token from your token generator

### Regenerate your backup codes

If you should lose your backup codes, your codes can be re-generated.

#### Procedure

1.  Click on the **User menu** \> **My profile** \> **Security**. The User menu is in the upper right corner of the Hypertec Cloud menu bar.

2.  Scroll to the bottom of the page and click on the button titled **Manage two-factor authentication \(2FA\)**.

3.  You will be prompted for your password, enter it and then click **Confirm**.

4.  Click on the button titled **Regenerate backup codes**.

    A list of the new backup codes will be displayed. Store them in a safe place.


### Disable two-factor authentication

#### Procedure

1.  Click on the **User menu** \> **My profile** \> **Security**. The User menu is in the upper right corner of the Hypertec Cloud menu bar.

2.  Scroll to the bottom of the page and click on the button titled **Manage two-factor authentication \(2FA\)**.

3.  You will be prompted for your password, enter it and then click **Confirm**.

4.  Click on the button titled **Disable two-factor authentication**.

    Two-factor authentication is now disabled on your account. Next time you log in, you will be asked only for your username and password.


