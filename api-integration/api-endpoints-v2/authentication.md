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
{% tab title="Sonoran.lua" %}
```lua
-- luarocks install sonoran.lua
local Sonoran = require("sonoran")

local sonoran = Sonoran.createClient({
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran:getUnitsV2({
  onlyUnits = true,
  includeOffline = false
})

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}

{% tab title="Sonoran.js" %}
```javascript
// npm install @sonoransoftware/sonoran.js
const Sonoran = require('@sonoransoftware/sonoran.js');

(async () => {
  const instance = new Sonoran.Instance({
    communityId: 'YOUR_COMMUNITY_ID',
    apiKey: 'YOUR_API_KEY',
    product: Sonoran.productEnums.CAD,
    serverId: 1,
  });

  const response = await instance.cad.getUnitsV2({
    onlyUnits: true,
    includeOffline: false,
  });
  console.log(response);
})();
```
{% endtab %}

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

## Rate Limits

All v2 endpoints are rate limited per API key. Limits vary by endpoint, so check the individual endpoint page for the current enforced limit.

When a request is rate limited, the API returns `429 Too Many Requests`.

Example:

```json
{
  "message": "API rate limit exceeded",
  "request_id": "9457fb389b3729164e453e4db4328909"
}
```

If the gateway provides a `Retry-After` header, your client should wait that long before retrying.

Our official libraries already help with this:

- [`Sonoran.js`](https://github.com/Sonoran-Software/Sonoran.js) automatically retries v2 CAD requests on `429` responses up to 2 times.
- [`Sonoran.lua`](https://github.com/Sonoran-Software/Sonoran.Lua) automatically retries v2 CAD requests on `429` responses up to 2 times.

These retries are intentionally limited. High-frequency integrations should still avoid bursty request patterns and should respect the published per-endpoint limits.
