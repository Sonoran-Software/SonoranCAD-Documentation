# Traffic Stops

## Traffic Stop Integration

When the the traffic stop command is used a dispatch call will be created in the CAD.

This call will:

* Attach the unit that performed the command
* Include the unit's address and postal code
* [Display on the live map](3d-live-map.md)
* Include the vehicle's make, model, year, color, and license plate in the [customizable description template](traffic-stops.md#dispatch-description)
* [Include the customizable 10-code](traffic-stops.md#id-10-code)
* Automatically search the license plate

## Traffic Stop Command Configuration

### Command

Customize the command from `:log ts` to something custom.

### Dispatch Description

When the traffic stop call is created, the call description can contain customizable information about the vehicle, license plate, and more. Select the `</>` icon to view available variables, click-to-copy, and paste them into the description.

#### 10-Code

When the traffic stop call is created, it will use the selected [custom 10-code](../../tutorials/customization/10-codes.md).

## CAD Permission Requirements

In order to use this command in-game, players must have a [linked Roblox account](getting-started.md#linking-your-roblox-account) with the **DMV Police** or **Dispatch** permissions to create a traffic stop call.

## Using the In-Game Commands

{% hint style="info" %}
_Note: Due to ER:LC's API rate limits, commands can take **up to 30 seconds** to be applied._
{% endhint %}

### License Plate Options

#### Automatic

The CAD will automatically find the closest vehicle to the unit. If the [vehicle is registered in the CAD](vehicle-registrations.md), it will automatically fill the license plate and other vehicle information.

Ex: `:log ts`

#### Manual Plate Entry

The CAD will automatically find the closest vehicle to the unit. If the vehicle is not registered in the CAD, it will use the manually entered license plate number.

Ex: `:log ts ABC-123`

### Result

Once the command has been ran, a traffic stop call will be generated with the details, a plate lookup will open, and the call will be visible on the [live map](3d-live-map.md).

<div><figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure></div>
