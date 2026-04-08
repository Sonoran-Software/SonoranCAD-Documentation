---
description: Update editable fields on an existing dispatch call.
---

# Update Dispatch Call

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}`

Update one or more editable fields on an existing dispatch call.

## Request Body

```json
{
  "priority": 2,
  "description": "Caller now reports two suspects",
  "trackPrimary": true
}
```

At least one editable field is required.
