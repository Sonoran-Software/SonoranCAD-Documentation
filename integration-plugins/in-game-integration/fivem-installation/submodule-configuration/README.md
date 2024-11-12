---
description: This guide covers the activation process for a general submodule.
---

# Submodule Configuration

{% hint style="warning" %}
All Sonoran CAD integration submodules require the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../other-products/server-hosting.md)!\
Sonoran Servers customers receive **free plugin installation** and **30% off** their monthly CAD subscription!
{% endhint %}

![Sonoran Servers - Discount and Free Plugin Installation](../../../../.gitbook/assets/Banner\_3.png)

## Installation Video

View our [framework installation](https://youtu.be/EsQWGnyrvm8) video also covers activation of a standard submodule ([Unit Status](../../../../roadmap/v2-legacy/available-plugins/unit-status.md)).

## Activating a Submodule

This example uses the `postals` submodule.

**If you have not already completed the** [..](../ "mention")**, please do so before continuing.**

### 1. Configure and Enable the Submodule

1. Navigate to the `\sonorancad\configuration` folder and locate the configuration file for your desired submodule. For this example we will be using the `postals_config.dist` file (name depends on the submodule ) and configure as desired. The files are usually commented, and more details are on its [submodule page](../available-plugins/postals.md).&#x20;
2. **Enable** the submodule by changing the `enabled` variable from `false` to `true` in the plugin config.

![](<../../../../.gitbook/assets/Screen Shot 2020-05-25 at 10.00.45 PM.png>)

2\. **Rename** and remove the `.dist` from the file to `postals_config.lua` (depending on name of plugin).

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### 2. Restart Sonoran CAD

Restart the `sonorancad` resource by entering `ensure sonorancad` in the server console and enjoy your submodule!

## Updates

Sonoran CAD's integration core and submodules will automatically update with the latest features, fixes, and changes!

Or, run `sonoran pluginupdate` to instantly check and update all submodules.

## Having Trouble?

If you're having trouble installing a plugin, check out our common troubleshooting guide:

{% content-ref url="../../../../roadmap/v2-legacy/plugin-installation/plugin-troubleshooting.md" %}
[plugin-troubleshooting.md](../../../../roadmap/v2-legacy/plugin-installation/plugin-troubleshooting.md)
{% endcontent-ref %}

