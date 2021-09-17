---
description: >-
  Setting your account's API ID allows you to interact with the CAD in-game via
  Sonoran CAD's integration plugin library.
---

# Integration API ID

{% hint style="info" %}
API IDs are set individually per community. Your API IDs on one community will not transfer over to another.
{% endhint %}

### Editing Your Account's API ID

1. From the start menu, navigate to System &gt; Settings

![Sonoran CAD - Settings Navigation](../../../.gitbook/assets/image%20%28184%29.png)

#### 2. Paste in your API ID and Press Save

{% hint style="info" %}
It is **highly recommended** that your community uses the [API ID plugin](../../../integration-plugins/integration-plugins/available-plugins/api-id-checker.md) to automatically check in-game if your API ID is properly set and retrieve the correct credentials with a command \(`/apiid`\). Without the correct API ID, many integration features will NOT work.

For retrieving a Discord API ID, we highly recommend the `/myid` command with our [Discord bot](../../../integration-plugins/discord-bot/features/permissions-synchronization.md#getting-started).
{% endhint %}

Typically, your API ID will be your Steam hex or a Discord numerical ID. This is how our public [plugins ](../../../integration-plugins/integration-plugins/available-plugins/)are currently structured.

When inputting your API ID, it is important to note that it is **case-sensitive**. Make sure you are putting in the **proper upper and lower case letters**!  
  
However, your community may choose to integrate their own identifier system with custom API integration scripts. If this is the case, you will need to ask an administrator from your community for what to enter.

![Sonoran CAD&apos;s API ID Setting](../../../.gitbook/assets/image%20%28185%29.png)

