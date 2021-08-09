---
description: >-
  Adds support for ESX to other plugins, as well as the ability to issue fines
  automatically to users in-game.
---

# ESX Support \(QBUS\) and Auto-Fines

{% hint style="warning" %}
This plugin only functions with other plugins that require the **standard** version of Sonoran CAD or higher. The auto-fine functionality requires the **pro** version.

For more information, view our [pricing ](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/pricing/faq)page.
{% endhint %}

{% hint style="info" %}
ESX v2 is not supported by this plugin and will not function. Only ESX v1 is supported.

**QBUS and QBUS "renamed" frameworks like RepentzFW should also work with this plugin**
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/integration-plugins/integration-plugins/framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_esxsupport/releases/tag/latest) to download the esxsupport plugin .zip file.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/integration-plugins/integration-plugins/plugin-installation) for the plugin.

### 4. \[Optional\] Add your Game Server IP and Port

_This step is only required if you wish to use the automatic fine capability._

Be sure to have your game server IP and port set in the admin panel under `Advanced` &gt; `In-Game Integration` &gt; `Server Events and Integrated Live Map`

![Sonoran CAD - Server IP and Port](../../../.gitbook/assets/image%20%28220%29.png)

### 5. Set Your API ID

Don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 6. Configuration

Review the `config_esxsupport.lua` file to configure the plugin to behave how you like. The file is well documented. Please review **all** the settings!

## Auto-Fines

Civilians in-game can be automatically billed with esx\_billing.

To do so, simply enable `issueFines` in the config and add a list of custom record types to the `fineableForms` array. Also, be sure that you have [configured your server IP and port](esx-support.md#4-optional-add-your-game-server-ip-and-port) in the admin menu.

Ex: `fineableForms = {"Arrest Report", "Speeding Citation"}`

The fines are pulled from your custom record's "Charges" section.

## Usage

This plugin can be used to issue fines to players when reports/records are entered into the CAD that include fines. You can configure the reports/records that are finable in the configuration. This plugin also adds support for ESX that other plugins can take advantage of. Currently, the following plugins are supported:

* [dispatchnotify](dispatch-notify.md)
  * Adds the ability to show character names in dispatch responses \(officer names\)
  * Adds the ability to restrict functionality to certain jobs \(like police\). See the [dispatchnotify documentation](dispatch-notify.md) for how to do this.
* [callcommands](call-commands.md)
  * Adds the ability to show character names for the caller when they use /911. This is automatic when the plugin is installed.
* [livemap](live-map/)
  * Adds the ability to show character names on the map.

## Configuration

| Config Value | Description |
| :--- | :--- |
| identityType | Newer ESX version use license instead of steam for identity. |
| usePrefix | Some ESX versions don't use the prefix \(such as license:abc\) with the identity, set to false to disable the prefix. |
| usingQbus | If you are using Qbus set this to true. |
| QbusEventName | Change to the prefix to the name of the event you are using for Qbus |
| issueFines | Whether to issue fines to players for finable reports/forms |
| fineNotify | Whether to send a message in chat when a player is issued a fine |
| fineableForms | A list of the names of forms that should issue fines to players. |

