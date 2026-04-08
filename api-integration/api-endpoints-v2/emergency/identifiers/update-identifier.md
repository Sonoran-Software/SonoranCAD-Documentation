---
description: Update an existing identifier for an account.
---

# Update Identifier

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers/{identId}`

Update one or more editable fields on an identifier.

## Request Body

```json
{
  "unitNum": "A-12",
  "subdivision": "Traffic",
  "rank": "Senior Officer"
}
```

At least one editable field must be supplied.
