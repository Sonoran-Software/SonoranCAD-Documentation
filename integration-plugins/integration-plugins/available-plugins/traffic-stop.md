---
description: >-
  Allows law enforcement to start a traffic stop which will automatically add a
  new call and attach the unit in the CAD.
---

# Traffic Stop

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Video

Click to view our [traffic stop installation guide](https://youtu.be/QmI7Wst2ytY).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_trafficstop/releases) to download the traffic stop plugin .zip file.
2. Download and install the [locations ](locations.md)plugin.
3. \(Optional\) Download and install the [postals ](postals.md)plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the traffic stop, locations, and postals plugin.

### 4. Configuration

| Option | Description | Default |
| :--- | :--- | :--- |
| enablets | Enables the plugin. | True |
| origin | Origin of the new call. | 2 \(OBSERVED\) |
| status | Status of the new call | 1 \(ACTIVE\) |
| priority | Priority of the new call | 1 |
| title | Title of the call when created. | Traffic Stop |
| code | The 10-code for the traffic stop. | 10-11 - Traffic |

### 5. Enable User Permissions

The default command ships with [ACE permission checks](https://forum.cfx.re/t/basic-aces-principals-overview-guide/90917) enabled. **You will need to allow `command.ts` for who you want to use this command.**

### **6**. Set Your API ID

Don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

## Usage

| Command | Description |
| :--- | :--- |
| ts | Send a new dispatch to dispatch regarding the TS |

## Custom Events

Event is sent when the /ts command is processed.

```text
 EVENT: SonoranCAD::trafficstop:cadIncomingTraffic
 PARAMS:
      origin =(1 = CALLER / 2 = RADIO DISPATCH / 3 = OBSERVED / 4 = WALK_UP
      status = 1 = PENDING / 2 = ACTIVE / 3 = CLOSED
      priority = 1, 2, or 3
      title = Title that will appear in CAD
      code = 10 code that will be used for the new dispatch
      address = street / cross street string
      postal = postal of the call
      description = description of Traffic Stop
      notes = notes for the call
      source = playerId
```

