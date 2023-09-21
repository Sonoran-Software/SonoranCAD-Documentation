---
description: >-
  Allows sending nearest postal to the CAD via the location field. Also enables
  postal auto-fill for new dispatches and calls.
---

# Postals

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Video

Click to view our [locations and postal install video](https://youtu.be/Rc6MT0D6rcI).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation **Guide**

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran\_postals/releases)to download the postals plugin .zip file.
2. Download and install the [locations ](locations.md)plugin.

### 3. Install the Plugin and Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the postals and locations plugins.

### 4. Configure Postal Script and Exports

1. If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you will need to follow the steps in the [usage](postals.md#using-nearest-postal) section below.
2. If you're using a custom postal script, you can learn more about the exports provided in the [usage ](postals.md#custom-postal-scripts)section below.

## Configuration

| Option               | Description                                        | Default |
| -------------------- | -------------------------------------------------- | ------- |
| sendTimer            | Time between sending postal updates to the server. | 950 ms  |
| shouldSendPostalData | Toggles the plugin on/off                          | True    |

## Usage

### Using [Nearest-Postal](https://forum.cfx.re/t/release-nearest-postal-script/293511)

{% hint style="warning" %}
The plugin only supports 1.5.0 or higher of the nearest postals plugin. Be sure to download the latest version before using.
{% endhint %}

If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), some minor configuration is required.

#### 1. Set the Resource Name

In the Sonoran CAD postals plugin config, change the `nearestPostalsResourceName` value to the _**exact**_ name of your nearest postals resource.\
\
Ex: `nearest-postals-1.5`

#### 2. Ensure Proper Startup Order

Be sure that you are starting the nearest-postals addon/resource **before/above** where you `ensure sonorancad` in your `server.cfg`.

Be sure to restart both the Sonoran CAD resource and the nearest-postals script, or restart your server entirely to apply the changes made.

### Custom Postal Scripts

This plugin no longer has a "custom" option. If you're not using the nearest postal script, you will need to create an export called getPostal in that script and have it return the player's current postal as a string. Need help? You can always [hire a developer](https://support.sonoransoftware.com/#/).
