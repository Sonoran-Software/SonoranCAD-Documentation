---
description: Implements the Wraith ARS 2X plate reader for automated plate reading.
---

# WraithV2

{% hint style="danger" %}
This plugin utilizes API endpoints that require the **Plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

This plugin is for sending plate reads to other plugins.

## Installation Video

Click to view our [WraithV2 plate reader and lookup installation video](https://youtu.be/IgaISh1CykE).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and Dependencies

1. Click[ HERE ](https://github.com/Sonoran-Software/sonoran_wraithv2/releases)to download the WraithV2 plugin .zip file.
2. Download and install the [lookups ](lookups.md)plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the WraithV2 plugin and the lookups plugin.

### 4. Configuration

In the `config_wraithv2.lua`file, set `isPluginEnabled` in the to `true`.

{% hint style="info" %}
Use of this plugin requires the [Wraith ARS 2X](https://forum.cfx.re/t/release-wraith-ars-2x-police-radar-and-plate-reader-v1-2-4/1058277) radar and plate reader to function. This resource is bundled with the latest SonoranCAD release as `wk_wars2x`.
{% endhint %}

| Config Option | Description |
| :--- | :--- |
| useExpires | use vehicle registration expirations, or not |
| useMiddleInitial | use middle initials? |
| alertNoRegistration | alert if no registration was found on scan? |
| statusUid | Custom record field UID containing the status |
| expiresUid | Custom record field UID containing the expiration date |
| flagOnStatuses | List of statuses to flag/alert on |

### 5. Custom Record Handling

If you wish to have the plugin alert when the vehicle is not registered, is marked as stolen, etc. you will need to ensure you have set the custom record field's UID in your config.

#### Find your custom record field's UID

In the CAD navigate to Admin &gt; Customization &gt; Custom Records &gt; select your custom vehicle registration record.

The very last column of the field containing your status and expiration dates will have the field's UID \(unique identifier, sometimes referred to as 'field mapping id'\).

![Custom Records - Field UID](../../../.gitbook/assets/image%20%28130%29.png)

#### Set the UID in your Config

By default, the `statusUid` is `status` and `expiresUid` is `expiration` for the default record. If you have customized these, you will need to update the UID in your config.

#### Set Statuses to be Flagged

The `flagOnStatuses` array contains a list of values that will result in a flag being displayed on the radar popup if they're found in the corresponding `statusUid` field.

Ex: `flagOnStatuses = {"STOLEN", "EXPIRED", "PENDING", "SUSPENDED"}`

### 6. Set Your API ID

In order to have locked plate results sent back to your CAD, don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).

## Usage

For more information on using the in-game UI, please view the [Wraith ARS 2X](https://forum.cfx.re/t/release-wraith-ars-2x-police-radar-and-plate-reader-v1-2-4/1058277) release information.  
**Results are sent directly to your CAD when a license plate is locked.**

![Wraith ARS 2X Controls](../../../.gitbook/assets/image%20%2826%29.png)

