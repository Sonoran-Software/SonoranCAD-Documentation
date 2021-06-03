---
description: >-
  Automatically set user's API IDs in the CAD on a login, and view your CAD
  in-game with our easy to use tablet resource!
---

# Tablet

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.  
This resource is included in the base framework.

### 2. Start the Resource

In your `server.cfg` file add the following new line:  
`ensure tablet`

### 3. Edit the index.html File

Open the `tablet/html/index.html` file and paste in your custom community URL.

![Tablet HTML file](../../../.gitbook/assets/screen-shot-2020-07-22-at-10.23.09-pm.png)

This is the same URL as your [custom login page](../../../tutorials/customization/custom-login-page.md).  
You can find this URL under Admin &gt; Customization &gt; Custom Login Page

![](../../../.gitbook/assets/screen-shot-2020-07-22-at-10.24.24-pm.png)

### 4. In-Game Command

Use the `/showcad` command in-game to toggle your tablet.
You can also add a custom keybind to open the tablet by going to `GTA Settings > Keybinds > FiveM`

### 5. Auto API ID

When a user signs into the CAD using the in-game tablet, their[ API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) can be automatically be set in the CAD.  
  
To enable this, open the [check API plugin](api-id-checker.md)'s config and set `forceSetApiId` to `true`.

