---
description: Update account permissions and account status for a community user.
---

# Modify Account Permissions

<mark style="color:green;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/accounts/permissions`

Update permissions for a community account and optionally set its active status.

## Request Body

Provide exactly one account identifier.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}
```

## Response

Returns the target `accountUuid`, the saved `permissions` object, and the supplied `active` state.
