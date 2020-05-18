---
description: This guide covers the installation process for a general integration plugin.
---

# Plugin Installation

{% hint style="warning" %}
All Sonoran CAD integration plugins require the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../pricing/faq/)page.
{% endhint %}

## Installing a Plugin

This example uses the postals plugin.

**If you have not already installed the** [**plugin framework**](framework-installation.md)**, please do so before continuing.**

### 1. Download

Download the plugin from its repository. These are found under its plugin page, like [here](available-plugins/postals.md) for the postals plugin.

![](../../.gitbook/assets/plugin_1.png)

### 2. Extract

Extract the plugins to your `sonorancad\plugins` folder.

![](../../.gitbook/assets/plugin_2.png)

### 3. Configure and Enable the Config

1. Open the `CHANGEMEconfig_postals.lua` file \(name depends on the plugin\) and configure as desired. The files are usually commented, and more details are on its [plugin page](available-plugins/postals.md). 
2. Enable the plugin by uncommenting the last line in the plugin config.

{% hint style="warning" %}
**Be sure to un-comment the last line of the config file to enable it!**  
To un-comment the last line, remove the -- characters.  
  
**Change:**  
`--Config.RegisterPluginConfig(config.pluginName, config)`  
**To:**  
`Config.RegisterPluginConfig(config.pluginName, config)`
{% endhint %}

2. Rename and remove the `CHANGEME` from the file to`config_postals.lua` \(depending on name of plugin\).

![This is how your folder should look now.](../../.gitbook/assets/plugin_3.png)

### 4. Restart Sonoran CAD

Restart the `sonorancad` resource by entering `restart sonorancad` in the console and enjoy your new plugin!

