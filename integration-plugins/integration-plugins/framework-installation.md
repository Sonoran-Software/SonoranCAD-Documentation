---
description: >-
  Sonoran CAD's plugin framework imports common API method wrappers and
  functionality. Installing our integration framework is easy! Learn more below.
---

# Framework Installation

{% hint style="warning" %}
All Sonoran CAD integration plugins require the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../vps-hosting-1/server-hosting.md)!  
Sonoran Servers customers receive **free plugin installation** and **30% off** their monthly CAD subscription!
{% endhint %}

![Sonoran Servers - Discount and Free Plugin Installation](../../.gitbook/assets/banner_3.png)

## Installation Video

View our [installation tutorial video](https://youtu.be/EsQWGnyrvm8) for help on installing our framework.

## Installation Guide

### 1. Download Release

Download the[ latest zip file from our Github.](https://github.com/Sonoran-Software/SonoranCADLuaIntegration/releases)

### 2. Extract

![Extract the zip file into your resources directory. Keep the \[sonorancad\] folder intact.](../../.gitbook/assets/2.png)

{% hint style="warning" %}
If you already have `pNotify` or the `wk_wars2x` resource, remove them from your resources folder and use the Sonoran CAD plugin version.
{% endhint %}

### 3. Configure and Rename

Open `sonorancad\config.CHANGEME.json`, update the values, then save it as `config.json`. Default configuration is below:

```javascript
{
    "communityID": "",
    "apiKey": "",
    "apiUrl": "https://api.sonorancad.com/",
    "postTime": 5000,
    "serverId": "1",
    "primaryIdentifier": "steam",
    "apiSendEnabled": true,
    "debugMode": false,
    "updateBranch": "master",
    "statusLabels": ["UNAVAILABLE", "BUSY", "AVAILABLE", "ENROUTE", "ON_SCENE"],
    "allowAutoUpdate": true,
    "autoUpdateUrl": "https://raw.githubusercontent.com/Sonoran-Software/SonoranCADLuaIntegration/{branch}/sonorancad/version.json",
    "allowUpdateWithPlayers": false
}
```

![Be sure to call your new file config.json](../../.gitbook/assets/4.png)

#### Configuration Details

| Option | Description |
| :--- | :--- |
| communityID | Your SonoranCAD [Community ID](../../tutorials/getting-started/finding-your-community-id-and-authentication-code.md). |
| apiKey | [API Key](../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md) from your In-Game Integration settings. |
| postTime | Update locations every x ms. Default 5000. It is recommend to not set this lower than 5000 ms due to rate limiting. |
| serverId | If using [multiple servers](../../tutorials/customization/configuring-multiple-servers.md) in Sonoran CAD, specify the ID here. |
| primaryIdentifier | The identifier type your community uses in the CAD to enter their API IDs. Valid values are: `license`, `steam`, or `discord.` |
| apiSendEnabled | When disabled, the integration will not send any API requests to SonoranCAD. |
| debugMode | When set to `true`, useful debugging information it outputted to the console. Keep disabled in production due to console spam. This can be toggled by entering `sonoran debugmode` in console. |
| updateBranch | Use this branch when checking for updates. Keep `master` unless you know what you're doing. |
| statusLabels | Should match what you have set in your CAD's [unit status code](../../tutorials/customization/unit-status-codes.md) settings. |
| allowAutoUpdate | When enabled, the resource will update itself. When disabled, it will simply show an update notification every 2 hours. |
| autoUpdateUrl | Where to check for updated versions. Don't touch this unless you have a reason. |
| allowUpdateWithPlayers | When enabled, it will run the updates even with players on the server. The updater will stop/start all associated resources which could cause client crashes. When disabled, the resource "waits" until there are no players. |

### 4. Server Config

Add the following to your `server.cfg` \(if you don't want pNotify or wraith, leave those out\):

```javascript
ensure pNotify
ensure wk_wars2x
ensure sonorancad
ensure tablet

# permissions for auto-updater (REQUIRED)
add_ace resource.sonorancad command allow
add_ace resource.sonoran_updatehelper command allow
```

### 4.5. Convar Overrides

Starting with framework version 2.6.2, you can override any configuration option in your `config.json` file by specifying a convar before the sonorancad resource starts.

For example, `set sonoran_serverId 2` in your server configuration will set the server ID of your server to `2` regardless of what `config.json` is set to. This is useful for communities that share the same resources.

IMPORTANT: This feature does not work with arrays \(like statusLabels\). Any other configuration option can be set using the `sonoran_<configSettingHere>` format.

### 5. Configure Push Events

In the CAD admin panel, navigate to: Advanced &gt; In-Game Integration  
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your game server's port. By default, this is port `30120`.

#### 5A. Admin Panel Configuration

Set your game server port and IP address in the admin panel of Sonoran CAD.  
The map port can be left blank, unless you are also installing the [integrated live map](available-plugins/live-map/).

![Sonoran CAD - Push Events and Map Port](../../.gitbook/assets/image%20%28157%29.png)

Learn more about [configuring multiple servers](../../tutorials/customization/configuring-multiple-servers.md).

### 6. Installing Plugins

Check out our [Available Plugins](available-plugins/) to make the integration useful.  
For basic functionality, we recommend at least the [`locations`](available-plugins/locations.md), [`callcommands`](available-plugins/call-commands.md), and [`postals`](available-plugins/postals.md) plugins.  
You can also view our [standard plugin installation guide](plugin-installation/).

### 7. Using the wk\_wars2x Radar

As of new installations, the configuration file has been renamed to prevent it being overwritten by updates. To use the radar for the first time, you must rename the file `config.dist.lua` within the `wk_wars2x` folder to `config.lua`.

## Updates

Sonoran CAD's integration framework and plugins will automatically update with the latest features, fixes, and changes!

Or, run `sonoran update` to instantly check and apply any updates for the framework core.

## Commands

The Sonoran CAD integration framework comes with several commands. These commands can be run in your server console to provide information, update plugins, and more.

| Command | Description |
| :--- | :--- |
| `sonoran help` | Display list of commands |
| `sonoran update` | Run core/framework updater |
| `sonoran pluginupdate` | Run plugin updater |
| `sonoran plugin <name>` | Display information about a plugin |
| `sonoran debugmode` | Toggle debug mode on/off |
| `sonoran info` | Dump version info and configuration data |
| `sonoran support` | Dump information for support staff |

