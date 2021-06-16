---
description: >-
  React to Sonoran CAD event webhooks to attach to dispatch calls, view modified
  records, and more!
---

# Webhook Actions

{% hint style="warning" %}
Due to the API calls, this feature requires the **Plus** version of SonoranCAD or higher.
{% endhint %}

## Using Webhook Actions

When a Discord webhook is fired, SonoranBot will add a reaction allowing you to react for a specific action.

### Available Reactions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Webhook</th>
      <th style="text-align:left">Reaction Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">New Dispatch</td>
      <td style="text-align:left">
        <p>React to attach to the dispatch call in the CAD.</p>
        <p>Remove the reaction to detach.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Modified Dispatch</td>
      <td style="text-align:left">
        <p>React to attach to the dispatch call in the CAD.</p>
        <p>Remove the reaction to detach.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">New Record</td>
      <td style="text-align:left">
        <p></p>
        <p>Automatically populates a record search with the record being the result.
          Depending on the record, related records will also appear in the search.
          Must be in one of the menus (such as Police or DMV) for this to work.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Modified Record</td>
      <td style="text-align:left">
        <p></p>
        <p>Automatically populates a record search with the record being the result.
          Depending on the record, related records will also appear in the search.
          Must be in one of the menus (such as Police or DMV) for this to work.</p>
      </td>
    </tr>
  </tbody>
</table>

### Setting Up

1. Configure [Webhooks](../../discord-webhooks.md) to the channel you desire.
2. Give the bot access to the channel these webhooks are going to. It needs at least the ability to read the channel and add reactions to messages.

## Examples

### Call Attachment

![](../../../.gitbook/assets/dispatch.png)

### Opening a Record

![](../../../.gitbook/assets/record.png)

