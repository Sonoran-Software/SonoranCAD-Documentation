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
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../pricing/vps-hosting.md)!
{% endhint %}

## Installation Video

Click to view our [locations and postal install video](https://youtu.be/Rc6MT0D6rcI).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation **Guide**

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_postals/releases)to download the postals plugin .zip file.
2. Download and install the [locations ](locations.md)plugin.

### 3. Install the Plugin and Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the postals and locations plugin.

### 4. Configure Postal Script and Exports

1. If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you will need to follow the steps in the [usage](postals.md#using-nearest-postal) section below.
2. If you're using a custom postal script, you can learn more about the exports provided in the [usage ](postals.md#custom-postal-scripts)section below.

## Configuration

| Option | Description | Default |
| :--- | :--- | :--- |
| sendTimer | Time between sending postal updates to the server. | 950 ms |
| shouldSendPostalData | Toggles the plugin on/off | True |

## Usage

### Using Nearest-Postal

{% hint style="info" %}
**As of Nearest-Postal v1.4.1 you do not need to manually add the export, it is included in the Nearest-Postal release.**
{% endhint %}

1. If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you must add the following code to the very bottom of the `cl.lua` file in your nearest postal resource \(**not** the Sonoran CAD plugin file\). This will be the **very last line** in the nearest postal's `cl.lua` file.

```lua
exports('getPostal', function() if nearest ~= nil then return postals[nearest.i].code else return nil end end)
```

The screenshot below shows an example of the export above being pasted as the **very last line** in the nearest postal's `cl.lua` file \(**not** the Sonoran CAD plugin file\).

![Nearest Postal&apos;s cl.lua File Example](../../../.gitbook/assets/image%20%2881%29.png)

### Custom Postal Scripts

This plugin no longer has a "custom" option. If you're not using the nearest postal script, you will need to paste the above export into your custom script and have it return the player's current postal as a string. Need help? You can always [hire a developer](https://support.sonoransoftware.com/#/).

