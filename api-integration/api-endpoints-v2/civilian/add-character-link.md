---
description: Link a sync-character ID to an account or API ID.
---

# Add Character Link

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/civilian/character-links/{syncId}`

Link a sync-character ID to an account or API ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `syncId` | string | External sync character ID |

## Request Body

Provide exactly one of `accountUuid` or `apiId`.

```json
{
  "apiId": "steam:110000112345678"
}
```
