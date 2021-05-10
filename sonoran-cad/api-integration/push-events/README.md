---
description: >-
  Sonoran CAD pushes event data to your community for further integration
  possibilities. Learn more below!
---

# Push Events

{% hint style="warning" %}
All push events require the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

### Configuring your Listener

#### 1. Admin Panel Configuration

In the admin panel, navigate to: Advanced &gt; In-Game Integration  
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your game server's port. Sonoran CAD will send events to `http://ip:gameport/sonorancad/event` **utilizing your existing game port**.

  
Learn more about [configuring multiple servers](../../../tutorials/customization/configuring-multiple-servers.md).

![Sonoran CAD&apos;s Event Listener Configuration](../../../.gitbook/assets/map_config_cad.png)

#### 2. Framework Configuration and Installation

You will need to download and install the [`pushevents`]() plugin installed in order to receive the events.

If you are not using the default game port `30120` you will need to specify the `SonoranListenPort`  in your `server.cfg` file.

  
Ex: Your game server is running on port 9000:  
Add `set SonoranListenPort 9000` to your `server.cfg` file.

### Developer Documentation

Many of our [integration plugins](../../../integration-plugins/integration-plugins/available-plugins/) rely on these push events for full functionality. Interested in developing your own plugins? Expand the push event and API endpoint documentation in the left side drawer.

