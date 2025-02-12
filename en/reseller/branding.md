---
title: "Brand management"
slug: branding
---


The CloudOps Web user interface is designed to easily align with your corporate branding.  Brand management in CloudOps allows an Operator, a Reseller, or someone with the *Branding: Manage* permission to:
   - Override the default colours for the interface
   - Select the available and default languages
   - Change the logo on the login page, in the side menu, and the favicon
   - Define the application name presented by the browser

Each organization can apply its own branding, and a **default branding** can be created for all organizations if desired.

Additionally, advanced users can apply custom CSS settings to modify the appearance of specific user interface components.  This article does not cover advanced mode.

### Branding hierarchy

CloudOps ships with factory branding.  This cannot be modified or deleted.  Creating a new branding within the System organization creates a **default branding**.  Upon creation, the branding will be listed with the "Default" badge on the *Branding* page.  Once the default branding has been saved,

   - Note: System branding is a special case, only an operator or account with *Branding: Manage* scoped to all organizations can manage the branding for System.

### Defining branding

All functionality related to branding is found on the *Administration* -> *Branding* page.  This item is visible in the sidebar only when the user account has the *Branding: Manage* permission scoped for the current organization.

#### Application name

The is the string displayed in the browser window title bar or name of tab.  It also appears in email templates.

#### Logo

CloudOps has support for two types of logos:
   - Small, square logo: Used on the miniature side menu and favicon
   - Large, rectangular logo: Used on the login page, side menu, and email notifications

#### Colours <a name="colours"></a>

Colours are managed through defined CSS variables.  The following variables govern the core set of colours used throughout the CloudOps interface:

   - **secondary**: Larger area of unselected side menu
   - **secondary-light**: Inner area of selected side menu
   - **primary-dark**: Selected UI elements such as the side menu, and the top bar
   - **primary-light**: Minor UI highlights
   - **primary**: Small highlights, selectors

The *Branding* page has a text box for defining the values of one or more of these variables.  Colours are expressed as hexadecimal values in the following format:

```
--secondary: #005D91;
```

#### Languages

Use the pop-up menu labeled *Languages* to select one or more languages to be available to your users.  Use the pop-up menu labeled *Default language* to choose the language which will be displayed for the login page.
