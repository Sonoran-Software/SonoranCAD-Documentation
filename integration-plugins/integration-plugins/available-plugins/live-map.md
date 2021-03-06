---
description: >-
  Sonoran CAD's live map plugin updates unit locations, unit numbers, statuses,
  and shows currently attached dispatch calls all right on the live map
  interface.
---

# Live Map

![Sonoran CAD&apos;s Custom Integrated Live Map System](../../../.gitbook/assets/live_map.png)

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
The live map will require you to open two additional ports on your server.  
**You will need to contact your hosting provider if you are unsure how to do this.**
{% endhint %}

## Installation Video

Click to view our [live map installation video](https://youtu.be/dhUCfvdLZ_U).

**Be sure you have already installed our** [**plugin framework**](../framework-installation.md)**!**

**The live map will only show units that are in your server and also actively logged into the police, fire, or EMS panel in the CAD. Be sure to have your** [**API ID**](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) **set.**

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_livemap/releases)to download the live map plugin .zip file.
2. Download and install the [push events listener](push-events.md) plugin.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the live map and push events listener plugin.

### 4. Configuration

This requires the resource `sonoran_livemap` to be loaded. This is bundled with the base resource.  
To do so, enter `start sonoran_livemap` in the console.

{% hint style="danger" %}
When using **Linux**, you will need to `start webpack` before the livemap in order to build it for the first time. You can stop webpack after it has been built. You will have to do this step whenever the `sonoran_livemap` resource is updated.
{% endhint %}

#### A. Live Map Configuration

**Convars:**

The following convars are available for you to change

| Name | Type | Default Value | Description |
| :--- | :--- | ---: | :--- |
| socket\_port | int | 30121 | Sets the port the socket server should listen on |
| livemap\_debug | int | 0 | Sets how much information gets printed to the console \(0 = none, 1 = basic information, 2 = all\) |
| blip\_file | string | "server/blips.json" | Sets the file that will contain the generated blips that is exposed via HTTP |
| livemap\_access\_control | string | "\*" | Sets the domain that is allowed to access the blips.json file \(E.g. "[https://example.com](https://example.com)" will only allow the UI on [http://example.com](http://example.com) to get the blips\), "\*" will allow everyone |

All above convars are set via the `set` command in your server config, such as `set socket_port 30000` if you wanted to change the port to 30000.

#### B. Admin Panel Configuration

![](../../../.gitbook/assets/livemap_config.png)

1. IP: Set IP to the **public** IP address of your server, 
2. Map Port: The port you specified via `socket_port` above or the default, which is `30121`.
3. Listener Port: The port you have specified in the the [`pushevents`](../../../sonoran-cad/api-integration/push-events/) plugin, by default this is `3232`.
4. Click "Save and Deploy" to deploy your live map.

Click Save And Deploy. After a few seconds, the live map should appear as a button on most CAD screens \(Police, Dispatch, etc\) and will auto-update with your unit positions.

#### C. Port Forwarding

You will need to port forward BOTH of the ports specified in the Map Port and Listener Port.  
These ports are accessed by Sonoran CAD to server position data and view the blips.  
**If you are unsure how to port forward, you will need to contact your hosting provider.**

### **5**. Set Your API ID

Don't forget to have each community member set their account [API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to properly link their in-game user to the CAD.

### **6. Enjoy!**

In the Police, Fire, EMS, or Dispatch window you can now click the "Live Map" button to view your new live map! Selecting a blip will show it's updated position and unit information.

**The live map will only show units that are in your server and also actively logged into the police, fire, or EMS panel in the CAD. Be sure to have your** [**API ID**](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) **set.**

## Troubleshooting

### Check if ports are open/server is reachable

You can manually check if your server's Live Map plugin is reachable by doing the following:

In your browser, enter the following:

```text
serverIP:MapPort/blips.json

Your Server's Public IP : Your Map Port (30121) /blips.json

123.456.789:30121/blips.json
```

If you've properly port forwarded and have the plugin running, your browser should show a screen similar to the following:

```text
{}
```

If you are unable to see the blips.json file, check the following:

1. Make sure you have the plugin running.
2. Make sure there are no other services running on your map port.
3. Otherwise, this is most likely a port forwarding issue. If you are unaware of how to port forward, please **contact your hosting provider.**

