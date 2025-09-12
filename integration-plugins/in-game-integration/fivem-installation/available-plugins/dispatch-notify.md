---
description: >-
  Notify officers of incoming calls, allow them to attach to them, notify the
  caller, and route units via GPS in real-time to calls and the lead pursuit
  officer...all in one!
---

# Dispatch Notify

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

This submodule:

* Notifies officers of incoming calls
* [Allows officers to attach to calls via command](dispatch-notify.md#2-officer-attaches-to-the-call)
* Automatically routes attached units to the postal code
* Unit GPS routing is updated whenever the dispatch postal is updated
* [Allows the call postal and GPS routing to be automatically updated to the primary unit's location](dispatch-notify.md#primary-unit-tracking-pursuit)
* Notifies the civilian making the emergency call when an officer is en-route.

## Video Showcase

Check out our video showcase of this submodule [here](https://youtu.be/eWmeFpz8jiA).

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Dispatch Notify requires you to [enable the following submodules](../submodule-configuration/#activating-a-submodule):

* &#x20;`callcommands`
* `locations`
* `postals`

### 3. Add your Game Server IP and Port

Be sure to have your game server IP and port set in the admin panel under `Advanced` > `In-Game Integration` > `Server Events and Integrated Live Map`

![Sonoran CAD - Server IP and Port](<../../../../.gitbook/assets/image (195).png>)

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

### 5. Configuration

Review the `dispatchnotify_config.lua` file to configure the submodule to behave how you like. The file is well documented. Please review **all** the settings!

## Commands

| Command    | Description                                                    |
| ---------- | -------------------------------------------------------------- |
| /rcall     | Respond/Attach to the new dispatch call                        |
| /togglegps | Toggle the GPS auto-lock when dispatch updates the postal code |

### Configuration

| Config Value                 | Description                                                                                                                                                                                                                                                                                                                                                                                           |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| enableUnitNotify             | Enable incoming 911 call notifications                                                                                                                                                                                                                                                                                                                                                                |
| emergencyCallType            | Specifies what emergency calls are displayed as. Some countries use different numbers (like 999)                                                                                                                                                                                                                                                                                                      |
| civilCallType                | Specifies non-emergency call types. If unused, set to blank ("")                                                                                                                                                                                                                                                                                                                                      |
| dotCallType                  | Some communities use 511 for tow calls. Specify below, or set blank ("") to disable                                                                                                                                                                                                                                                                                                                   |
| respondCommandName           | Command to respond to calls with                                                                                                                                                                                                                                                                                                                                                                      |
| enableUnitResponse           | <p>Enable call responding (self-dispatching)</p><p>If disabled, running commandName will return an error to the unit</p>                                                                                                                                                                                                                                                                              |
| dispatchDisablesSelfResponse | If a dispatcher is detected to be online, automatically disable the response command.                                                                                                                                                                                                                                                                                                                 |
| enableCallerNotify           | Enable "units are on the way" notifications                                                                                                                                                                                                                                                                                                                                                           |
| unitNotifyMethod             | <p><strong>chat</strong>: Sends a message in chat</p><p><strong>pnotify</strong>: Uses pNotify to show a notification</p><p><strong>custom</strong>: Use the custom event <code>SonoranCAD::dispatchnotify:IncomingCallNotify</code>instead (Provides single parameter) - The message.</p>                                                                                                            |
| notifyMessage                | <p>NotifyMessage: Message template to use when sending to the player</p><p>You can use the following replacements:</p><p><strong>{officer}</strong> - officer name</p>                                                                                                                                                                                                                                |
| incomingCallMessage          | <p>How should officers be notified of a new 911 call? Parameters:<br><strong>{location}</strong> - location of call (street + postal)<br><strong>{description}</strong> - description as given by civilian<br><strong>{caller}</strong> - caller's name<br><strong>{callId}</strong> - ID of the call so LEO can respond with /r911<br><strong>{command}</strong> - The command to use</p>            |
| unitDutyMethod               | <p>How to detect if units are online?<br><strong>incad</strong>: units must be logged into the CAD<br><strong>permissions</strong>: units must have the "sonorancad.dispatchnotify" ACE permission (see docs)<br><strong>esxjob</strong>: requires esxsupport submodule, use jobs instead for on duty detection<br><strong>custom</strong>: Use custom function (defined below as unitDutyCustom)</p> |
| esxJobsAllowed               | What jobs should count as being on duty?                                                                                                                                                                                                                                                                                                                                                              |
| waypointType                 | <p>Customise the title of a call made in the CAD<br><strong>postal</strong>: set gps to caller's postal (less accurate, more realistic) - REQUIRES <a href="postals.md">CONFIGURED POSTAL </a>SUBMODULE<br><strong>exact</strong>: set gps to caller's position (less realistic)<br><strong>none</strong>: disable waypointing</p>                                                                    |
| waypointFallbackEnabled      | Fall back to postal if exact coordinates cannot be found (for self-generated calls)                                                                                                                                                                                                                                                                                                                   |
| callTitle                    | <p>Type of waypoint to use when officer is attached<br><strong>Default</strong>: OFFICER RESPONSE</p>                                                                                                                                                                                                                                                                                                 |
| sendNotesToUnits             | Enable "the sending of notes to units" notifications                                                                                                                                                                                                                                                                                                                                                  |
| noteNotifyMethod             | <p><strong>chat</strong>: Sends a message in chat</p><p><strong>pnotify</strong>: Uses pNotify to show a notification</p><p><strong>custom</strong>: Use the custom event <code>SonoranCAD::dispatchnotify:NewCallNote</code>instead (Provides single parameter) - The message.</p>                                                                                                                   |
| notifyMessage                | <p>NotifyMessage: Message template to use when sending to the player</p><p>You can use the following replacements:</p><p><strong>{callid}</strong> - The CAD Call ID</p><p><strong>{note}</strong> - The Note Added</p>                                                                                                                                                                               |
| enableAddNote                | Enable "the adding of the notes" notifications                                                                                                                                                                                                                                                                                                                                                        |
| addNoteCommand               | Command to add notes to a call with                                                                                                                                                                                                                                                                                                                                                                   |
| enableAddPlate               | Enable "the adding of plates that are locked" notifications - REQUIRES [CONFIGURED WRAITHV2 ](broken-reference)SUBMODULE                                                                                                                                                                                                                                                                              |
| addPlateCommand              | Command to add plates to a call with                                                                                                                                                                                                                                                                                                                                                                  |

## Dispatch Call Responding

### 1. Civilian Places a 911 Call

This call can be placed from the Civilian menu of the CAD, or via the `/911` command in-game, supplied by the [callcommands ](call-commands.md)submodule.

### 2. Officer Attaches to the Call

All on-duty officers get a notification (if configured) and can use the attach command to respond to the call.

#### A. Call Attach Command

By default, this command is `/rcall <callid>`, where callid is the ID shown in the call notification.

#### B. GPS Toggle Command

Units can optionally choose to disable the postal updating when dispatch updates the call (or primary unit tracking) by using the `/togglegps` command. This is a toggle and will be shown in chat what it gets changed to. This is `ON` by default.

## Primary Unit Tracking (Pursuit)

Dispatch notify can also be used to track the primary unit on a call. This will auto route attached units via GPS to the primary unit in real-time. Additionally, the postal code on the call will be continually updated for dispatchers to easily view. This is highly useful for pursuits, where additional units need to catch up and join the chase.

### 1. Toggle Unit Tracking for the Primary Unit

#### A. Via the CAD UI:

Dispatchers can set the primary unit to any unit currently attached to the call. The slider next to the Primary Unit box will toggle tracking mode. When enabled, the postal will automatically update based on the primary unit's location and be sent to all attached units.

![Sonoran CAD - Primary Unit](<../../../../.gitbook/assets/image (30).png>)

A unit can also designate themselves as primary, but only if Self Dispatch is enabled.

![Sonoran CAD - Primary Unit](<../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png>)

## Troubleshooting

* No notifications for 911 calls
  * Units must be logged into the CAD (by default) or meeting the requirements depending on how the submodule is configured.
  * If using pNotify notifications, ensure that resource is running.
* Units do not automatically attach to calls
  * Ensure their [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) is set so the server knows who they are.
* Caller is not notified when units attach to the call
  * If the caller ever leaves the server and rejoins, this feature does not work.
  * If dispatch created the call within the CAD, there is no way to notify a caller.
  * Ensure you are not overriding the 911 command (default `/911`) with another resource.
