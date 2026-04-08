---
description: Retrieve public login-page community details by custom URL or community ID.
---

# Get Login Page

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/login-page`

Return public login-page details for a community. This endpoint does not require bearer authentication.

## Query Parameters

Provide exactly one of the following:

| Name | Type | Description |
| --- | --- | --- |
| `url` | string | Community custom domain |
| `communityId` | string | Sonoran CAD community ID |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/login-page?communityId=examplecad"
```

## Response

Returns the community login-page metadata object.
