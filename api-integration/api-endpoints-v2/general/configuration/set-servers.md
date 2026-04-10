---
description: Replace configured community servers.
---

# Set Servers

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/servers`

Replace the configured server list for the authenticated community.

## Request Body

Each `servers[]` item can include `id`, `name`, `description`, `signal`, `mapUrl`, `mapIp`, `listenerPort`, `differingOutbound`, `outboundIp`, `enableMap`, `mapType`, `isStatic`, and `liveMapFormat`.

```json
{
  "deployMap": true,
  "servers": [
    {
      "id": 1,
      "name": "Main Server",
      "description": "Primary patrol server",
      "signal": "100",
      "mapUrl": "https://example.com/tiles/{z}/{x}/{y}.png",
      "mapIp": "203.0.113.10",
      "listenerPort": "30120",
      "differingOutbound": false,
      "outboundIp": "",
      "enableMap": true,
      "mapType": "NORMAL",
      "isStatic": false,
      "liveMapFormat": 0
    }
  ]
}
```

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

local response = sonoran:setServersV2({
    // See the request body above for the full server config shape.
    { id = 1, name = 'Main Server' },
  }, true)

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

  const response = await instance.cad.setServersV2([
    // See the request body above for the full server config shape.
    { id: 1, name: 'Main Server' },
  ], true);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/general/servers" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "deployMap": true,
  "servers": [
    {
      "id": 1,
      "name": "Main Server",
      "description": "Primary patrol server",
      "signal": "100",
      "mapUrl": "https://example.com/tiles/{z}/{x}/{y}.png",
      "mapIp": "203.0.113.10",
      "listenerPort": "30120",
      "differingOutbound": false,
      "outboundIp": "",
      "enableMap": true,
      "mapType": "NORMAL",
      "isStatic": false,
      "liveMapFormat": 0
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/servers", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "deployMap": true,
  "servers": [
    {
      "id": 1,
      "name": "Main Server",
      "description": "Primary patrol server",
      "signal": "100",
      "mapUrl": "https://example.com/tiles/{z}/{x}/{y}.png",
      "mapIp": "203.0.113.10",
      "listenerPort": "30120",
      "differingOutbound": false,
      "outboundIp": "",
      "enableMap": true,
      "mapType": "NORMAL",
      "isStatic": false,
      "liveMapFormat": 0
    }
  ]
}),
});

const data = await response.json();
console.log(data);
```
{% endtab %}

{% tab title="PowerShell" %}
```powershell
$headers = @{
  Authorization = "Bearer YOUR_API_KEY"
  Accept = "application/json"
  "Content-Type" = "application/json"
}

$body = @'
{
  "deployMap": true,
  "servers": [
    {
      "id": 1,
      "name": "Main Server",
      "description": "Primary patrol server",
      "signal": "100",
      "mapUrl": "https://example.com/tiles/{z}/{x}/{y}.png",
      "mapIp": "203.0.113.10",
      "listenerPort": "30120",
      "differingOutbound": false,
      "outboundIp": "",
      "enableMap": true,
      "mapType": "NORMAL",
      "isStatic": false,
      "liveMapFormat": 0
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/general/servers" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "servers": [
    {
      "id": 1,
      "name": "Main Server",
      "description": "Primary patrol server",
      "signal": "100",
      "mapUrl": "https://example.com/tiles/{z}/{x}/{y}.png",
      "mapIp": "203.0.113.10",
      "listenerPort": "30120",
      "differingOutbound": false,
      "outboundIp": "",
      "enableMap": true,
      "mapType": "NORMAL",
      "isStatic": false,
      "liveMapFormat": 0
    }
  ]
}
```

## Enumeration Values

### LIVE_MAP_FORMAT

| Value | Description |
| --- | --- |
| `0` | `GTA_V` |
| `1` | `ROBLOX` |
