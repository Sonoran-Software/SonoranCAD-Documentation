---
description: Retrieve all record templates for the authenticated community.
---

# Get Templates

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/templates`

Return every record template configured for the authenticated community.

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/templates" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns a JSON array of record template objects.
