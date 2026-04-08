---
description: Replace configured community servers.
---

# Set Servers

<mark style="color:green;">`PUT`</mark> `https://api.sonorancad.com/v2/general/servers`

Replace the configured server list for the authenticated community.

## Request Body

```json
{
  "deployMap": true,
  "servers": []
}
```

## Response

Returns the saved server configuration object.
