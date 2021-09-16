---
description: >-
  Automatically set user's API IDs in the CAD on a login, and view your CAD
  in-game with our easy to use tablet resource! Use the Mini-CAD to view current
  calls, and easily attach to and view them.
---

# Tablet & Mini-CAD

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.  
This resource is included in the base framework.

### 2. Start the Resource

In your `server.cfg` file add the following new line:  
`ensure tablet`

### 3. Edit the Configuration File

Open the `tablet/config.dist.lua` file and paste your custom community URL. Ensure that the settings for primaryIdentifier and serverid match that of your sonorancad config file.  
****  
The easiest way to show your [custom login page](../../../tutorials/customization/custom-login-page.md) is to use a query string.

`"https://app.sonorancad.com/#/?comid=YOUR_COMMUNITY_ID_HERE"`

Simply replace `YOUR_COMMUNITY_ID_HERE` in the URL with your [community ID](../../../tutorials/getting-started/finding-your-community-id-and-authentication-code.md).  
EX: `https://app.sonorancad.com/#/?comid=dojrp`

**Rename the** `config.dist.lua` **file to** `config.lua`

![](../../../.gitbook/assets/image_2021-09-16_013027.png)

### 4. Using the Tablet

* Use the `/showcad` command in-game to toggle your tablet. You can also add a custom keybind to open the tablet by going to `GTA Settings > Keybinds > FiveM`
* Use the `/cadsize <width> <height>` command to resize the tablet to best fit your screen. This size persists on reload of the client.
* Use the `/cadrefresh` command to refresh the tablet if it's not loading properly.

### 5. Using the Mini-CAD

* Use the `/minicad` command in-game to display your Mini-CAD. You must be logged into the Police or Fire CAD, and need to have your [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) set.
* You can close or move the Mini-CAD by opening the tablet, and interacting with the Mini-CAD window. 
* \(Experimental\) Use the `/minicadsize <width> <height>` command to resize the Mini-CAD to best fit your screen. This size persists on reload of the client.
* Use the `/minicadrefresh` command to refresh the Mini-CAD if it's not loading properly.
* Controls
  * Use the `Left Arrow Key` to display the previous call.
  * Use the `Right Arrow Key` to display the next call.
  * Use the `K` key to attach or detach to/from the displayed call.
  * Use the `L` key to toggle display of the call details.

### 6. Auto API ID

When a user signs into the CAD using the in-game tablet, their[ API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) can be automatically be set in the CAD.

To enable this, open the [check API plugin](api-id-checker.md)'s config and set `forceSetApiId` to `true`.

