---
description: Create a new identifier for an account.
---

# Create Identifier

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers`

Create a new identifier for an account.

## Request Body

```json
{
  "status": "UNAVAILABLE",
  "unitNum": "A-10",
  "name": "John Doe",
  "district": "Los Santos",
  "department": "LSPD",
  "subdivision": "Patrol",
  "rank": "Officer",
  "group": "",
  "page": "POLICE",
  "isDispatch": false
}
```
