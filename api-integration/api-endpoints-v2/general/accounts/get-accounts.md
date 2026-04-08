---
description: Retrieve paginated community accounts.
---

# Get Accounts

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/accounts`

Return paginated community accounts.

## Query Parameters

| Name | Type | Description |
| --- | --- | --- |
| `limit` | integer | Page size. Maximum `100`. Default `100` |
| `offset` | integer | Page offset. Default `0` |
| `status` | string | Account validation status. Default `VALIDATED` |
| `username` | string | Optional username filter |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/accounts?limit=25&offset=0&status=VALIDATED" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns a `pagination` object and an `accounts` array.
