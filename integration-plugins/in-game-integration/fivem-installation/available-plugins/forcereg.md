---
description: >-
  Requires players to register on the CAD via a nag screen or freezing them.
  This can be restricted to specific jobs or ACE permissions.
---

# ForceReg

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](broken-reference)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../other-products/server-hosting.md)!
{% endhint %}

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the required submodules.

### 3. Set Your API ID

Don't forget to set your account [API ID](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 4. (OPTIONAL) Utilize the Tablet's Auto API ID

The [tablet resource](tablet.md) can be configured to automatically set user's API IDs when they login, removing the need for users to manually type this in.

## Further Configuration

| Option            | Description                                                                                                                          | Default Value                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| captiveOption     | The mode to use for telling players to sign up.                                                                                      | Nag                                                                                              |
| captiveMessage    | Message to show to the player.                                                                                                       | See Config                                                                                       |
| verifyMessage     | Message to show how to confirm the player registered.                                                                                | See Config                                                                                       |
| whitelist.enabled | Restrict forcing registration to only the configured people                                                                          | `false`                                                                                          |
| whitelist.mode    | What the whitelist will use to check if a player is whitelisted                                                                      | <p><code>qb-core</code><br>Options: <code>qb-core</code>, <code>esx</code>, <code>ace</code></p> |
| whitelist.aces    | Ace permissions that will pass the whitelist and will get the ForceReg notifications if `whitelist.mode` is set to `ace`.            | `forcereg.whitelist`                                                                             |
| whitelist.jobs    | QBCore of ESX jobs that will pass the whitelist and get the ForceReg notifications if `whitelist.mode` is set to `qb-core` or `esx`. | `police`                                                                                         |

## Usage

### Automated Functionality

This submodule requires no configuration by default and will show a message at the top of the screen telling players to register for the CAD. Depending on the selected option, this behavior can change.

### Event

This event is sent to the **client** after the check is completed.

```lua
Event: "SonoranCAD::forcereg:PlayerReg"

Parameters:
    identifier: The identifier checked
    exists: true/false, if the identifier is linked to a CAD account
```
