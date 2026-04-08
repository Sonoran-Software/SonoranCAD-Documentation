---
description: Remove a custom record by record ID.
---

# Delete Record

<mark style="color:green;">`DELETE`</mark> `https://api.sonorancad.com/v2/general/records/{recordId}`

Delete a custom record by its record ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordId` | integer | Record ID to remove |

## Example Request

```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/general/records/451" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns the removed `recordId`.
