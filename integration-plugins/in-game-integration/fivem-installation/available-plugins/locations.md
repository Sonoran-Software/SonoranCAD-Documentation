---
description: Sends locations of all online players to the CAD.
---

# Locations

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

## Activation Video

Click to view our [locations and postal install video](https://youtu.be/Rc6MT0D6rcI).

**Be sure you have already installed our** [**core framework**](../)**!**

## Installation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the required submodules.

### 3. Set Your API ID

Don't forget to set your account [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

## Further Configuration

| Option       | Description                                                                    | Default Value       |
| ------------ | ------------------------------------------------------------------------------ | ------------------- |
| checkTime    | How frequently to send location updates to the server.                         | 5000 ms (5 seconds) |
| prefixPostal | Prefixes postal to locations (like \[111] Some Road). Requires Postals plugin. | True                |

## Usage

### Automated Functionality

This plugin requires no configuration by default and will send locations of all active players. This can be seen by dispatch or other panels.

### Function

This function can **only** be used by other plugins and is not exported.

```lua
function findPlayerLocation(source) -- returns location as a string
```
