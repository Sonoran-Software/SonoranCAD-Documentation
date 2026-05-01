---
description: Retrieve custom blips for a server.
---

# Get Blips

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/blips`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Retrieve custom blips configured for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

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

local response = sonoran.cad:getBlipsV2(1)

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
Use the server-side `sonorancad` export to get the CAD client in your runtime.

```lua
local cad = exports["sonorancad"]:getCadClient()
```

```csharp
dynamic cad = Exports["sonorancad"].getCadClient();
```

```javascript
const cad = exports["sonorancad"].getCadClient();
```

```lua
local response = cad:getBlipsV2(1)

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

  const response = await instance.cad.getBlipsV2(1);
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

response = instance.cad.getBlipsV2(1)

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

var response = await sonoran.Cad.getBlipsV2(1);

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Get Blips"
  version: "1.0.0"
  description: "Retrieve custom blips for a server."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/blips:
    get:
      summary: "Get Blips"
      operationId: "getBlips"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "array"
                items:
                  type: "object"
              example:
                - id: 32
                  coordinates:
                    x: 425.5
                    y: -979.8
                    z: 0.0
                    w: 0.0
                  subType: "radius"
                  icon: "fa-location-dot"
                  color: "#ff0000"
                  tooltip: "Perimeter"
                  data:
                    - title: "Assigned Unit"
                      text: "A-10"
                  radius: 100.0
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
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/blips" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
  {
    "id": 32,
    "coordinates": {
      "x": 425.5,
      "y": -979.8,
      "z": 0.0,
      "w": 0.0
    },
    "subType": "radius",
    "icon": "fa-location-dot",
    "color": "#ff0000",
    "tooltip": "Perimeter",
    "data": [
      {
        "title": "Assigned Unit",
        "text": "A-10"
      }
    ],
    "radius": 100.0
  }
]
```

