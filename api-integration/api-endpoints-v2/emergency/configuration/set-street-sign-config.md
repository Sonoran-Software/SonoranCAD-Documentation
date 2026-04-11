---
description: Replace street sign configuration for a server.
---

# Set Street Sign Config

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/street-sign-config`

> **Rate limit:** `2 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Replace the full street sign configuration for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
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

local response = sonoran:setStreetSignConfigV2({
    // See the request body above for the full street sign shape.
    { id = 1, coordinates = { x = 0, y = 0, z = 0, w = 0 }, label = 'Alta St' },
  }, 1)

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

  const response = await instance.cad.setStreetSignConfigV2([
    // See the request body above for the full street sign shape.
    { id: 1, coordinates: { x: 0, y: 0, z: 0, w: 0 }, label: 'Alta St' },
  ], 1);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
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
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1,
  "signs": 1
}
```
