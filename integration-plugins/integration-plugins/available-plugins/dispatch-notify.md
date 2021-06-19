---
description: >-
  Notify officers of incoming calls, allow them to attach to them, notify the
  caller, and route units via GPS in real-time to calls and the lead pursuit
  officer...all in one!
---

# Dispatch Notify

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../sonoran-servers/server-hosting.md)!
{% endhint %}

This plugin notifies officers of incoming calls and allows them to attach to calls via command. When the officer is attached to the dispatch call their GPS is automatically routed to the postal code. GPS routing is updated whenever the dispatch postal is updated and civilians making the emergency call are also notified when an officer is en-route.

## Video Showcase

Check out our video showcase of this plugin [here](https://youtu.be/eWmeFpz8jiA).

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE](https://github.com/Sonoran-Software/sonoran_dispatchnotify/releases) to download the DispatchNotify plugin .zip file.
2. Download and install the [callcommands](https://github.com/Sonoran-Software/sonoran_callcommands/releases/tag/latest) plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the callcommands plugin.

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 5. Configuration

Review the `config_dispatchnotify.lua` file to configure the plugin to behave how you like. The file is well documented. Please review **all** the settings!

## Commands

| Command | Description |
| :--- | :--- |
| /rcall | Respond/Attach to the new dispatch call |
| /togglegps | Toggle the GPS auto-lock when dispatch updates the postal code |

### Configuration

<table>
  <thead>
    <tr>
      <th style="text-align:left">Config Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">enableUnitNotify</td>
      <td style="text-align:left">Enable incoming 911 call notifications</td>
    </tr>
    <tr>
      <td style="text-align:left">emergencyCallType</td>
      <td style="text-align:left">Specifies what emergency calls are displayed as. Some countries use different
        numbers (like 999)</td>
    </tr>
    <tr>
      <td style="text-align:left">civilCallType</td>
      <td style="text-align:left">Specifies non-emergency call types. If unused, set to blank (&quot;&quot;)</td>
    </tr>
    <tr>
      <td style="text-align:left">dotCallType</td>
      <td style="text-align:left">Some communities use 511 for tow calls. Specify below, or set blank (&quot;&quot;)
        to disable</td>
    </tr>
    <tr>
      <td style="text-align:left">respondCommandName</td>
      <td style="text-align:left">Command to respond to calls with</td>
    </tr>
    <tr>
      <td style="text-align:left">enableUnitResponse</td>
      <td style="text-align:left">
        <p>Enable call responding (self-dispatching)</p>
        <p>If disabled, running commandName will return an error to the unit</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">dispatchDisablesSelfResponse</td>
      <td style="text-align:left">If a dispatcher is detected to be online, automatically disable the response
        command.</td>
    </tr>
    <tr>
      <td style="text-align:left">enableCallerNotify</td>
      <td style="text-align:left">Enable &quot;units are on the way&quot; notifications</td>
    </tr>
    <tr>
      <td style="text-align:left">callerNotifyMethod</td>
      <td style="text-align:left">
        <p>notifyMethod: how should the caller be notified?</p>
        <p><b>none</b>: disable notification</p>
        <p><b>chat</b>: Sends a message in chat</p>
        <p><b>pnotify</b>: Uses pNotify to show a notification</p>
        <p><b>custom</b>: Use the custom event instead</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">notifyMessage</td>
      <td style="text-align:left">
        <p>NotifyMessage: Message template to use when sending to the player</p>
        <p>You can use the following replacements:</p>
        <p><b>{officer} </b>- officer name</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">incomingCallMessage</td>
      <td style="text-align:left">How should officers be notified of a new 911 call? Parameters:
        <br /><b>{location}</b> - location of call (street + postal)
        <br /><b>{description}</b> - description as given by civilian
        <br /><b>{caller}</b> - caller&apos;s name
        <br /><b>{callId}</b> - ID of the call so LEO can respond with /r911
        <br /><b>{command}</b> - The command to use</td>
    </tr>
    <tr>
      <td style="text-align:left">unitDutyMethod</td>
      <td style="text-align:left">How to detect if units are online?
        <br /><b>incad</b>: units must be logged into the CAD
        <br /><b>permissions</b>: units must have the &quot;sonorancad.dispatchnotify&quot;
        ACE permission (see docs)
        <br /><b>esxjob</b>: requires esxsupport plugin, use jobs instead for on duty
        detection
        <br /><b>custom</b>: Use custom function (defined below as unitDutyCustom)</td>
    </tr>
    <tr>
      <td style="text-align:left">esxJobsAllowed</td>
      <td style="text-align:left">What jobs should count as being on duty?</td>
    </tr>
    <tr>
      <td style="text-align:left">waypointType</td>
      <td style="text-align:left">Type of waypoint to use when officer is attached
        <br /><b>postal</b>: set gps to caller&apos;s postal (less accurate, more realistic)
        - REQUIRES <a href="postals.md">CONFIGURED POSTAL PLUGIN</a>
        <br /><b>exact</b>: set gps to caller&apos;s position (less realistic)
        <br /><b>none</b>: disable waypointing</td>
    </tr>
    <tr>
      <td style="text-align:left">waypointFallbackEnabled</td>
      <td style="text-align:left">Fall back to postal if exact coordinates cannot be found (for self-generated
        calls)</td>
    </tr>
  </tbody>
</table>

## Dispatch Call Responding

### 1. Civilian Places a 911 Call

### 2. Officer Attaches to the Call

#### A. Call Attach Command

#### B. GPS Toggle Command

## Primary Unit Tracking \(Pursuit\)

Dispatch notify can also be used to track the primary unit on a call. This will auto route attached units via GPS to the primary unit in real-time. Additionally, the postal code on the call will be continually updated for dispatchers to easily view. This is highly useful for pursuits, where additional units need to catch up and join the chase.

### 1. Toggle Unit Tracking for the Primary Unit

#### A. Via the CAD UI:

#### B. Via in-game Command:

{% hint style="danger" %}
This documentation is under construction.
{% endhint %}

### Troubleshooting

* No notifications for 911 calls
  * Units must be logged into the CAD \(by default\) or meeting the requirements depending on how the plugin is configured.
  * If using pNotify notifications, ensure that resource is running.
* Units do not automatically attach to calls
  * Ensure their [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) is set so the server knows who they are.
* Caller is not notified when units attach to the call
  * If the caller ever leaves the server and rejoins, this feature does not work.
  * If dispatch created the call within the CAD, there is no way to notify a caller.
  * Ensure you are not overriding the 911 command \(default `/911`\) with another resource.



