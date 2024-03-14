---
description: >-
  The Sonoran CAD bodycam enables dispatchers to see live images from units
  in-game.
---

# Body Camera

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **Pro** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

<figure><img src="../../../.gitbook/assets/bodycam.png" alt=""><figcaption></figcaption></figure>

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Install Locations

The [locations plugin](locations.md) includes all logic required to send bodycam images to the CAD.

### 3. Adjust the Framework Configuration

The bodycam settings are stored inside of the framework configuration file.

| Variable                        | Description                                                                                                                                                                                                                             |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `bodycamEnabled`                | <p>Enables or disables the body camera command.<br>Default: <code>true</code></p>                                                                                                                                                       |
| `bodycamBeepFrequency`          | <p>Adjusts the frequency at which unit body camera beeps when turned on(in milliseconds).<br>Default: <code>30000</code> (30 seconds)</p>                                                                                               |
| `bodycamPlayBeeps`              | <p>Enables or disables the body camera beeping when turned on.<br>Default: <code>true</code></p>                                                                                                                                        |
| `bodycamScreenshotFrequency`    | <p>Adjusts the frequency at which unit body cameras update (in milliseconds).<br>Default: <code>2000</code> (2 seconds)</p>                                                                                                             |
| `bodycamOverlayEnabled`         | <p>Enables or disables the blinking body camera image on screen when enabled.<br>Default <code>true</code></p>                                                                                                                          |
| `bodycamOverlayLocation`        | <p>The position (corner) of the screen where the body camera image is displayed.<br>Options: <code>top-left</code>, <code>top-right</code>, <code>bottom-left</code>, <code>bottom-right</code> <br>Default: <code>top-right</code></p> |
| `bodycamCommandToggle`          | <p>The command name to toggle your body camera on or off.<br>Default: <code>bodycam</code></p>                                                                                                                                          |
| `bodycamCommandChangeFrequency` | <p>The command to adjust your individual body camera screenshot frequency to be different than the server's <code>bodycamScreenshotFrequency</code> value.<br>Default: <code>bodycamFreq</code></p>                                     |

## In-Game Usage

When in-game, units must also be actively signed into the dispatch, police, fire, or EMS panel.

Use the `/bodycam` command to toggle your body camera on or off.

#### Body Camera Overlay

If enabled in your framework configuration, a periodic beep and blinking body camera logo will appear on your screen reflecting that your body camera is active.

<figure><img src="../../../.gitbook/assets/SonoranCAD Logo_Icon_1.gif" alt="" width="85"><figcaption></figcaption></figure>

## CAD Usage

### Active Units

In the active units panel, units with their body camera enabled will show a pulsing camera icon.

#### Preview:

Hover over this icon to see a preview image of their body camera.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-13 121327.png" alt="" width="375"><figcaption></figcaption></figure>

#### Window:

Click the icon to open an adjustable window of their body camera.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-13 121257.png" alt="" width="375"><figcaption></figcaption></figure>

### Live Map

In the live map, units with their body camera enabled will show a pulsing camera icon.

#### Preview:

Click on the unit blip to view a live preview of their body camera in the unit action menu.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-03-13 121420.png" alt="" width="375"><figcaption></figcaption></figure>

## Troubleshooting

### No such export requestClientScreenshot in resource screenshots-basic

Some servers may see the following error print in their console:

`SCRIPT ERROR: @sonorancad/core/screenshot.lua:15: No such export requestClientScreenshot in resource screenshots-basic`

This means that you do not have the [screenshot-basic](https://github.com/citizenfx/screenshot-basic) resource installed on your server.&#x20;

We recommend that you update your server artifacts, as newer versions come with this resource installed by default. Alternatively, you can manually install it from [GitHub](https://github.com/citizenfx/screenshot-basic).

## Disclaimer

_Please note that this feature is in early development and may exhibit instability, influenced by server and network performance. Body camera images are generated by the client and temporarily stored on the community's server. Viewing these images, whether by dispatchers or units, involves active requests to your CFX nucleus proxy, leading to increased network traffic and processing demands._
