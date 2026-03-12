# Vehicle Registrations

## Registration Command Configuration

### Persistent Registration

When the registration command is ran a new vehicle registration will be created under the user's currently selected character in the CAD. The registration information will include the character information, license plate from the command, make, and color.

If the user already has this license plate registered under any of their characters, the registration will be moved to the currently selected character and the vehicle information will be updated.

### Temporary Registration

Running the temporary registration command will perform the same actions as above. However, the registration record will be automatically **deleted after 24 hours**.

#### Vehicle Registration Persistence

Vehicles purchased in public ER:LC servers persist their license plate across public and private servers. If a vehicle is purchased in a private server, vehicles are not persisted and are removed when the user leaves the game. For private server vehicles, it is best to use the temporary registration command.

## CAD Permission Requirements

In order to use this command in-game, players must have a [linked Roblox account](getting-started.md#linking-your-roblox-account) with the **DMV Record Add** and **DMV Record Edit** permissions to add or update vehicle registrations.

## Using the In-Game Commands

{% hint style="info" %}
_Note: Due to ER:LC's API rate limits, commands can take **up to 30 seconds** to be applied._
{% endhint %}

When in-game, users can run the customizable vehicle registration commands followed by the license plate on the vehicle.

Ex: `:log register ABC-123`

Once the registration has been created in the CAD, users will be notified by an optional in-game message.

<div><figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

## Troubleshooting

### Registration Fields Blank

<details>

<summary>Registration Fields Blank</summary>

In order for Sonoran CAD to know where to place information (license plate, color, etc.) in your custom record fields, the field IDs must match.

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

| Field ID | Use                                              |
| -------- | ------------------------------------------------ |
| `plate`  | <p>License Plate<br>Ex: <code>ABC-123</code></p> |
| `make`   | <p>Vehicle Name<br>Ex: <code>Captain</code></p>  |
| `model`  | <p>Vehicle Model<br>Ex: <code>Chevlon</code></p> |
| `year`   | <p>Vehicle Year<br>Ex: <code>1992</code></p>     |
| `color`  | <p>Vehicle Color<br>Ex: <code>Crimson</code></p> |

</details>
