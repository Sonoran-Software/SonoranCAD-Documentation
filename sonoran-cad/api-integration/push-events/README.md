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
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

### Configuring your Listener

#### 1. Admin Panel Configuration

In the admin panel, navigate to: Advanced &gt; In-Game Integration  
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your game server's port. Sonoran CAD will send events to `http://ip:gameport/sonorancad/event` **utilizing your existing game port**.

Push event configuration is covered as a part of the [framework installation](../../../integration-plugins/integration-plugins/framework-installation.md#5-configure-push-events).

### Developer Documentation

Many of our [integration plugins](../../../integration-plugins/integration-plugins/available-plugins/) rely on these push events for full functionality. Interested in developing your own plugins? Expand the push event and API endpoint documentation in the left side drawer.

