---
description: Force a unit offline by API ID.
---

# Kick Unit

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/kick`

Force the currently selected identifier for an API ID offline.

## Request Body

```json
{
  "apiId": "steam:110000112345678",
  "reason": "Connection reset by integration"
}
```

## Response

```json
{
  "identId": 15,
  "reason": "Connection reset by integration"
}
```
