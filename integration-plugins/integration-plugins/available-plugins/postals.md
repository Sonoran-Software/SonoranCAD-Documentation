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

1. If you're using the publicly available [nearest-postal script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you will need to follow the steps in the [usage](postals.md#using-nearest-postal) section below.
2. If you're using a custom postal codes file, you will need to add the file to the plugin and Sonoran CAD's fxmanifest as shown in the [usage ](postals.md#custom-postal-codes-file)section below.
3. If you're using an event triggered by a custom postals script, you must configure it as explained in the [usage](postals.md#custom-postal-events) section below.

## Configuration

| Option                    | Description                                                                                                                                                                                                                             | Default        |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Option                    | Description                                                                                                                                                                                                                             | Default        |
| sendTimer                 | Time between sending postal updates to the server.                                                                                                                                                                                      | 950 ms         |
| shouldSendPostalData      | Toggles the plugin on/off                                                                                                                                                                                                               | True           |
| nearestPostalResourceName | If using our [nearest-postal](https://forum.cfx.re/t/release-nearest-postal-script/293511) script, specify the name of its folder here                                                                                                  | nearest-postal |
| mode                      | Specify what "mode" this plugin should use to determine postals. If using nearest-postal, set this to `resource`. If using an event fired by another resource, set this to `event`. If using a custom postals file, set this to `file`. | resource       |
| nearestPostalEvent        | If you've set `mode` to `event`, specify the name of the event fired by your postals resource here                                                                                                                                      |                |
| customPostalCodesFile     | If you've set `mode` to `file`, copy your custom postal codes file to the postals plugin folder, and add the name of that file here.                                                                                                    |                |

## Usage

### Using [Nearest-Postal](https://forum.cfx.re/t/release-nearest-postal-script/293511)

{% hint style="warning" %}
The plugin only supports 1.5.0 or higher of the nearest-postal plugin. Be sure to download the latest version before using.
{% endhint %}

If you're using the publicly available [nearest-postal script](https://forum.cfx.re/t/release-nearest-postal-script/293511), some minor configuration is required.

#### 1. Set the Resource Name

In the Sonoran CAD postals plugin config, change the `nearestPostalsResourceName` value to the _**exact**_ name of your nearest postals resource. The "name of the resource" is whatever its folder is called.\
\
Ex: `nearest-postals-1.5`

#### 2. Ensure Proper Startup Order

Be sure that you are starting the nearest-postals addon/resource **before/above** where you `ensure sonorancad` in your `server.cfg`.

Be sure to restart both the Sonoran CAD resource and the nearest-postal script, or restart your server entirely to apply the changes made.

### Custom Postal Codes File

If you want to use your own custom postal codes file with this plugin, open the config and change `mode` to `file`. Next, copy your custom postal codes file to the postals plugin folder, and set the value of `customPostalCodesFile` to the name of this file.

Finally, open the `fxmanifest.lua` file for Sonoran CAD, and change the `files { }` section at the bottom to look like this, replacing `postals_file.json` with the name of your postal file:

```lua
files {
'stream/**/*.ytyp',
'core/client_nui/index.html',
'core/client_nui/js/*.js',
'core/client_nui/sounds/*.mp3',
'core/client_nui/img/logo.gif',
'plugins/postals/postals_file.json'
}
```

{% hint style="danger" %}
Do not simply replace the `files { }` section with that and be done. It is crucial that you change `postals_file.json` to match the name of your custom postals file!
{% endhint %}

### Custom Postal Events

If you're not using the nearest-postal script or a custom postal codes file, you will need to create a export in your postals script, and have it return the player's current postal as a string.

Additionally, you will need to edit the config to set `mode` to `event`, then specify the name of this event in `nearestPostalEvent`.

Need help? You can always [hire a developer](https://support.sonoransoftware.com/#/).
