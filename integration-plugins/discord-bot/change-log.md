---
description: Changes to Sonoran Bot.
---

# Change Log

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



