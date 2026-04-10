---
description: Replace station alert configuration for a server.
---

# Set Stations

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/stations`

Replace the station alert configuration for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "config": {
    "locations": [
      {
        "name": "Mission Row",
        "coordinates": {
          "x": 425.1,
          "y": -979.2,
          "z": 30.7,
          "w": 0.0
        },
        "doors": ["bay_1", "bay_2"],
        "icon": "fas fa-building"
      }
    ],
    "tones": ["tone_station_open.mp3"],
    "unitColors": ["#2563eb", "#ef4444"]
  }
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

local response = sonoran:setStationsV2({
    // See the request body above for the full station config shape.
    locations = {},
    tones = {},
    unitColors = {},
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

  const response = await instance.cad.setStationsV2({
    // See the request body above for the full station config shape.
    locations: [],
    tones: [],
    unitColors: [],
  }, 1);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/stations" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "config": {
    "locations": [
      {
        "name": "Mission Row",
        "coordinates": {
          "x": 425.1,
          "y": -979.2,
          "z": 30.7,
          "w": 0.0
        },
        "doors": ["bay_1", "bay_2"],
        "icon": "fas fa-building"
      }
    ],
    "tones": ["tone_station_open.mp3"],
    "unitColors": ["#2563eb", "#ef4444"]
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/stations", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "config": {
    "locations": [
      {
        "name": "Mission Row",
        "coordinates": {
          "x": 425.1,
          "y": -979.2,
          "z": 30.7,
          "w": 0.0
        },
        "doors": [
          "bay_1",
          "bay_2"
        ],
        "icon": "fas fa-building"
      }
    ],
    "tones": [
      "tone_station_open.mp3"
    ],
    "unitColors": [
      "#2563eb",
      "#ef4444"
    ]
  }
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
  "config": {
    "locations": [
      {
        "name": "Mission Row",
        "coordinates": {
          "x": 425.1,
          "y": -979.2,
          "z": 30.7,
          "w": 0.0
        },
        "doors": ["bay_1", "bay_2"],
        "icon": "fas fa-building"
      }
    ],
    "tones": ["tone_station_open.mp3"],
    "unitColors": ["#2563eb", "#ef4444"]
  }
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/stations" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1
}
```
