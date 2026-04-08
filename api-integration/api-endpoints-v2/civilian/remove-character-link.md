---
description: Unlink a sync-character ID from an account or API ID.
---

# Remove Character Link

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/civilian/character-links/{syncId}`

Unlink a sync-character ID from an account or API ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `syncId` | string | External sync character ID |

## Request Body

Provide exactly one of `accountUuid` or `apiId`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
```
