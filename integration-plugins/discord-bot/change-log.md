---
description: Changes to Sonoran Bot.
---

# Change Log

### 2021-08-08

{% tabs %}
{% tab title="Updates" %}
* Add new `/changeprimary` command to allow admins to change what guild should the bot consider to be the "primary" for the purposes of commands.
{% endtab %}
{% endtabs %}

## 2021-07-04

{% tabs %}
{% tab title="Updates" %}
* Update to the latest discord.js dev release - will add buttons/dropdown support soon!
{% endtab %}

{% tab title="Fixes" %}
* Resolve crash when a command is used before the community is set up.
* Resolve some permissions-related issues with embeds and reactions.
{% endtab %}
{% endtabs %}

## 2021-06-26

{% tabs %}
{% tab title="Updates" %}
* Syncing setup commands now require the executor to have permission key permissions in their SonoranCAD community rather than requiring Administrator. This affects:
  * `/maprole`
  * `/unmaprole`
  * `/syncroles`
  * `s!showrolemap`
* Added a new slash command `/removelink` for administrators to delete secret key links on other accounts, usually to remove an accidental link on two accounts.
{% endtab %}

{% tab title="Fixes" %}
* The bot will also attempt to message the first available channel its welcome message, if a system channel is not configured.
{% endtab %}
{% endtabs %}



