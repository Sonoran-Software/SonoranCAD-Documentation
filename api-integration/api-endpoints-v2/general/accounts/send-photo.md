---
description: Send a photo URL to active connections for an API ID.
---

# Send Photo

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/photos`

Send a photo URL to every active connection linked to an API ID.

## Request Body

```json
{
  "apiId": "steam:110000112345678",
  "url": "https://cdn.example.com/mugshots/example.png"
}
```

## Response

Returns the target `apiId` and the number of connections the photo was delivered to.
