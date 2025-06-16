---
description: Handles sending emergency calls to the CAD.
---

# Call Commands

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../other-products/server-hosting.md)!
{% endhint %}

## Activation Video

Click to view our call [commands install video](https://youtu.be/ZeCzvU3ZfD0).

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

1. Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the `callcommands`, `locations`, and `postals` submodules.

## Usage

### Commands

| Command | Description                                 |
| ------- | ------------------------------------------- |
| Panic   | Toggles your unit panic status in the CAD   |
| 911     | Sends specific 911 call to the CAD          |
| 511     | Sends specific 511 call to the CAD (Civil)  |
| 311     | Sends non-emergency call to the CAD (Civil) |

### Key Binds

Users can toggle a `panic` event via a customizable keybind in their GTA `Settings` -> `Key Bindings` -> `FiveM` -> `(sonorancad)`

By default, this keybind is blank.

<figure><img src="../../../../.gitbook/assets/image (57).png" alt="" width="375"><figcaption><p>Sonoran CAD: Panic Keybind</p></figcaption></figure>

### Custom Events

```
 EVENT: SonoranCAD::callcommands:cadIncomingCall
 PARAMS:
      emergency = true/false (911 or 311 call)
      caller = name of caller
      location = street / cross street string
      description = description of call
      source = playerId
```

### Call Location

By default, calls responded to via the `/rcall` command located in [Dispatch Notify](dispatch-notify.md) will attempt to be routed to the callers current location, rather than the location of the call. If you would like calls to route to the location of the original call, please set `useCallLocation` to `true`
