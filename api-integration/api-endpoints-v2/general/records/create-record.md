---
description: Create a new custom record using a raw record payload or template replacement values.
---

# Create Record

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/records`

Create a custom record for a target account.

## Request Body

Provide exactly one of `accountUuid` or `apiId` as the target user. Then provide either a full `record` object or set `useDictionary` with `recordTypeId` and `replaceValues`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
}
```

## Response

Returns the created record object.
