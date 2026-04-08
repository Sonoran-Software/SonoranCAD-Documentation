---
description: Retrieve configured community servers.
---

# Get Servers

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/servers`

Return the configured server list for the authenticated community.

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/servers" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns the community server configuration object.
