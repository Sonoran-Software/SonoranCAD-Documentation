---
description: Search records by numeric, account-backed, or secret-backed values.
---

# Lookup By Value

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/lookups/by-value`

Search records by a typed lookup value.

## Request Body

```json
{
  "searchType": "NUMBER",
  "value": "451",
  "types": [12]
}
```

## Response

Returns a JSON array of matching record objects.
