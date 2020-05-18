---
description: Handles sending emergency calls to the CAD.
---

# Call Commands

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_callcommands/releases)to download the call commands plugin .zip file.
2. Download and install the [locations ](https://app.gitbook.com/@sonoran-software-systems-llc/s/sonoran-software/~/drafts/-M7ZzzsXkmITLyW1hwM9/integration-plugins/integration-plugins/available-plugins/locations)plugin.
3. \(Optional\) Download and install the [postal ](https://app.gitbook.com/@sonoran-software-systems-llc/s/sonoran-software/~/drafts/-M7ZzzsXkmITLyW1hwM9/integration-plugins/integration-plugins/available-plugins/postals)plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the call commands plugin, the locations plugin, and the optional postals plugin.

## Usage

### Commands

| Command | Description |
| :--- | :--- |
| 911 | Sends specific 911 call to the CAD |
| 511 | Sends specific 511 call to the CAD \(Civil\) |
| 311 | Sends non-emergency call to the CAD \(Civil\) |

### Custom Events

```text
 EVENT: SonoranCAD::callcommands:cadIncomingCall
 PARAMS:
      emergency = true/false (911 or 311 call)
      caller = name of caller
      location = street / cross street string
      description = description of call
      source = playerId
```

