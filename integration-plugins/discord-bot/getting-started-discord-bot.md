---
description: Get started with the official Sonoran Bot today!
---

# Getting Started - Discord Bot

## Video Tutorial

Click [HERE](https://www.youtube.com/watch?v=uFMhJa4jbCo) to watch our video tutorial and showcase.

## Setup

{% hint style="warning" %}
Setting up the bot requires you to have Administrator permissions on the Discord server for security reasons. You must also have access to your server's [API Key information](../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md).
{% endhint %}

#### 1. Invite the Bot to Your Server

[Invite the bot to your Discord server](https://discord.com/oauth2/authorize?client_id=747991263172755528&scope=bot%20applications.commands&permissions=805686352). You must have the "Manage Server" permission to add bots; plus any permissions the bot requires to function.

#### 2. Receive the Setup Message

When the bot joins your server, it will attempt to post a message to the "System Channel" that the server has. If unset, the bot will attempt to DM the owner of the Discord server, but the owner doesn't need to be the one to set up the bot.

#### 3. Run the Setup Command

To begin the setup process, type `s!setup` in any channel the bot has access to. You will be sent a direct message \(DM\) with instructions. **Be sure DMs are enabled**! Follow the prompts from the bot to finish the setup process.

## Commands Reference

By default, the bot uses the `s!` prefix for all commands. This can be changed with the `setprefix` command, as noted below.

{% page-ref page="commands-reference.md" %}

## Features

See the [Features](features/) section for instructions on how to use the various features of the Bot.

{% page-ref page="features/" %}

