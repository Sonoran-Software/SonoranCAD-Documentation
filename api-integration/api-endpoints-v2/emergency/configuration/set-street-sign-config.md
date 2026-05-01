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
  product = Sonoran.productEnums.CAD,
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran.cad:setStreetSignConfigV2({
    // See the request body above for the full street sign shape.
    { id = 1, coordinates = { x = 0, y = 0, z = 0, w = 0 }, label = 'Alta St' },
  }, 1)

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
local response = cad:setStreetSignConfigV2({
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

response = instance.cad.setStreetSignConfigV2([
    # See the request body above for the full street sign shape.
    { "id": 1, "coordinates": { "x": 0, "y": 0, "z": 0, "w": 0 }, "label": 'Alta St' },
  ], 1)

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

var response = await sonoran.Cad.setStreetSignConfigV2(
    new[]
    {
        new Dictionary<string, object?>
        {
            ["id"] = 1,
            ["coordinates"] = new Dictionary<string, object?>
            {
                ["x"] = 0,
                ["y"] = 0,
                ["z"] = 0,
                ["w"] = 0
            },
            ["label"] = "Alta St"
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
  title: "Sonoran CAD v2 - Set Street Sign Config"
  version: "1.0.0"
  description: "Replace street sign configuration for a server."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/street-sign-config:
    put:
      summary: "Set Street Sign Config"
      operationId: "setStreetSignConfig"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                serverId: 1
                signs: 1
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
              signs:
                id: 7
                coordinates:
                  x: 420.1
                  y: -980.4
                  z: 30.8
                  w: 0.0
                label: "Mission Row"
                text1: "Mission Row"
                text2: "Integrity Way"
                text3: ""
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
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1,
  "signs": 1
}
```

