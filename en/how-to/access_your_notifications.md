---
title: "Manage your notifications"
slug: manage-your-notifications
---


This article describes notifications and how to access and manage them in CloudMC.

## Overview

From time to time, you will receive various messages inside the platform. Some of these messages may be automatically generated for activity within the system, others may be announcements which are titleed and published by your system administrator. Collectively, these messages are referred to as **notifications**.

Your notifications appear in the **Notifications** panel, which is accessible via the bell icon on the right side of the menu bar, at the top of the page.

## Activity notifications

In order to provide accountability and traceability, all user operations are logged and stored in the **Activity Log**. In some contexts, such as for operations that will take extra time to complete, an activity notification will provide further information such as progress or completion status. An amber badge will appear on the bell icon in the menu bar at the top of the page to indicate that there is a new notification. Click the bell icon to reveal the Notifications panel. The **Activity** tab is selected by default, and any activity notifications will be listed below.

![A screenshot of an expanded Notifications panel with a notification indication progress of an operation](/assets/announcements-notificationpanel-en.png)

Furthermore, when certain operations are performed, the system may need to communicate further information to you in order to complete the operation. For example, when adding a new instance, new credentials will be generated, or, when generating new API credentials, the system will generate a new key. These will be provided to you via activity notifications.

For these situations, CloudMC will create a notification in the Notifications panel, an amber badge will appear on the bell icon, and the sensitive information will be presented inside the notification. You can copy the information out of the notification, and then clear the notification to preserve security.

![A screenshot of a notification containing a ghosted password with gadgets for exposing the password and copying it to the clipboard](/assets/announcements-credentials-en.png)

Because of the transitory and sensitive nature of activity notifications, they are accessible only from the notifications panel and are never saved by CloudMC, and may be cleared manually if desired by clicking the **Clear** or **Clear all** buttons.

## Announcements from your organization

When your organization needs to communicate with you, your system administrator will publish an announcement. Announcements from your organization will appear in one of two ways:

-   **Regular announcement**: These will appear in the **Notifications** panel, and are normally about general or non-urgent topics
-   **Splash announcement**: These will appear in the center of the CloudMC interface, similar to a dialog box, and are normally about urgent topics that need your immediate attention

When a new regular announcement has been published, an amber badge will appear on the bell icon. Click the bell icon to expand the Notifications panel. Click on the **Announcements** tab to list your announcements. All published announcements will appear, listed from newest to oldest. Once you close the Notifications panel, any announcements will be considered read, and the amber badge will be removed from the bell icon. Opening, clicking the Announcements tab, then closing the Notifications panel is the only way to acknowledge an announcement.

Announcements will persist in your Notifications panel even after they have been read, until your system administrator removes them.

![Screenshot of the Notifications panel with a regular announcement indicating an upcoming change to a product displayed](/assets/announcements-regular-en.png)

Splash announcements do not appear in the Notifications panel. Instead, these appear in the center of the CloudMC interface. They have a **Close** button, and all functionality in the platform is unavailable until you close the announcement. If you log out and then log back in, the announcement will be displayed again, until you click the **Close** button.

Once a splash announcement has been closed, it will not reappear.

![Screenshot of the CloudMC user interface with an splash announcement indicating emergency downtime for later in the day](/assets/announcements-splash-en.png)

