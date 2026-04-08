---
description: Add a note to a dispatch call.
---

# Add Call Note

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/notes`

## Request Body

```json
{
  "note": "Suspect vehicle fleeing northbound",
  "noteType": "text",
  "label": "Integration"
}
```
