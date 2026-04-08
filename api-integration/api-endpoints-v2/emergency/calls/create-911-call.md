---
description: Create a new 911 call for a server.
---

# Create 911 Call

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/calls/911`

Create a new 911 call for a server.

## Request Body

```json
{
  "isEmergency": true,
  "caller": "911 Caller",
  "location": "Alta St / Integrity Way",
  "description": "Shots fired",
  "deleteAfterMinutes": 15,
  "metaData": {
    "source": "integration"
  }
}
```
