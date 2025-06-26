---
description: Implements the Wraith ARS 2X plate reader for automated plate reading.
---

# WraithV2

{% hint style="danger" %}
This submodule utilizes API endpoints that require the **Plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

This submodule is for sending plate reads to other submodules.

## Showcase Video

View our [WraithV2 showcase video](https://www.youtube.com/watch?v=5oL7Mg6LQgg)!

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the required submodules.

1. Ensure the third-party [pNotify](https://github.com/Nick78111/pNotify) addon is installed.

### 3. Configuration

In the `config_wraithv2.lua`file, set `isPluginEnabled` in the to `true`.

{% hint style="info" %}
Use of this submodule requires the Sonoran version of [Wraith ARS 2X](https://github.com/sonoran-Software/wk_wars2x)[ ](https://github.com/Sonoran-Software/wk_wars2x)radar and plate reader to function. This resource is bundled with the latest SonoranCAD release as `wk_wars2x`.

You also need [pNotify](https://github.com/Nick78111/pNotify), a third party resource that is not bundled by default.
{% endhint %}

| Config Option       | Description                                                    |
| ------------------- | -------------------------------------------------------------- |
| useExpires          | use vehicle registration expirations, or not                   |
| useMiddleInitial    | use middle initials?                                           |
| alertNoRegistration | alert if no registration was found on scan?                    |
| statusUid           | Custom record field UID containing the status                  |
| expiresUid          | Custom record field UID containing the expiration date         |
| flagOnStatuses      | List of statuses to flag/alert on                              |
| vehTypeFilter       | List of Classes that will NOT get ran through CAD              |
| notificationTimers  | Time in MS, for how long each alert type will last via pNotify |

### 4. Custom Record Handling

The in-game radar can alert you about expired registrations, BOLOs, warrants, and more:

<details>

<summary>Alert on Vehicle Status (Expired, Stolen, etc.)</summary>

When a vehicle is scanned by your radar, you can be notified if the vehicle registration status is inactive, expired, etc.

### 1. Get the Status field ID

In the custom record configuration panel, copy the field ID for your vehicle registration's status field. Typically this would be a dropdown (or "select") type field with options like "Active", "Pending", "Expired", etc.

![](<../../../../.gitbook/assets/Screenshot 2024-11-12 at 7.36.39 PM.png>)

### 2. Set the Field ID in your Config

Ensure the `statusUid` configuration value matches your status field ID from the custom record.

If your vehicle registration record has an expiration date value in it, be sure to set the `expiresUid` value to its field ID and set `useExpires` to `true`. This will display the registration expiration date in the notifications.

![](<../../../../.gitbook/assets/Screenshot 2024-11-12 at 7.44.27 PM (1).png>)

### 3. Set Status Flag Options

Customize the `flagOnStatuses` list to configure which vehicle registration statuses your radar will alter you on.

If the vehicle registration's status field (the record field ID that matches your `statusUid`) matches one of the `flagOnStatuses` values, your in-game radar will alert you.

![](<../../../../.gitbook/assets/Screenshot 2024-11-12 at 7.46.54 PM.png>)

</details>

<details>

<summary>Alert on BOLO or Warrant</summary>

When a vehicle is scanned by your radar, you can be notified of any active warrant or BOLO record with that license plate on it.

### 1. Ensure your Warrant or BOLO Record has a Status Field

In order for the radar to determine if the warrant or BOLO record is active, ensure your custom record has a `status` type field on it.

![](<../../../../.gitbook/assets/Screenshot 2024-11-12 at 7.50.05 PM.png>)

### 2. Ensure your Warrant or BOLO Record has a Plate Field

In order to match the vehicle plate with a record, ensure your custom record has a field with the field ID set to `plate`.

![](<../../../../.gitbook/assets/Screenshot 2024-11-12 at 7.51.37 PM.png>)

### 3. Receive In-Game Alerts

Your radar will alter you when a scanned vehicle matches:

* A Warrant or BOLO record with the `status` type field of `ACTIVE`
* A license plate matching the `plate` field ID of one of those active records

</details>

### 5. Set Your API ID

In order to have locked plate lookup results sent back to your CAD, don't forget to set your account [API ID](../../../../api-integration/getting-started/setting-your-api-id.md).

## Usage

For more information on using the in-game UI, please view the Sonoran version of the  [Wraith ARS 2X](https://forum.cfx.re/t/release-wraith-ars-2x-police-radar-and-plate-reader-v1-2-4/1058277)[ ](https://github.com/Sonoran-Software/wk_wars2x)release information.\
**Results are sent directly to your CAD when a license plate is locked.**

![Wraith ARS 2X Controls](<../../../../.gitbook/assets/image (314).png>)

## Sonoran wk\_wars2x&#x20;

{% hint style="info" %}
These features are not found in the original wk\_wars2x resource, and only come packaged with our version found [here](https://github.com/sonoran-Software/wk_wars2x).
{% endhint %}

### Additional Features

* Added the ability to blacklist certain vehicle classes via the config.lua, these blacklisted vehicles will show on the plate reader as the `CONFIG.noPlateValue` value (default: "NO PLATE").
* Added the feature `CONFIG.realisticPlateScanning`. This feature is disabled by default due to certain vehicles having incorrect metadata causing this feature to display `CONFIG.noPlateValue` falsely. Behavior when enabled: when you are traveling toward/away from a vehicle that does not have a front/back plate the plate reader will not be able to scan it and will display the `CONFIG.noPlateValue` value.
* Added custom sounds when a BOLO, Warrant or unregistered vehicle plate is scanned.

### Realistic Plate Scanning

Set `CONFIG.realisticPlateScanning` to `true` to enable only scanning vehicles with the ALPR when they have a plate.

Note: Some vehicles may show a plate due to missing vehicle metadata or being able to remove the plate with extras.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-11-14 172304.png" alt=""><figcaption><p>Sonoran wk_wars2x - Additional Config Options</p></figcaption></figure>

### Custom Alert Tones

Custom tones will now play when you scan a plate that is has either a BOLO, Warrant or is unregistered. These tones can be customized by replacing the existing files in the `/sonorancad/submodules/wraithv2/sfx` folder with your own. **Please note the files names need to be the same as the ones you are replacing**

## Troubleshooting

### AI Cars are Spamming the Reader

The framework ships with the `wk_wars2x` plate reader included. This will have the `config.use_sonorancad` set to `true`. When enabled, the plate reader will not run a lookup on any AI vehicle.

![Wraith - Use Sonoran CAD Config Option](<../../../../.gitbook/assets/Screen Shot 2022-04-02 at 4.18.19 PM.png>)

### Vehicles Aren't Being Flagged

#### Status

Keep in mind that AI vehicles won't display or be ran unless there's a vehicle registration record added to the CAD with that plate.

Ensure that you've correctly followed [step 5](broken-reference) and the `statusUid` and `expirationUid` fields have been set correctly, both in the CAD record template and the submodule  config.

Ensure that the `flagOnStatuses` array has the exact string/text values that match the options in your custom record template.&#x20;

#### BOLO and Warrant

Ensure that your custom BOLO and Warrant records have a field with the `type` set to `status`. Otherwise, there's no way to determine if the BOLO/Warrant is active, closed, etc. The plate reader will warn of any active BOLO or Warrant records with the vehicle plate attached _and_ the `status` type field set to active/open.

### Error: attempt to index a nil value (local 'vehicle')

Some servers will see this error in their server console:

```
sv_wraithv2.lua:112 - attempt to index a nil value (local 'vehicle')
```

To fix this, navigate to your `[sonorancad]/wk_wars2x` folder, and rename `config.dist.lua` to just `config.lua`&#x20;

The config not being renamed is the most common cause of this error, however, if for some reason that doesn't fix it, feel free to open a [support ticket](https://support.sonoransoftware.com) with us.
