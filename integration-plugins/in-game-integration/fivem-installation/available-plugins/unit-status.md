---
description: Allows you to change a unit's status in the CAD.
---

# Unit Status

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the required submodules.

### 3. Set Your API ID

Don't forget to set your account [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 4. Setup User Permissions

This script provides a status set command by default. Players will need the `command.setstatus` [ACE permission](https://forum.cfx.re/t/basic-aces-principals-overview-guide/90917) (or whatever you configure the command to be).

**Example**

`add_ace builtin.everyone command.setstatus allow`

This line in your `config.cfg` file will allow everyone to access the command. We highly reccomend creating [proper ace permission groups](https://forum.cfx.re/t/basic-aces-principals-overview-guide/90917) to prevent users from spamming.

## Configuration

| Option           | Description                                                  | Default                  |
| ---------------- | ------------------------------------------------------------ | ------------------------ |
| setStatusCommand | Command that will allow units to set their own status.       | setstatus                |
| statusCodes      | Array of status codes, configurable to be community-specific | Default SonoranCAD setup |

## Usage

### Commands

| Command              | Description                                                                           |
| -------------------- | ------------------------------------------------------------------------------------- |
| setstatus <_STATUS>_ | <p>Update your unit status in the CAD.</p><p>Ex: <code>setstatus AVAILABLE</code></p> |

### Function

This is a server-side function only and is exported as `cadSetUnitStatus`. Use `setUnitStatus` if using with other submodules.

```lua
cadSetUnitStatus(<apiId>, <status>, [player])
```

* apiId: The identifier attached to the unit
* status: A status, can be the actual string or a number, based on configuration
* player (optional): server ID of the player, used to send a client event

### Event

```lua
--[[
    Event Name: SonoranCAD::unitstatus:UpdateStatus
    Arguments:
        statusText: Text or number of the status to set
]]

```
