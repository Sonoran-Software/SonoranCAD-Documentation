---
description: Get started with the official Sonoran Bot today!
---

# Getting Started - Discord Bot

## Setup

{% hint style="warning" %}
Setting up the bot requires you to have the `Manage Server` permissions on the Discord server for security reasons.

You must also have access to your server's [API Key information](../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md).
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=VATCtHH7GQw" %}

### 1. Invite the Bot to Your Server

[Invite the bot to your Discord server](https://discord.com/api/oauth2/authorize?client\_id=1060274480930361424\&permissions=9395244032\&scope=bot%20applications.commands). You must have the "Manage Server" permission to add bots; plus any permissions the bot requires to function.

### 2. Run the Setup Command

* After inviting the bot, run the `/setup` command.
* Enter your [Sonoran CAD ID and API key](https://info.sonorancad.com/sonoran-cad/api-integration/getting-started/retrieving-your-credentials).
* (OPTIONAL) Enter your [Sonoran CMS ID and API key](https://info.sonorancms.com/developer-api-documentation/api-integration/getting-started#gather-your-credentials).

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

You will then be presented with the results of the setup.

<figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

Note: When setting up the bot, it will automatically be set to CAD sync mode if you opted to link your CAD community. If you linked BOTH the CAD and CMS communities, it will be set to CMS mode automatically and you should [follow this document instead](https://info.sonorancms.com/integration-capabilities/discord-role-sync/getting-started).

{% hint style="info" %}
The /linkme command is only used on the primary server. Your users will automatically be associated with the secondary server(s).
{% endhint %}

### 3. Invite to Additional Servers

By default, the bot uses the `s!` prefix for all commands. This can be changed with the `setprefix` command, as noted below.

If your community uses multiple discord servers, you can link them all to the same community to utilize the permissions sync easily using the `/guildlink` command, as shown below.

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

Fill out the information (using either your CAD or CMS information), and you will receive a confirmation. At this point, you can use the other commands just like on the primary server.

## Commands Reference



{% content-ref url="commands-reference.md" %}
[commands-reference.md](commands-reference.md)
{% endcontent-ref %}

## Features

See the [Features](features/) section for instructions on how to use the various features of the Bot.

{% content-ref url="features/" %}
[features](features/)
{% endcontent-ref %}
