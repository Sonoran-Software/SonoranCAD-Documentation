---
description: Publish a server heartbeat with current player count.
---

# Heartbeat

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/servers/{serverId}/heartbeat`

Publish a heartbeat for a configured server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured server ID for this API key |

## Request Body

```json
{
  "playerCount": 42
}
```

## Response

Returns the `serverId`, `playerCount`, and `receivedAtUtc` timestamp.
