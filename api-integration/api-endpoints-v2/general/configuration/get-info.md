---
description: Retrieve authenticated community metadata and shared codes.
---

# Get Info

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/info`

Return the authenticated community UUID, community metadata, and shared code lists.

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/info" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns `uuid`, `community`, and `codes`.
