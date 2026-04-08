---
description: Retrieve a single community account by account UUID, API ID, or username.
---

# Get Account

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/accounts/account`

Return a single community account record.

## Query Parameters

Provide exactly one of the following:

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | UUID | Sonoran CAD account UUID |
| `apiId` | string | API ID linked to an account |
| `username` | string | Sonoran CAD username |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/accounts/account?username=ExampleUser" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns the full community account object.
