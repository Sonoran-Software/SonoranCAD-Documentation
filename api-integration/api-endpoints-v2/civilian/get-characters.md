---
description: Retrieve characters for an account or API ID.
---

# Get Characters

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/civilian/characters`

Retrieve characters for a Sonoran CAD account or a linked API ID.

## Query Parameters

Provide exactly one of the following:

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | UUID | Sonoran CAD account UUID |
| `apiId` | string | API ID linked to a Sonoran CAD account |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/civilian/characters?apiId=steam:110000112345678" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns a JSON array of character records.
