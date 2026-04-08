---
description: Set the selected character for an account or API ID.
---

# Set Selected Character

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/civilian/selected-character`

Set the selected character or selected sync character for an account.

## Request Body

Provide exactly one of `accountUuid` or `apiId`.

```json
{
  "apiId": "steam:110000112345678",
  "characterId": "1042"
}
```

`characterId` may be a numeric Sonoran character ID or a sync character string ID.
