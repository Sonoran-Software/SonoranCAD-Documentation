---
description: >-
  Sonoran CAD's Integration Core imports common API method wrappers and
  functionality. Installing our integration framework is easy! Learn more below.
---

# FiveM Installation

{% hint style="warning" %}
Sonoran CAD integration submodules require the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

## A. One-Click Installation (RocketNode)

We've partnered with Rocket Node to bring you one-click Sonoran CAD installation for FiveM — making it easier than ever to host your community and connect with Sonoran CAD.

* [Purchase your FiveM Game Server!](https://sonoran.link/v2E9hKGm)
* Use code `SONORAN`to save big!

{% embed url="https://www.youtube.com/watch?v=h8Ftx14j8l8" %}

The Sonoran CAD FiveM resources has multiple "submodules" for every integration feature. [These are easily enabled and configured](submodule-configuration/) in the `/configuration` folder.

{% content-ref url="submodule-configuration/" %}
[submodule-configuration](submodule-configuration/)
{% endcontent-ref %}

***

## B. Pre-Configured Resource Installation <a href="#pre-configured-resource-installation-recommended" id="pre-configured-resource-installation-recommended"></a>

{% embed url="https://youtu.be/QimkcbTPl44" %}

### 1. Download the ZIP

Download a pre-configured version of the in-game integration resource from the panel. This download will already have your community ID and API Key in the `config.lua` file in addition to file renaming done for you.

Navigate to `Admin` -> `Advanced` -> `In-Game Integration` -> `FiveM`

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Sonoran CAD: FiveM Resource Download</p></figcaption></figure>

### 2. Extract the ZIP File

Extract the `.zip` file into your resources directory. Place the `[sonorancad]` folder directly in the resources root directory.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Sonoran CAD - Folder Structure</p></figcaption></figure>

### 3. Update Your Server Config

In your `server.cfg` file, add the following:

```
ensure pNotify
ensure wk_wars2x
ensure nearest-postal
ensure sonorancad
ensure tablet

# permissions for auto-updater (REQUIRED)
add_ace resource.sonorancad command allow
add_ace resource.sonoran_updatehelper command allow
```

{% hint style="danger" %}
It is very important that the `sonoran_updatehelper` resource is not started manually. Doing so may cause a server crash if updates are available due to a race condition.

**DO NOT** start the whole \[sonorancad] folder as that will also start the sonoran\_updatehelper which might cause crashing if it is started manually. Example of not what to do `ensure [sonorancad]`
{% endhint %}

### 4. Configure the Resource

Modify the `/configuration/config.json`file for any additional configuration values.

### 5. Configure the Submodules

The Sonoran CAD FiveM resources has multiple "submodules" for every integration feature. [These are easily enabled and configured](submodule-configuration/) in the `/configuration` folder.

{% content-ref url="available-plugins/" %}
[available-plugins](available-plugins/)
{% endcontent-ref %}

***

## Resource Installation (Manual)

### 1. Download the ZIP

Download the[ latest zip file from our Github.](https://github.com/Sonoran-Software/SonoranCADFiveM/releases)

### 2. Extract the ZIP File

Extract the `.zip` file into your resources directory. Place the `[sonorancad]` folder directly in the resources root directory.

![Extract the zip file into your resources directory. Keep the \[sonorancad\] folder intact.](../../../.gitbook/assets/2.png)

{% hint style="warning" %}
If you already have the `wk_wars2x` resource, please remove it from your resources folder and use the Sonoran version included with the framework download.
{% endhint %}

### 3. Configure and Rename

Open `sonorancad\configuration\config.CHANGEME.json`, update the values, then save it as `config.json`. Default configuration is below:

```javascript
{
    "communityID": "",
    "apiKey": "",
    "mode": "production",
    "postTime": 5000,
    "serverId": "1",
    "primaryIdentifier": "steam",
    "apiSendEnabled": true,
    "debugMode": false,
    "updateBranch": "master",
    "statusLabels": ["UNAVAILABLE", "BUSY", "AVAILABLE", "ENROUTE", "ON_SCENE"],
    "allowAutoUpdate": true,
    "autoUpdateUrl": "https://raw.githubusercontent.com/Sonoran-Software/SonoranCADLuaIntegration/{branch}/sonorancad/version.json",
    "allowUpdateWithPlayers": false,
    "noUnitTimer": false,
    "forceSetApiId": false,
    "enablePushEventForwarding": false,
    "pushEventForwardUrl": "https://host",
    "disableOverride": false,
    "bodycamEnabled": true,
    "bodycamBeepFrequency": 300000,
    "bodycamScreenshotFrequency": 2000,
    "bodycamPlayBeeps": true,
    "bodycamOverlayEnabled": true,
    "bodycamOverlayLocation": "top-right",
    "bodycamCommandToggle": "bodycam",
    "bodycamCommandChangeFrequncy": "bodycamfreq"
}
```

#### Configuration Details

<details>

<summary>Configuration Options</summary>

| Option                    | Description                                                                                                                                                                                                                                                                                               |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| communityID               | Your SonoranCAD [Community ID](../../../tutorials/getting-started/finding-your-community-id-and-authentication-code.md).                                                                                                                                                                                  |
| apiKey                    | [API Key](../../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md) from your In-Game Integration settings.                                                                                                                                                                    |
| postTime                  | <p>Update locations every x ms. Default 5000.<br>It is recommend to not set this lower than 5000 ms due to rate limiting.</p>                                                                                                                                                                             |
| serverId                  | If using [multiple servers](../../../tutorials/customization/configuring-multiple-servers.md) in Sonoran CAD, specify the ID here.                                                                                                                                                                        |
| primaryIdentifier         | <p>The identifier type your community uses in the CAD to enter their API IDs.<br>Valid values are: <code>license</code>, <code>steam</code>, or <code>discord.</code></p>                                                                                                                                 |
| apiSendEnabled            | When disabled, the integration will not send any API requests to SonoranCAD.                                                                                                                                                                                                                              |
| debugMode                 | <p>When set to <code>true</code>, useful debugging information it outputted to the console.<br>Keep disabled in production due to console spam.<br>This can be toggled by entering <code>sonoran debugmode</code> in console.</p>                                                                         |
| updateBranch              | <p>Use this branch when checking for updates.<br>Keep <code>master</code> unless you know what you're doing.</p>                                                                                                                                                                                          |
| statusLabels              | Should match what you have set in your CAD's [unit status code](../../../tutorials/customization/unit-status-codes.md) settings.                                                                                                                                                                          |
| allowAutoUpdate           | When enabled, the resource will update itself. When disabled, it will simply show an update notification every 2 hours.                                                                                                                                                                                   |
| autoUpdateUrl             | Where to check for updated versions. Don't touch this unless you have a reason.                                                                                                                                                                                                                           |
| allowUpdateWithPlayers    | When enabled, it will run the updates even with players on the server. The updater will stop/start all associated resources which could cause client crashes. When disabled, the resource "waits" until there are no players.                                                                             |
| noUnitTimer               | When set to `true`, the CAD will not check every minute for a current unit list. Should only be enabled for troubleshooting issues with the unit cache.                                                                                                                                                   |
| enableCanary              | When enabled, allows the CAD to update to beta (aka canary) releases.                                                                                                                                                                                                                                     |
| enablePushEventForwarding | <p>Enables push event forwarding to the specific URL defined in the next option.<br><br><mark style="color:red;"><strong>NOTE: DO NOT ENABLE IF YOU DO NOT KNOW WHAT YOU ARE DOING (Used for custom development only!)</strong></mark></p>                                                                |
| pushEventForwardUrl       | <p><a href="../../../sonoran-cad/api-integration/push-events/#webserver-example">Web server</a> URL to forward push events to.<br><br><mark style="color:red;"><strong>NOTE: DO NOT ENABLE IF YOU DO NOT KNOW WHAT YOU ARE DOING (Used for custom development only!)</strong></mark></p>                  |
| forceSetApiId             | When enabled, the tablet resource will show an alert message stating they must set their API ID.                                                                                                                                                                                                          |
| disableOverride           | <p>By default, the framework will try and automatically correct your <a href="../../../tutorials/customization/configuring-multiple-servers.md">server's IP, port, and outgoing IP address</a> if it detects something different.<br><br>Set this to <code>true</code> to disable this functionality.</p> |

</details>

For information regarding the bodycam script config values, please see our [Bodycam Submodule Guide.](available-plugins/bodycam.md)

### 4. Server Config

Add the following to your `server.cfg` (if you don't want pNotify or wraith, leave those out):

{% hint style="danger" %}
It is very important that the `sonoran_updatehelper` resource is not started manually. Doing so may cause a server crash if updates are available due to a race condition.

**DO NOT** start the whole \[sonorancad] folder as that will also start the sonoran\_updatehelper which might cause crashing if it is started manually. Example of not what to do `ensure [sonorancad]`
{% endhint %}

```
ensure pNotify
ensure wk_wars2x
ensure sonorancad
ensure tablet

# permissions for auto-updater (REQUIRED)
add_ace resource.sonorancad command allow
add_ace resource.sonoran_updatehelper command allow
```

{% hint style="success" %}
Once completed please move to the [#additional-configuration](./#additional-configuration "mention") section to complete your setup
{% endhint %}

## Additional Configuration

### 1. Convar Overrides

Starting with framework version 2.6.2, you can override any configuration option in your `config.json` file by specifying a convar before the sonorancad resource starts.

{% hint style="warning" %}
This feature does not work with arrays (like statusLabels). Any other configuration option can be set using the `sonoran_<configSettingHere>` format.
{% endhint %}

### 2. Configure Push Events

In the CAD admin panel, navigate to: Advanced > In-Game Integration\
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your game server's port. By default, this is port `30120`.

#### 2A. Admin Panel Configuration

Set your game server port and IP address in the admin panel of Sonoran CAD.\
The map port can be left blank, unless you are also installing the [integrated live map](available-plugins/live-map.md).

![Sonoran CAD - Game Port](<../../../.gitbook/assets/Sonoran CAD - Game Port.png>)

Learn more about [configuring multiple servers](../../../tutorials/customization/configuring-multiple-servers.md).

#### 2B. Forward Push Events to an External Server

You may wish to also send push events to another external web server, like a Discord bot.

In the framework configuration file, simply set `enablePushEventForwarding` to `true` and `pushEventForwardUrl` to your web server address.

### 3. Activating Submodules

Check out our pre-bundled [submodule-configuration](submodule-configuration/ "mention")to make the integration useful.\
For basic functionality, we recommend at least the [`locations`](../../../roadmap/v2-legacy/available-plugins/locations.md), [`callcommands`](../../../roadmap/v2-legacy/available-plugins/call-commands.md), and [`postals`](../../../roadmap/v2-legacy/available-plugins/postals.md) submodules.\
You can also view our [standard submodule activation guide](submodule-configuration/).

### 4. Using the wk\_wars2x Radar

As of new installations, the configuration file has been renamed to prevent it being overwritten by updates. To use the radar for the first time, you must rename the file `config.dist.lua` within the `wk_wars2x` folder to `config.lua`.

### 5. Steam API Key

If your framework has the `primaryIdentifier` set to `steam` in the [configuration ](./#3.-configure-and-rename)(used for your API ID type), you'll need to ensure a Steam API key is set in your `server.cfg` file.

You can register a new Steam API Key at [http://steamcommunity.com/dev/apikey](http://steamcommunity.com/dev/apikey)

Then, paste it into your `server.cfg`

```
# Steam Web API key
# If you want to use Steam authentication (https://steamcommunity.com/dev/apikey) # -> replace "" with the key
set steam_webApiKey "YOUR_KEY_HERE"
```

## Updates

Sonoran CAD's integration framework and submodules will automatically update with the latest features, fixes, and changes!

Or, run `sonoran update` to instantly check and apply any updates for the framework core.

## Commands

The Sonoran CAD integration framework comes with several commands. These commands can be run in your server console to provide information, update submodules , and more.

| Command             | Description                              |
| ------------------- | ---------------------------------------- |
| `sonoran help`      | Display list of commands                 |
| `sonoran update`    | Run core/framework updater               |
| `sonoran debugmode` | Toggle debug mode on/off                 |
| `sonoran info`      | Dump version info and configuration data |
| `sonoran support`   | Dump information for support staff       |

## Troubleshooting

### Server Crashes

1\. Check to make sure `sonoran_updatehelper` or `[sonorancad]` is not being started in your server.cfg.

{% hint style="danger" %}
It is very important that the `sonoran_updatehelper` resource is not started manually. Doing so may cause a server crash if updates are available due to a race condition.

**DO NOT** start the whole \[sonorancad] folder as that will also start the sonoran\_updatehelper which might cause crashing if it is started manually. Example of not what to do `ensure [sonorancad]`
{% endhint %}

2\. Try updating your smartsigns submodule manually to the latest version. This is done by copying over the lua files from the latest release found [here](available-plugins/smart-signs.md) and overrideing the old files.

{% hint style="info" %}
We have gotten isolated reports of servers crashing with the following error, this is assumed to be related to having lower end VPS hardware specs and txadmin rebooting the server because the update process is taking too long.
{% endhint %}

![](<../../../.gitbook/assets/image (306) (1).png>)

### Warning: Could not find file X

1.) Check that the file in question is actually present in the specified file path. To find the correct path please read the example below:

```
Started resource sonorancad (3 warnings)
^3Warning: Could not find file `html/config.js` (defined in fxmanifest.lua:16^7
```

In this example, you would navigate to the `sonorancad` **resource**, open the `html` **folder** and ensure the **file** `config.js` is present.

{% hint style="info" %}
This is simply a **WARNING**, if the resource works **AS EXPECTED**, you can simply ignore the warning and continue
{% endhint %}
