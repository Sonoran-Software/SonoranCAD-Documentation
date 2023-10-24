---
description: >-
  Sonoran CAD's live map allows you to update and view live unit locations,
  emergency calls, in-game road signs, and more!
---

# Live Map

<figure><img src="../../../.gitbook/assets/live map.png" alt=""><figcaption><p>Sonoran CAD - Live Map</p></figcaption></figure>

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Install Desired Blip Plugins

#### Install the Locations Plugin

The [locations plugin](locations.md) includes all logic required to display and update unit locations on the live map.

#### Install the Postals Plugin

The [postals ](postals.md)plugin (for **Pro** communities only) allows you to automatically search the live map for postals, zoom to an active unit location, or active call location.

#### &#x20;Install the Smart Signs Plugin

The [smart signs plugin](smart-signs.md) (Optional, for **Pro** communities only) allows you to change in-game smart signs right from the live map. This is an optional install feature.

#### Install the Call Commands Plugin

The [call commands plugin](call-commands.md) allows you to create emergency 911 calls in-game with a command, and provides the emergency call blips on the live map.

### 3. Choose Your Map

In the admin panel, navigate to `Advanced` > `In-Game Integration` > `Server Events and Integrated Live Map`

Here, you can enable and select a default map option for GTA, Roblox, or others. Additionally, pro communities can [upload a custom map](live-map.md#using-a-custom-map).

![Sonoran CAD - Live Map Type Selection](<../../../.gitbook/assets/image (298) (1).png>)

### 4. Set Your API ID

Don't forget to have each community member set their account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link their in-game user to the CAD.

### 5. User Access Permission

Users will need to be granted access to view the live map. This can be done via [Discord role sync](../../discord-bot-integration.md), [permission key](../../../tutorials/getting-started/permissions.md#permission-keys), or by [manually granting permissions](../../../tutorials/getting-started/permissions.md#manually-granting-permissions) in the admin menu.

### **6. Enjoy!**

In the Police, Fire, EMS, or Dispatch window you can now click the "Live Map" button to view your new live map! Selecting a blip will show it's updated position and unit information.

This is found in the task bar's start menu under `Unit Management` > `Live Map`\
You can also [pin the live map button to your taskbar](../../../tutorials/customization/customizing-your-layout.md#7-tab-system) for easy access.

{% hint style="info" %}
The live map will only show units that are in your server and also actively logged into the police, fire, or EMS panel in the CAD. Be sure to have your [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) set.
{% endhint %}

![Sonoran CAD: Live Map Button](<../../../.gitbook/assets/Screen Shot 2021-06-18 at 11.12.10 PM.png>)

## **Using the Live Map**

### **Map Controls**

#### **Postal Search**

{% hint style="warning" %}
The postal search functionality requires the **Pro** version of Sonoran CAD.

For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

With the [postals ](postals.md)plugin configured, you can manually enter and search for a postal code on the live map.

Or, quickly auto-open and search for the location by clicking the search icon:

* In the active call's postal field
* In the active unit's location field

![Live Map - Postal Search](../../../.gitbook/assets/map\_search\_postal.gif)

![Live Map - Location Search](../../../.gitbook/assets/map\_search\_btn.gif)

#### Blip Customization

You can toggle specific blips visibility and outline colors for police, fire, EMS, and dispatch.

![Live Map - Blip Customization](<../../../.gitbook/assets/image (299) (1).png>)

### **Unit Blips**

Unit blips display the live location of all police, fire, EMS, and dispatch units in-game. You can hover over a unit for brief details, or click on one for more options.

You can also easily filter the map to specific units by selecting them in the active units panel.

![Live Map - Unit Filter](../../../.gitbook/assets/map\_filter.gif)

#### Menu Options

Clicking on a unit blip allows you to add the unit to a call, add the unit to a group, send the unit lookup results, edit the unit's information, toggle their panic state, and more.

![Live Map - Unit Blip Options](<../../../.gitbook/assets/image (66).png>)

#### Drag-and-Drop

{% hint style="warning" %}
Drag-and-drop support for the live map is currently only available for the [Roblox (ER:LC)](../../roblox-er-lc.md) edition.
{% endhint %}

Drag-and-drop is also supported for unit blips. The following drag-and-drop options are supported:

* Drag to the call editor
* Drag to an active call
* Drag to a unit group
* Drag to the unit group header to create a new group
* Drag to the lookup window or minimized tab
* Drag to the timer window or minimized tab
* Drag to the tone board window or minimized tab

### Emergency Call Blips

Emergency calls placed in-game will also appear on the live map. You can hover over the blip for the call details.

#### Menu Options

Clicking on the emergency blip allows you to import the call to your editor or remove the emergency call.

![Live Map - Emergency Call Blip](<../../../.gitbook/assets/image (296) (1).png>)

#### Drag-and-Drop

Drag-and-drop is also supported for emergency call blips.

You can drag the emergency call to your call editor to import and view the information.

### Smart Sign Blips

[Smart signs](smart-signs.md) will also appear as blips on the map. You can click on these to edit the signs in-game.

![Live Map - Smart Signs](<../../../.gitbook/assets/image (144).png>)

## Using a Custom Map

{% hint style="danger" %}
This feature requires the **pro** version of Sonoran CAD.\
For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

Sonoran CAD allows communities to upload custom map images to the integrated, hosted live map. If your community does not use one of the map types provided, you can upload the images manually.

### 1. Extract Images

Extract the images from the YTD files with a program like OpenIV.\
**You will need six files named exactly as follows:**

`minimap_sea_0_0.png`\
`minimap_sea_0_1.png`\
`minimap_sea_1_0.png`\
`minimap_sea_1_1.png`\
`minimap_sea_2_0.png`\
`minimap_sea_2_1.png`

![OpenIV - Extract Images](<../../../.gitbook/assets/image (131).png>)

![OpenIV - Save Images](<../../../.gitbook/assets/image (193).png>)

### 2. Upload Images

Navigate to Admin > Advanced > In-Game Integration > Live Map and Push Events\
Select "Upload Custom" and upload all six correctly named files.

![Live Map - Custom Map Uploader](<../../../.gitbook/assets/image (179).png>)

### 3. File Size

Custom map images are limited to 30MB each. **However, if you are uploading more than 100MB of images total, you will need to upload in separate batches.**
