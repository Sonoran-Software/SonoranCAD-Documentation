---
description: Kick or ban an account in the authenticated community.
---

# Kick Or Ban User

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/account-bans`

Kick an account from the community or apply a community ban.

## Request Body

Provide exactly one account identifier.

```json
{
  "apiId": "steam:110000112345678",
  "isBan": true
}
```

## Response

Returns the target `accountUuid`, the applied `action`, and a result `message`.
