---
description: Adds support for ESX to other plugins.
---

# ESX Support



{% hint style="warning" %}
This plugin only functions with other plugins that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/pricing/faq)page. 
{% endhint %}

{% hint style="info" %}
ESX v2 is not supported by this plugin and will not function. Only ESX v1 is supported.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../vps-hosting-1/server-hosting.md)!
{% endhint %}

### Installation

#### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/integration-plugins/integration-plugins/framework-installation.md) first.

#### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_esxsupport/releases/tag/latest) to download the esxsupport plugin .zip file.

#### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](https://github.com/Sonoran-Software/SonoranCAD-Documentation/blob/master/integration-plugins/integration-plugins/plugin-installation) for the plugin.

### Usage

This plugin does nothing on its own, but rather adds support for ESX that other plugins can take advantage of. Currently, the following plugins are supported:

* [dispatchnotify](dispatch-notify.md)
  * Adds the ability to show character names in dispatch responses \(officer names\)
  * Adds the ability to restrict functionality to certain jobs \(like police\). See the [dispatchnotify documentation](dispatch-notify.md) for how to do this.
* [callcommands](call-commands.md)
  * Adds the ability to show character names for the caller when they use /911. This is automatic when the plugin is installed.
* [livemap](live-map/)
  * Adds the ability to show character names on the map.

