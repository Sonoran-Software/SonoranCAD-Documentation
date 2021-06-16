---
description: Some logs sent by SonoranCAD can be reacted to for certain actions.
---

# Webhook Actions

{% hint style="warning" %}
This feature requires the **Plus** version of SonoranCAD or higher due to the API calls it needs.
{% endhint %}

### Using Webhook Actions

When a webhook is fired, SonoranBot will add a reaction \(currently a + symbol for attaching to calls, or a newspaper to open a record\) to it which triggers a specific action. They currently are:

* New Dispatch \(Call\)
  * Attaches you to the call automatically. Must have Police/Fire/EMS permissions.
* Dispatch Modified \(Call\)
  * Attaches you to the call automatically. Must have Police/Fire/EMS/permissions.
* New Record Added/Modified
  * Automatically populates a record search with the record being the result. Depending on the record, related records will also appear in the search. Must be in one of the menus \(such as Police or DMV\) for this to work.

### Setting Up

Setup is very easy. 

1. Set up [Webhooks](../../discord-webhooks.md) to the channel you desire.
2. Give the bot access to the channel these webhooks are going to. It needs at least the ability to read the channel and add reactions to messages.

That's it! More features may be added in the future.

### Examples

#### Call Attachment

![](../../../.gitbook/assets/dispatch.png)

#### Opening a Record

![](../../../.gitbook/assets/record.png)

