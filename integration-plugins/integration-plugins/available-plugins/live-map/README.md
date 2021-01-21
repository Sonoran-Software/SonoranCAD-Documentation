---
description: >-
  Sonoran CAD's live map plugin updates unit locations, unit numbers, statuses,
  and shows currently attached dispatch calls all right on the live map
  interface.
---

# Live Map

![Sonoran CAD&apos;s Custom Integrated Live Map System](../../../../.gitbook/assets/live_map.png)

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
The live map will require you to open **two additional ports** on your server.  
**You will need to contact your hosting provider if you are unsure how to do this.**
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../pricing/vps-hosting.md)!
{% endhint %}

## Installation Video

Click to view our [live map installation video](https://youtu.be/dhUCfvdLZ_U).

**Be sure you have already installed our** [**plugin framework**](../../framework-installation.md)**!**

**The live map will only show units that are in your server and also actively logged into the police, fire, or EMS panel in the CAD. Be sure to have your** [**API ID**](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) **set.**

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_livemap/releases)to download the live map plugin .zip file.
2. Download and install the [push events listener](../push-events.md) plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../../plugin-installation/) for the live map and push events listener plugin.

### 4. Configuration

This requires the resource `sonoran_livemap` to be loaded. This is bundled with the base resource.

1. Add a new line for `ensure sonoran_livemap` into your `server.cfg` file.

#### ERROR: Couldn't start resource sonoran\_livemap

![Error message without starting webpack](../../../../.gitbook/assets/image%20%2850%29.png)

Particularly with **Linux**, some users have an additional installation step.

First, run `start webpack` in your server console _before_ running `start sonoran_livemap` in order to build it for the first time. You can `stop webpack` after it has been built.

You will have to do this step whenever the `sonoran_livemap` resource is updated.

#### A. Live Map Configuration

**Convars:**

| Name | Type | Default Value | Description |
| :--- | :--- | ---: | :--- |
| socket\_port | int | 30121 | Sets the port the socket server should listen on |
| livemap\_debug | int | 0 | Sets how much information gets printed to the console \(0 = none, 1 = basic information, 2 = all\) |
| blip\_file | string | "server/blips.json" | Sets the file that will contain the generated blips that is exposed via HTTP |
| livemap\_access\_control | string | "\*" | Sets the domain that is allowed to access the blips.json file \(E.g. "[https://example.com](https://example.com)" will only allow the UI on [http://example.com](http://example.com) to get the blips\), "\*" will allow everyone |

All above convars are set via the `set` command in your server config, such as `set socket_port 30000` if you wanted to change the port to 30000.

#### B. Admin Panel Configuration

{% hint style="warning" %}
IMPORTANT: You must use an unused port for both the map and listener ports. It cannot be the same as the port used to connect to your server \(which is by default 30120\).
{% endhint %}

![](../../../../.gitbook/assets/livemap_config.png)

1. IP: Set IP to the **public** IP address of your server, 
2. Map Port: The port you specified via `socket_port` above or the default, which is `30121`.
3. Listener Port: The port you have specified in the the [`pushevents`](../../../../sonoran-cad/api-integration/push-events/) plugin, by default this is `3232`.
4. Click "Save and Deploy" to deploy your live map.

Click Save And Deploy. After a few seconds, the live map should appear as a button on most CAD screens \(Police, Dispatch, etc\) and will auto-update with your unit positions.

#### C. Port Forwarding

You will need to port forward BOTH of the ports specified in the Map Port and Listener Port.  
These ports are accessed by Sonoran CAD to server position data and view the blips.  
**If you are unsure how to port forward, you will need to contact your hosting provider.**

### **5**. Set Your API ID

Don't forget to have each community member set their account [API ID](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link their in-game user to the CAD.

### **6. Enjoy!**

In the Police, Fire, EMS, or Dispatch window you can now click the "Live Map" button to view your new live map! Selecting a blip will show it's updated position and unit information.

**The live map will only show units that are in your server and also actively logged into the police, fire, or EMS panel in the CAD. Be sure to have your** [**API ID**](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) **set.**

## When are Player Blips Displayed?

Players will only show on the map when **ALL** of the following conditions are met:

1. The player has their [API ID set in the CAD](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).
2. The player actively is logged into the police, fire, or EMS page.
3. The player has the [correct server selected in the CAD](../../../../tutorials/customization/configuring-multiple-servers.md), on the top right of the page.
4. The player is actively logged into the server.
5. The player has Steam, Discord, or other identifier type program running:
   * If the server API IDs are based on the Steam HEX, **the player must have Steam running**.
   * If the server API IDs are based on Discord IDs, **the player must have Discord running**.

## Using Different Ports

If you are not using the default ports `30121` \(map port\) and `3232` \(listener/push events port\) you will need to change these.

Your hosting provider may give you other ports, or you may have services already running on these default ports. You will need **TWO** open ports not being used by any other service.

1. Navigate to your server's `server.cfg` file.
2. Add the lines to set the convar values to the ports you are using
   * Ex: Your hosting provider opens port `8000` and `9000` for you to use.
     * `set socket_port 8000` for the live map port.
     * `set SonoranListenPort 9000` for the [push events](../../../../sonoran-cad/api-integration/push-events/) port.
       * **Make sure both of these lines are BEFORE/ABOVE your `ensure sonoran_livemap` and `ensure sonorancad` lines in the `server.cfg`.**
3. Update the ports in the admin panel setting the new map and listener ports.
4. Save everything, restart your server, and deploy the live map.

**If you are unsure how to open additional ports, you will need to contact your hosting provider.**

## Troubleshooting

If you're still having issues, check out our troubleshooting steps below:

{% page-ref page="live-map-troubleshooting.md" %}

