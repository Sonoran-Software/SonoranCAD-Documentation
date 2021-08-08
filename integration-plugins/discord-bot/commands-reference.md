---
description: 'List of all bot commands. <> are required arguments, [] are optional.'
---

# Commands Reference

### Publicly Usable

| Command | Arguments | Description |
| :--- | :--- | :--- |
| help  | \[command\] | Shows a help box for the specific command \(if given\). Will only show commands you have access to. |
| ping | None | Check the bot's ping. |
| uptime | None | Check the bot's uptime. |
| checkperms | None | Check what your permission level is for certain actions. |

### Usable by Linked Servers

| Command | Arguments | Description | Permission Needed |
| :--- | :--- | :--- | :--- |
| panic | None | Toggles panic button for your unit. | Police/Fire/EMS |
| penal | &lt;search term&gt; | Searches the community's penal code titles. | All |

### Setup and Settings

| Command | Arguments | Description | Permission Needed |
| :--- | :--- | :--- | :--- |
| setprefix | &lt;newprefix&gt; | Sets a new command prefix for the bot. | Manage Server |
| showrolemap | None | Shows the current role mapping setup. | Administrator |

## Slash Commands Reference

The following commands are general commands for controlling the bot's behavior. Features may add additional commands to the bot.

| Command | Arguments | Description | Permission Needed |
| :--- | :--- | :--- | :--- |
| setup | None | Sets up a new guild. | Manage Server |
| changeprimary | newguildid | Change the primary server the bot will use. This affects the linking commands. | Manage Server |
| caduser | \[discordid\] | Shows if you have connected with SonoranCAD properly. | Everyone |

This list was last updated on 8/8/2021. Use the `help` command for an updated list of commands you have access to.

