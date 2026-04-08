---
description: Update an existing custom record by record ID.
---

# Update Record

<mark style="color:green;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/records/{recordId}`

Update a custom record with either a full `record` payload or template replacement values.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordId` | integer | Record ID to update |

## Request Body

Provide either a full `record` object or set `useDictionary` with `templateId` and `replaceValues`.

```json
{
  "useDictionary": true,
  "templateId": 12,
  "replaceValues": {
    "{{plate}}": "XYZ987"
  }
}
```

## Response

Returns the updated record object.
