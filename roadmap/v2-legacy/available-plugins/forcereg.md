---
description: Requires players to register on the CAD via a nag screen or freezing them.
---

# ForceReg

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](https://app.gitbook.com/s/-M4pGN81fb4R6zFhodcu/pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_forcereg) to download the ForceReg plugin .zip file.
2. Download and install the [apicheck ](api-id-checker.md)plugin.
3. Download and install the[ locations](https://github.com/Sonoran-Software/sonoran_locations/releases) plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the forcereg, locations and API check plugins.

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 5. (OPTIONAL) Utilize the Tablet's Auto API ID

The [tablet resource](tablet.md#5-auto-api-id) can be configured to automatically set user's API IDs when they login, removing the need for users to manually type this in.

## Further Configuration

| Option         | Description                                           | Default Value |
| -------------- | ----------------------------------------------------- | ------------- |
| captiveOption  | The mode to use for telling players to sign up.       | Nag           |
| captiveMessage | Message to show to the player.                        | See Config    |
| verifyMessage  | Message to show how to confirm the player registered. | See Config    |

## Usage

### Automated Functionality

This plugin requires no configuration by default and will show a message at the top of the screen telling players to register for the CAD. Depending on the selected option, this behavior can change.

### Event

This event is sent to the **client** after the check is completed.

```lua
Event: "SonoranCAD::forcereg:PlayerReg"

Parameters:
    identifier: The identifier checked
    exists: true/false, if the identifier is linked to a CAD account
```
