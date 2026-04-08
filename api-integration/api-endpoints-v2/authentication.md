---
description: Learn how to authenticate requests against the Sonoran CAD v2 API.
---

# v2 Authentication

All current v2 API endpoints require bearer authentication.

## Base URL

```http
https://api.sonorancad.com
```

## Required Header

```http
Authorization: Bearer YOUR_API_KEY
```

## Authentication Model

Unlike v1, the v2 API does not require the community ID or API key in the request body.

Your API key is used to identify the target community automatically.

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units?onlyUnits=true&includeOffline=false" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response Formats

### Successful Requests

Successful responses return `application/json`.

### Failed Requests

Failed requests return `application/problem+json`.

Example:

```json
{
  "type": "https://httpstatuses.com/401",
  "title": "Unauthorized",
  "status": 401,
  "detail": "Missing Authorization header.",
  "instance": "/v2/emergency/servers/1/units",
  "traceId": "00-abc123..."
}
```

## Common Authentication Errors

| Status | Cause |
| --- | --- |
| `401` | Missing `Authorization` header |
| `401` | `Authorization` header is not using the `Bearer` scheme |
| `401` | API key is invalid |
| `404` | The requested `serverId` is not configured for the authenticated community |

## Notes

* v2 does not accept the v1 `id`, `key`, `type`, and `data` request body format.
* Current v2 responses include `Cache-Control: no-store` on authenticated requests.
* External rate limiting is expected to be handled in front of the API gateway.
