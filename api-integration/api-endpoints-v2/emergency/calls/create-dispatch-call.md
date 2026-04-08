---
description: Create a new dispatch call.
---

# Create Dispatch Call

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls`

Create a new dispatch call and attach initial units resolved from account UUIDs or API IDs.

## Request Body

```json
{
  "origin": "RADIO_DISPATCH",
  "status": "ACTIVE",
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "description": "Clerk reports a firearm",
  "notes": [],
  "apiIds": ["steam:110000112345678"],
  "metaData": {
    "source": "integration"
  }
}
```
