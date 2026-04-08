---
description: Replace or append API IDs for a community account.
---

# Set API IDs

<mark style="color:green;">`PUT`</mark> `https://api.sonorancad.com/v2/general/api-ids`

Set or append API IDs for a community account.

## Request Body

Provide exactly one of `username` or `accountUuid`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
}
```

## Response

Returns the target `accountUuid`, saved `apiIds`, and `pushNew` mode.
