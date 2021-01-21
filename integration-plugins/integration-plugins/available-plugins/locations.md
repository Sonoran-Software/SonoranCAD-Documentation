---
description: Sends locations of all online players to the CAD.
---

# Locations

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../pricing/vps-hosting.md)!
{% endhint %}

## Installation Video

Click to view our [locations and postal install video](https://youtu.be/Rc6MT0D6rcI).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation **Guide**

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_locations/releases)to download the locations plugin .zip file.

### 3. Install the Plugin

1. Follow the [standard plugin installation guide](../plugin-installation/) for the locations plugin.

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

## Further Configuration

| Option | Description | Default Value |
| :--- | :--- | :--- |
| checkTime | How frequently to send location updates to the server. | 5000 ms \(5 seconds\) |
| prefixPostal | Prefixes postal to locations \(like \[111\] Some Road\). Requires Postals plugin. | True |

## Usage

### Automated Functionality

This plugin requires no configuration by default and will send locations of all active players. This can be seen by dispatch or other panels.

### Function

This function can **only** be used by other plugins and is not exported.

```lua
function findPlayerLocation(source) -- returns location as a string
```

