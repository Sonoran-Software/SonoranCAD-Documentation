---
description: Search records by name or plate values.
---

# Lookup Name Or Plate

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/lookups`

Search records by name and plate values.

## Request Body

```json
{
  "first": "John",
  "last": "Doe",
  "mi": "",
  "plate": "",
  "types": [7, 12],
  "partial": true
}
```

## Response

Returns a JSON array of matching record objects.
