---
description: Replace station alert configuration for a server.
---

# Set Stations

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/stations`

> **Rate limit:** `2 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Replace the station alert configuration for a server.

For parity with the v1 `SET_STATIONS` endpoint, the canonical config shape uses arrays for `locations`, `tones`, and `unitColors`. The backend also accepts a single object/string for these fields for compatibility, but array values are the recommended format.

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
  product = Sonoran.productEnums.CAD,
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran.cad:setStationsV2({
    // See the request body above for the full station config shape.
    locations = {},
    tones = {},
    unitColors = {},
  }, 1)

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:setStationsV2({
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
{% tab title="Sonoran.py" %}
~~~python
# pip install Sonoran.py
from sonoran import Instance, productEnums

instance = Instance(
    apiKey="YOUR_API_KEY",
    communityId="YOUR_COMMUNITY_ID",
    product=productEnums.CAD,
    serverId=1,
)

response = instance.cad.setStationsV2({
    # See the request body above for the full station config shape.
    locations: [],
    "tones": [],
    "unitColors": [],
  }, 1)

print(response.success)
print(response.data if response.success else response.reason)
~~~
{% endtab %}
{% tab title="Sonoran.Net" %}
~~~csharp
// dotnet add package Sonoran.Net
using Sonoran;

using var sonoran = new SonoranClient(new SonoranClientOptions
{
    product = SonoranProduct.CAD,
    communityId = "YOUR_COMMUNITY_ID",
    apiKey = "YOUR_API_KEY",
    defaultServerId = 1
});

var response = await sonoran.Cad.setStationsV2(
    new StationConfigV2
    {
        Enabled = true,
        Stations = new[]
        {
            new StationV2
            {
                Label = "Mission Row",
                Department = "Police",
                Subdivision = "Patrol",
                IdentIds = new[] { 12, 18 }
            }
        }
    },
    1
);

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Set Stations"
  version: "1.0.0"
  description: "Replace station alert configuration for a server."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/stations:
    put:
      summary: "Set Stations"
      operationId: "setStations"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                serverId: 1
      parameters:
        -
          description: "Configured Sonoran CAD server ID."
          name: "serverId"
          in: "path"
          schema:
            type: "integer"
          example: 1
          required: true
      security:
        -
          bearerAuth:
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: "object"
            example:
              config:
                locations:
                  - name: "Mission Row"
                    coordinates:
                      x: 425.1
                      y: -979.2
                      z: 30.7
                      w: 0.0
                    doors:
                      - "bay_1"
                      - "bay_2"
                    icon: "fas fa-building"
                tones:
                  - "tone_station_open.mp3"
                unitColors:
                  - "#2563eb"
                  - "#ef4444"
components:
  securitySchemes:
    bearerAuth:
      type: "http"
      scheme: "bearer"
      bearerFormat: "JWT"
~~~
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
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1
}
```

