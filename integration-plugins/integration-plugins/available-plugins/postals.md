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

1. If you're using the publicly available [nearest postal script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you will need to follow the steps in the [usage](postals.md#using-nearest-postal) section below.
2. If you're using a custom postal codes file, you will need to add the file to the plugin and sonorancad's fxmanifest as shown in the [usage ](postals.md#custom-postal-codes-file)section below.
3. If you're using an event triggered by a custom postals script, you must configure it as explained in the [usage](postals.md#custom-postal-events) section below.
4. If you're using a custom postal script, you can learn more about the exports provided in the [usage ](postals.md#custom-postal-scripts)section below.

## Configuration

<table data-header-hidden><thead><tr><th width="264.3333333333333">Option</th><th width="312">Description</th><th>Default</th></tr></thead><tbody><tr><td>Option</td><td>Description</td><td>Default</td></tr><tr><td>sendTimer</td><td>Time between sending postal updates to the server.</td><td>950 ms</td></tr><tr><td>shouldSendPostalData</td><td>Toggles the plugin on/off</td><td>True</td></tr><tr><td>nearestPostalResourceName</td><td>If using our <a href="https://forum.cfx.re/t/release-nearest-postal-script/293511">nearest-postal</a> script, specify the name of its folder here</td><td>nearest-postal</td></tr><tr><td>mode</td><td>Specify what "mode" this plugin should use to determine postals. If using nearest-postal, set this to <code>resource</code>. If using an event fired by another resource, set this to <code>event</code>. If using a custom postals file, set this to <code>file</code>.</td><td>resource</td></tr><tr><td>nearestPostalEvent</td><td>If you've set <code>mode</code> to <code>event</code>, specify the name of the event fired by your postals resource here</td><td></td></tr><tr><td>customPostalCodesFile</td><td>If you've set <code>mode</code> to <code>file</code>, copy your custom postal codes file to the postals plugin folder, and add the name of that file here.</td><td></td></tr></tbody></table>

## Usage

### Using [Nearest-Postal](https://forum.cfx.re/t/release-nearest-postal-script/293511)

{% hint style="warning" %}
The plugin only supports 1.5.0 or higher of the nearest postals plugin. Be sure to download the latest version before using.
{% endhint %}

If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), some minor configuration is required.

#### 1. Set the Resource Name

In the Sonoran CAD postals plugin config, change the `nearestPostalsResourceName` value to the _**exact**_ name of your nearest postals resource. The "name of the resource" is whatever its folder is called.\
\
Ex: `nearest-postals-1.5`

#### 2. Ensure Proper Startup Order

Be sure that you are starting the nearest-postals addon/resource **before/above** where you `ensure sonorancad` in your `server.cfg`.

Be sure to restart both the Sonoran CAD resource and the nearest-postal script, or restart your server entirely to apply the changes made.

### Custom Postal Events

If you're using a custom script that triggers an event containing the nearest postal to a character, first set `mode` to `event`, then specify the name of the event fired by your postals resource in `nearestPostalEvent` in the config.

### Custom Postal Codes File

If you want to use your own custom postal codes file with this plugin, open the config and change `mode` to `file`. Next, copy your custom postal codes file to the postals plugin folder, and set the value of `customPostalCodesFile` to the name of this file.

Finally, open the fxmanifest.lua file for sonorancad, and change the files { } section at the bottom to look like this, replacing postals\_file.json with the name of your postal file:

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
Do not simply replace the `files { }` section with that and be done. It is crucial that you change `postals_file.json` to match the name of your custom postals file.
{% endhint %}

### Custom Postal Scripts

This plugin no longer has a "custom" option. If you're not using the nearest postal script, you will need to create an export called getPostal in that script and have it return the player's current postal as a string. Need help? You can always [hire a developer](https://support.sonoransoftware.com/#/).
