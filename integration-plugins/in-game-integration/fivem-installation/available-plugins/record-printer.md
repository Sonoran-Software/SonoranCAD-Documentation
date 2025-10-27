---
description: Print CAD PDF records to viewable, sharable, in-game inventory items!
---

# Record Printer

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **Pro** version of Sonoran CAD or higher. For more information, view our [pricing](../../../../pricing/faq/) page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](https://docs.sonoransoftware.com/promotions/fivem-hosting)!
{% endhint %}

## What is the Record Printer?

Sonoran CAD’s Record Printer seamlessly connects CAD records with the in-game world, enabling officers to generate and view official documents directly through an interactive in-game printer.

Records can be **printed at configurable printer objects or within vehicles**, shared as **inventory items**, and **viewed entirely in-game**.

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [Sonoran CAD Core](../) first.

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

### Sending Files From Sonoran CAD

When in-game, units must also be actively signed into the dispatch, police, fire, or EMS panel.

Using the records section in CAD, navigate to the record you would like to print, click the **down arrow** next to the blue **PDF** button and press **Print In-Game**.

<figure><img src="../../../../.gitbook/assets/image (101).png" alt="" width="375"><figcaption><p>Sonoran CAD - Print Record Option</p></figcaption></figure>

### Printing In-Game

After selecting **Print In-Game**, a message will appear in-game stating "**You have a new record to print. Use `/printqueue` to view queue**".

You can print this file by using the command `/print <PRINT QUEUE #>` near a configured printer (`printerObjects`) or inside a configured vehicle (`vehicleConfig`).

Once printed, the PDF will be placed in your hand with a viewer shown on your in-game screen. Buttons on-screen will allow you to maximize, minimize, and exit the window.

If configured, closing the record will [place it in your player inventory](record-printer.md#inventory-support). Otherwise, the record will be dropped on the ground and can be picked up to be viewed by other players.

<div><figure><img src="../../../../.gitbook/assets/image (110).png" alt="" width="375"><figcaption></figcaption></figure> <figure><img src="https://media.discordapp.net/attachments/624489051172503555/1430304995680714873/image.png?ex=68fb4514&#x26;is=68f9f394&#x26;hm=2ad7541a1e41ee61844b25fc133e110c058263a66a9f516212f6699953935f83&#x26;=&#x26;format=webp&#x26;quality=lossless&#x26;width=3456&#x26;height=1944" alt=""><figcaption></figcaption></figure> <figure><img src="../../../../.gitbook/assets/image (119).png" alt="" width="375"><figcaption></figcaption></figure></div>

### Inventory Support

Records can be stored and shared as an inventory item. The `frameworks` configuration item allows for inventories like ESX, QB Core, OX Inventory, and more.
