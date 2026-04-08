---
description: Set status for one or more identifiers.
---

# Set Unit Status

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/status`

Set a new unit status for one or more identifiers resolved by `accountUuid`, `apiId`, `apiIds`, or `identIds`.

## Request Body

```json
{
  "apiIds": ["steam:110000112345678"],
  "status": "ENROUTE"
}
```

## Status Values

`UNAVAILABLE`, `BUSY`, `AVAILABLE`, `ENROUTE`, `ON_SCENE`, `OFFLINE`

## Response

```json
{
  "updated": 1,
  "status": "ENROUTE"
}
```
