---
description: Implements the Wraith ARS 2X plate reader for automated plate reading.
---

# WraithV2

{% hint style="danger" %}
This plugin utilizes API endpoints that require the **Plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

This plugin is for sending plate reads to other plugins.

## Installation Video

Click to view our [WraithV2 plate reader and lookup installation video](https://youtu.be/IgaISh1CykE).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_wraithv2) to download the WraithV2 plugin .zip file.
2. Download the [lookups ](lookups.md)plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the WraithV2 plugin and the lookups plugin.

### 4. Configuration

In the `config_wraithv2.lua`file, set `isPluginEnabled` in the to `true`.

{% hint style="info" %}
Use of this plugin requires the [Wraith ARS 2X](https://forum.cfx.re/t/release-wraith-ars-2x-police-radar-and-plate-reader-v1-2-4/1058277) radar and plate reader to function. This resource is bundled with the latest SonoranCAD release as `wk_wars2x`.
{% endhint %}

### 5. Set Your API ID

In order to have locked plate results sent back to your CAD, don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).

## Usage

For more information on using the in-game UI, please view the [Wraith ARS 2X](https://forum.cfx.re/t/release-wraith-ars-2x-police-radar-and-plate-reader-v1-2-4/1058277) release information.  
**Results are sent directly to your CAD when a license plate is locked.**

![Wraith ARS 2X Controls](../../../.gitbook/assets/image%20%2826%29.png)

