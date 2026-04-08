---
description: Check whether an API ID is linked to an account in the authenticated community.
---

# Check API ID

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/api-ids/{apiId}`

Resolve an API ID to a Sonoran CAD username and account UUID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `apiId` | string | API ID linked to a community account |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/api-ids/steam:110000112345678" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns the linked `apiId`, `username`, and `accountUuid`.
