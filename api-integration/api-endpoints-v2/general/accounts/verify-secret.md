---
description: Resolve an account from a Sonoran CAD account secret.
---

# Verify Secret

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/secrets/verify`

Verify an account secret and return the matched account UUID.

## Request Body

```json
{
  "secret": "00000000-0000-0000-0000-000000000000"
}
```

## Response

Returns an object keyed by the resolved `accountUuid` with the matching `secret` value.
