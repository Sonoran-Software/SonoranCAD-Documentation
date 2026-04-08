---
description: Retrieve the stored community plan version metadata associated with the authenticated API key.
---

# Get Version

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/version`

Return the stored plan version metadata resolved during API authentication.

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/version" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns a numeric `version` value and a plan `name`.
