---
description: Attach identifiers or a group to a dispatch call.
---

# Attach Units

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/attachments`

Attach identifiers or a group to a dispatch call.

## Example Body

```json
{
  "identIds": [15, 18]
}
```

Or:

```json
{
  "groupName": "CAR 51"
}
```
