---
description: Learn how to authenticate requests against the Sonoran CAD v2 API.
---

# v2 Authentication

All current v2 API endpoints require bearer authentication.

## Base URL

```http
https://api.sonorancad.com
```

## Required Headers

| Header | Value | Description |
| --- | --- | --- |
| `Authorization` | `Bearer YOUR_API_KEY` | Authenticates the request |
| `Accept` | `application/json` | Recommended for all requests |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units?onlyUnits=true&includeOffline=false" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch(
  "https://api.sonorancad.com/v2/emergency/servers/1/units?onlyUnits=true&includeOffline=false",
  {
    method: "GET",
    headers: {
      Authorization: "Bearer YOUR_API_KEY",
      Accept: "application/json",
    },
  }
);

const data = await response.json();
console.log(data);
```
{% endtab %}

{% tab title="PowerShell" %}
```powershell
$headers = @{
  Authorization = "Bearer YOUR_API_KEY"
  Accept = "application/json"
}

Invoke-RestMethod `
  -Method Get `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/units?onlyUnits=true&includeOffline=false" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

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
