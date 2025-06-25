---
description: This guide covers the activation process for a general submodule.
---

# Submodule Configuration

{% hint style="warning" %}
All Sonoran CAD integration submodules require the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

## Install the Resource

If you have not already, [install the base FiveM resource](../).

## Activating a Submodule

The [FiveM resource](../) contains multiple "submodules" for each integration. These can be individually enabled/disabled and configured.

{% content-ref url="../available-plugins/" %}
[available-plugins](../available-plugins/)
{% endcontent-ref %}

This example uses the `postals` submodule.

### 1. Configure and Enable the Submodule

* Navigate to the `\sonorancad\configuration` folder and locate the configuration file for your desired submodule.
  * For this example we will be using the `postals_config.dist` file (name depends on the submodule ). More details are on the [specific submodule page](../available-plugins/).&#x20;
* **Enable** the submodule by changing the `enabled` variable from `false` to `true` in the plugin config.

![](<../../../../.gitbook/assets/Screen Shot 2020-05-25 at 10.00.45 PM.png>)

### 2. Rename and Save

* **Rename** and remove the `.dist` from the file to `postals_config.lua` (depending on name of plugin).
  * If you've downloaded the [pre-configured FiveM resource from the admin panel](../), this has already been done for you.
* **Save** the configuration file.

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1).png" alt="" width="369"><figcaption></figcaption></figure>

### 3. Restart Sonoran CAD

Restart the `sonorancad` resource by entering `ensure sonorancad` in the server console and enjoy your submodule!

Learn more about the available submodules:

{% content-ref url="../available-plugins/" %}
[available-plugins](../available-plugins/)
{% endcontent-ref %}

## Updates

Sonoran CAD's integration core and submodules will automatically update with the latest features, fixes, and changes!

Or, run `sonoran pluginupdate` to instantly check and update all submodules.

## Having Trouble?

If you're having trouble installing a plugin, check out our common troubleshooting guide:

{% content-ref url="../../../../roadmap/v2-legacy/plugin-installation/plugin-troubleshooting.md" %}
[plugin-troubleshooting.md](../../../../roadmap/v2-legacy/plugin-installation/plugin-troubleshooting.md)
{% endcontent-ref %}

