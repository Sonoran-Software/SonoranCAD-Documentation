---
description: Apply a permission key to an account resolved by API ID.
---

# Apply Permission Key

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/permission-keys/applications`

Apply a Sonoran CAD permission key to the account linked to an API ID.

## Request Body

```json
{
  "apiId": "steam:110000112345678",
  "permissionKey": "YOUR_PERMISSION_KEY"
}
```

## Response

Returns the target `accountUuid`, `username`, a result `message`, and the updated `permissions` object.
