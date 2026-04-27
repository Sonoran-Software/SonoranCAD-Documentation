---
description: Replace configured community servers.
---

# Set Servers

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/servers`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

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
  product = Sonoran.productEnums.CAD,
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran.cad:setServersV2({
    // See the request body above for the full server config shape.
    { id = 1, name = 'Main Server' },
  }, true)

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:setServersV2({
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

response = instance.cad.setServersV2([
    # See the request body above for the full server config shape.
    { "id": 1, "name": 'Main Server' },
  ], True)

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

var response = await sonoran.Cad.setServersV2(
    new[]
    {
        new CadServerV2
        {
            Id = 1,
            Config = new Dictionary<string, object?>
            {
                ["name"] = "Main Server",
                ["enableMap"] = true
            }
        }
    },
    true
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
  title: "Sonoran CAD v2 - Set Servers"
  version: "1.0.0"
  description: "Replace configured community servers."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/servers:
    put:
      summary: "Set Servers"
      operationId: "setServers"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                servers:
                  id: 1
                  name: "Main Server"
                  description: "Primary patrol server"
                  signal: "100"
                  mapUrl: "https://example.com/tiles/{z}/{x}/{y}.png"
                  mapIp: "203.0.113.10"
                  listenerPort: "30120"
                  differingOutbound: false
                  outboundIp: ""
                  enableMap: true
                  mapType: "NORMAL"
                  isStatic: false
                  liveMapFormat: 0
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
              deployMap: true
              servers:
                id: 1
                name: "Main Server"
                description: "Primary patrol server"
                signal: "100"
                mapUrl: "https://example.com/tiles/{z}/{x}/{y}.png"
                mapIp: "203.0.113.10"
                listenerPort: "30120"
                differingOutbound: false
                outboundIp: ""
                enableMap: true
                mapType: "NORMAL"
                isStatic: false
                liveMapFormat: 0
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

