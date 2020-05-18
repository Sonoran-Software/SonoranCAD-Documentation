---
description: >-
  Sonoran CAD pushes event data to your community for further integration
  possibilities. Learn more below!
---

# Push Events

{% hint style="warning" %}
All push events require the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

### Configuring your Listener

#### 1. Admin Panel Configuration

In the admin panel, navigate to: Advanced &gt; In-Game Integration  
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your new listener port. By default, this is port `3232`.  
Learn more about [configuring multiple servers](../../../tutorials/customization/configuring-multiple-servers.md).

![Sonoran CAD&apos;s Event Listener Configuration](../../../.gitbook/assets/map_config_cad.PNG)

#### 2. Framework Configuration

Ensure you have **port forwarded** your new listener port. By default, this is port `3232`.  
You will need to download and install the [`pushevents`](../../../integration-plugins/integration-plugins/available-plugins/push-events.md) plugin installed in order to receive the events.

{% hint style="danger" %}
You will need to properly port forward your listener port.  
If you are unsure how to do this, you will need to **contact your hosting provider**.
{% endhint %}

