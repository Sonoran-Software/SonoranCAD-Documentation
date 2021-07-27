---
description: >-
  Our smart signs integration plugin allows you to update roadway signs in-game
  directly from the CAD!
---

# Smart Signs

{% hint style="danger" %}
**This plugin has not yet been released.**
{% endhint %}

![Sonoran CAD x London Studios](../../../.gitbook/assets/image%20%28217%29.png)

![London Studios - Smart Signs](../../../.gitbook/assets/image%20%2850%29.png)

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **Pro** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click HERE to download the free Sonoran CAD Smart Sign plugin .zip file from London Studios.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the Smart Signs plugin.

### 4. Copy the Stream Folder

The downloaded zip file contains both the `smartsigns` plugin and the `stream` folder.

Copy the `stream` folder to the `[sonorancad]/sonorancad/` directory.

![Sonoran CAD - Smart Signs Stream Directory](../../../.gitbook/assets/image%20%28219%29.png)

### 5. Configure your Sign Locations

In the `config_smartsigns.lua` file, you can specify sign locations and labels.

### 6. Modifying Signs in the CAD

The street sign panel can be found in both the Dispatch and DMV pages. Users will need the `Modify Street Signs` permissions in order to update them.

Here, you can easily search to filter sign labels. Sign text can also be easily duplicated from one sign to another.

![Sonoran CAD - Street Signs UI](../../../.gitbook/assets/streetsigns.gif)

