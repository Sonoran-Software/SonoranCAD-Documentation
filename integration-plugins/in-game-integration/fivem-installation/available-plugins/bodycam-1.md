---
description: >-
  The Sonoran CAD record printer enables you to turn SonoranCAD records into
  in-game items
---

# Record Printer

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **Pro** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

## What is the Record Printer?

Sonoran CAD’s Record Printer seamlessly bridges CAD records and the in-game world, allowing officers to generate and view official documents directly through an interactive, in-game printer object.\
This system supports real-time data transmission from CAD records to in-game devices, with customizable formatting, automatic pagination, and secure access controls.\
Learn more about the integration process, configuration options, and supported record types.

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Adjust the Core Configuration

The record printer settings are stored inside of the core configuration file.

| Variable                 | Description                                                                     |
| ------------------------ | ------------------------------------------------------------------------------- |
| `recordPurgeDays`        | The number of days that the downloaded PDF's will be stored on the local server |
| `printQueueCommand`      | Command the view the print queue                                                |
| `printCommand`           | Command used to print PDF's in-game                                             |
| `clearPrintQueueCommand` | Command to clear the print queue                                                |
| `maxPrintsPerQueue`      | Max number of print requests a user can have in their queue at a time           |
| `vehicleConfig`          | Configuration of LEO vehicles that have a printer                               |
| `printerObjects`         | Array of in-game printer objects that can be walked up to and print records     |
| `printerCoords`          | Array of specific in-game coordinates where a print station is                  |
| `frameworks`             | Framework activation configuration                                              |
| `translations`           | List of translations                                                            |

## In-Game Usage

### Sending Files From SonoranCAD

When in-game, units must also be actively signed into the dispatch, police, fire, or EMS panel.

Using the records section in CAD, navigate to the record you would like to print, click the "down arrow" next to the blue "PDF" button and press "Print In-Game"

<figure><img src="../../../../.gitbook/assets/image (101).png" alt=""><figcaption><p>SonoranCAD - Print Record Option</p></figcaption></figure>

### Printing In-Game

Once you send the file from SonoranCAD, you should see a message in-game stating "You have a new record to print. Use `/printqueue` to view queue.

Upon running the command you will see the file in your queue as well as the number identifier next to the file name. You can print this file by using the command `/print <PRINT QUEUE INDEX>` near a printer or inside a configured vehicle. Upon printing the PDF viewer will then show on your in-game screen

<div><figure><img src="../../../../.gitbook/assets/image (110).png" alt=""><figcaption><p>In-Game - PDF Viewer</p></figcaption></figure> <figure><img src="https://media.discordapp.net/attachments/624489051172503555/1430304995680714873/image.png?ex=68fb4514&#x26;is=68f9f394&#x26;hm=2ad7541a1e41ee61844b25fc133e110c058263a66a9f516212f6699953935f83&#x26;=&#x26;format=webp&#x26;quality=lossless&#x26;width=3456&#x26;height=1944" alt=""><figcaption><p>In-Game - PDF Viewer Fullscreen</p></figcaption></figure></div>

<div><figure><img src="../../../../.gitbook/assets/image (119).png" alt=""><figcaption><p>In-Game PDF Viewer Minimized</p></figcaption></figure> <figure><img src="https://media.discordapp.net/attachments/624489051172503555/1430304994489405500/image.png?ex=68fb4514&#x26;is=68f9f394&#x26;hm=fda100e0e2195ea2b42ec894deb8c9600efcb51f509707a3961f13f12b1ea7a5&#x26;=&#x26;format=webp&#x26;quality=lossless&#x26;width=3456&#x26;height=1944" alt=""><figcaption><p>In-Game PDF Object in Inventory</p></figcaption></figure></div>
