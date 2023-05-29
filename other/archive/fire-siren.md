---
description: >-
  Automatically sends fire tones to the nearest station and updates dispatch
  call notes.
---

# Fire Siren

## THIS PLUGIN IS TEMPORARILY REMOVED AND IS BEING RE-WORKED. SUPPORT IS NOT PROVIDED.

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../other-products/server-hosting.md)!
{% endhint %}

## ~~Features~~

1. ~~This plugin scans Sonoran CAD's dispatch calls for one matching a configured fire 10-code.~~
2. ~~When a dispatch is found, the nearest fire station is sent a notification tone.~~
3. ~~Notes are automatically added to the dispatch call with more information.~~

## ~~Installation **Guide**~~

### ~~1. Download and Install the Framework~~

~~If you haven't already, be sure to install and configure the~~ [~~plugin framework~~](../../integration-plugins/integration-plugins/framework-installation.md) ~~first.~~

### ~~2. Download the Plugin~~

1. ~~Click~~ [~~HERE~~](https://github.com/Sonoran-Software/firesiren/releases) ~~to download the firesiren plugin .zip file.~~

### ~~3. Install the Plugin~~

1. ~~Follow the~~ [~~standard plugin installation guide~~](../../integration-plugins/integration-plugins/plugin-installation/) ~~for the firesiren plugin.~~

### ~~4. Install Dependencies~~

1. ~~This plugin works in conjunction with the~~ [~~Inferno Collection Fire Siren~~](https://github.com/inferno-collection/Fire-EMS-Pager/releases)~~. Install this resource and any dependencies.~~

## ~~Configuration~~

<table><thead><tr><th width="168">Option</th><th>Description</th></tr></thead><tbody><tr><td>firesirenResourceName</td><td>Resource name of the Inferno Collection: Fire/EMS Pager + Fire Siren script</td></tr><tr><td>nearestPostalResourceName</td><td>Resource name of the nearest-postal script</td></tr><tr><td>postalsType</td><td>Postals type to use, should be the same as configured in the nearest postal resource.</td></tr><tr><td>fireSirens</td><td>A list of all configured fire sirens - should be the same as configured in the fire siren resource.</td></tr><tr><td>fireCalls</td><td>Codes that will trigger a fire siren</td></tr><tr><td>addCallNote</td><td>True/false, enable adding call notes</td></tr><tr><td>callNoteMessage</td><td>What note to add to a call</td></tr><tr><td>callNoteStation</td><td>Adds the station name where the alarm was triggered</td></tr></tbody></table>
