---
description: Get started with the official Sonoran Bot today!
---

# Getting Started - Discord Bot

## Video Tutorial

Click [HERE](https://www.youtube.com/watch?v=uFMhJa4jbCo) to watch our video tutorial and showcase.

## Setup

{% hint style="warning" %}
Setting up the bot requires you to have the "Manage Server" permissions on the Discord server for security reasons. You must also have access to your server's [API Key information](../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md).
{% endhint %}

#### 1. Invite the Bot to Your Server

[Invite the bot to your Discord server](https://discord.com/oauth2/authorize?client_id=747991263172755528&scope=bot%20applications.commands&permissions=805686352). You must have the "Manage Server" permission to add bots; plus any permissions the bot requires to function.

#### 2. Run the Setup Command

To begin the setup process, use the `/setup` command that should have appeared on your server as a slash command. You will need the Community ID and API Key for this step. Once set up, the bot will automatically set up the other commands for permissions sync and other features.

**3. Invite to Additional Servers**

{% hint style="info" %}
The /linkme command is only used on the primary server. Your users will automatically be associated with the secondary server\(s\).
{% endhint %}

If your community has multiple discord servers \(for example, a LEO or civilian only server\), you can invite the bot to these servers as well and use the role mapping functionality. 

## Commands Reference

By default, the bot uses the `s!` prefix for all commands. This can be changed with the `setprefix` command, as noted below.

{% page-ref page="commands-reference.md" %}

## Features

See the [Features](features/) section for instructions on how to use the various features of the Bot.

{% page-ref page="features/" %}

