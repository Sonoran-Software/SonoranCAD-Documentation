---
description: Handles sending emergency calls to the CAD.
---

# Call Commands

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard **version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Video

Click to view our call [commands install video](https://youtu.be/ZeCzvU3ZfD0).

**Be sure you have already installed our **[**plugin framework**](../framework-installation.md)**!**

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_callcommands/releases)to download the call commands plugin .zip file.
2. Download and install the[ locations ](locations.md)plugin.
3. (Optional) Download and install the[ postal ](postals.md)plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the call commands plugin.
2. Install the [locations](locations.md) plugin
3. Install the optional [postals](postals.md) plugin.

## Usage

### Commands

| Command | Description                                 |
| ------- | ------------------------------------------- |
| Panic   | Toggles your unit panic status in the CAD   |
| 911     | Sends specific 911 call to the CAD          |
| 511     | Sends specific 511 call to the CAD (Civil)  |
| 311     | Sends non-emergency call to the CAD (Civil) |

### Custom Events

```
 EVENT: SonoranCAD::callcommands:cadIncomingCall
 PARAMS:
      emergency = true/false (911 or 311 call)
      caller = name of caller
      location = street / cross street string
      description = description of call
      source = playerId
```
