---
description: Retrieve active, emergency, and closed calls for a server.
---

# Get Calls

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/calls`

Retrieve dispatch calls, emergency calls, and recent closed calls.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `closedLimit` | integer | `10` | Number of closed calls returned |
| `closedOffset` | integer | `0` | Closed-call offset |
| `type` | string | `SEARCH_ALL` | `DISPATCH_CALL`, `EMERGENCY_CALL`, or `SEARCH_ALL` |

## Response

```json
{
  "activeCalls": [],
  "emergencyCalls": [],
  "closedCalls": [],
  "closedCallCount": 0
}
```
