---
description: Register a vehicle with a single in-game command!
---

# VehReg

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/vehreg/releases/tag/latest) to download the VehReg plugin .zip file.
2. Download and install the [apicheck ](api-id-checker.md)plugin.
3. Download and install the[ locations](https://github.com/Sonoran-Software/sonoran\_locations/releases) plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the vehreg, locations, and API check plugins.

### 4. Configuration&#x20;

<table><thead><tr><th>Option</th><th width="276">Description</th><th>Default</th></tr></thead><tbody><tr><td>reigsterCommand</td><td>The command used to register current vehicle</td><td>reg</td></tr><tr><td>defaultRegExpire</td><td>The default date that all registrations will expire</td><td>01/02/2030</td></tr><tr><td>defaultRegStatus</td><td>The default status that all registrations will have | MUST BE IN CAPS</td><td>VALID</td></tr><tr><td>language</td><td>Array of language used within the script</td><td>English</td></tr></tbody></table>

## Usage

### Commands

| reg | Register your current vehicle in CAD |
| --- | ------------------------------------ |

