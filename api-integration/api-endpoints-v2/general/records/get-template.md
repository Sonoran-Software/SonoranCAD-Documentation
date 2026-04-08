---
description: Retrieve a single record template by record type ID.
---

# Get Template

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/templates/{recordTypeId}`

Return one record template by its record type ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordTypeId` | integer | Record type ID to retrieve |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/templates/12" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns the matching record template object.
