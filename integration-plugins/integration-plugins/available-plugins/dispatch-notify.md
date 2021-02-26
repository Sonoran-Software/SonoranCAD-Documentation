---
description: >-
  Notify officers of incoming calls, allow them to attach to them, notify the
  caller, and route units via GPS in real-time...all in one!
---

# Dispatch Notify

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

This plugin notifies officers of incoming calls and allows them to attach to calls via command. When the officer is attached to the dispatch call their GPS is automatically routed to the postal code. GPS routing is updated whenever the dispatch postal is updated and civilians making the emergency call are also notified when an officer is en-route.

## Video Showcase

Check out our video showcase of this plugin [here](https://youtu.be/eWmeFpz8jiA).

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_dispatchnotify/releases) to download the DispatchNotify plugin .zip file.
2. Download and install the [pushevents](https://github.com/Sonoran-Software/sonoran_pushevents/releases/tag/latest) and [callcommands](https://github.com/Sonoran-Software/sonoran_callcommands/releases/tag/latest) plugins.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the pushevents and callcommands plugins.

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 5. Configuration

Review the `config_dispatchnotify.lua` file to configure the plugin to behave how you like. The file is well documented. Please review **all** the settings!

## Commands

| Command | Description |
| :--- | :--- |
| /rcall | Respond/Attach to the new dispatch call |
| /togglegps | Toggle the GPS auto-lock when dispatch updates the postal code |

### Troubleshooting

* No notifications for 911 calls
  * Units must be logged into the CAD \(by default\) or meeting the requirements depending on how the plugin is configured.
  * Ensure the pushevents plugin is functioning properly and the port is forwarded.
  * If using pNotify notifications, ensure that resource is running.
* Units do not automatically attach to calls
  * Ensure their API ID is set so the server knows who they are.
  * Ensure the pushevents plugin is functional.
* Caller is not notified when units attach to the call
  * If the caller ever leaves the server and rejoins, this feature does not work.
  * If dispatch created the call within the CAD, there is no way to notify a caller.
  * Check the civilian has entered an API ID if they placed the call from within the CAD.
  * Ensure you are not overriding the 911 command \(default `/911`\) with another resource.



