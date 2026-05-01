---
description: Replace available ERS callouts for a server.
---

# Set Callouts

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/callouts`

> **Rate limit:** `2 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Replace the ERS callout configuration for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "callouts": [
    {
      "id": "armed_suspect",
      "data": {
        "PedActionOnNoActionFound": "Flee",
        "PedActionMinimumTimeoutInMs": 2000,
        "PedChanceToFleeFromPlayer": 50,
        "PedChanceToObtainWeapons": 30,
        "CalloutName": "Armed Suspect",
        "CalloutDescriptions": ["Reports of an armed suspect in the area."],
        "PedChanceToAttackPlayer": 20,
        "PedActionMaximumTimeoutInMs": 10000,
        "Enabled": true,
        "CalloutLocations": [],
        "PedChanceToSurrender": 30,
        "PedWeaponData": ["WEAPON_PISTOL"],
        "CalloutUnitsRequired": {
          "towRequired": false,
          "fireRequired": false,
          "description": "Single suspect, use caution.",
          "policeRequired": true,
          "ambulanceRequired": false
        }
      }
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

local response = sonoran.cad:setAvailableCalloutsV2({
    // See the request body above for the full callout shape.
    { id = 'armed_suspect', data = {} },
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
local response = cad:setAvailableCalloutsV2({
    // See the request body above for the full callout shape.
    { id = 'armed_suspect', data = {} },
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

  const response = await instance.cad.setAvailableCalloutsV2([
    // See the request body above for the full callout shape.
    { id: 'armed_suspect', data: {} },
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

response = instance.cad.setAvailableCalloutsV2([
    # See the request body above for the full callout shape.
    { "id": 'armed_suspect', "data": {} },
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

var response = await sonoran.Cad.setAvailableCalloutsV2(
    new[]
    {
        new AvailableCalloutV2
        {
            Code = "10-70",
            Label = "Structure Fire",
            Priority = 1
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
  title: "Sonoran CAD v2 - Set Callouts"
  version: "1.0.0"
  description: "Replace available ERS callouts for a server."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/callouts:
    put:
      summary: "Set Callouts"
      operationId: "setCallouts"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                serverId: 1
                callouts: 1
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
              callouts:
                - id: "armed_suspect"
                  data:
                    PedActionOnNoActionFound: "Flee"
                    PedActionMinimumTimeoutInMs: 2000
                    PedChanceToFleeFromPlayer: 50
                    PedChanceToObtainWeapons: 30
                    CalloutName: "Armed Suspect"
                    CalloutDescriptions:
                      - "Reports of an armed suspect in the area."
                    PedChanceToAttackPlayer: 20
                    PedActionMaximumTimeoutInMs: 10000
                    Enabled: true
                    CalloutLocations: []
                    PedChanceToSurrender: 30
                    PedWeaponData:
                      - "WEAPON_PISTOL"
                    CalloutUnitsRequired:
                      towRequired: false
                      fireRequired: false
                      description: "Single suspect, use caution."
                      policeRequired: true
                      ambulanceRequired: false
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
  --url "https://api.sonorancad.com/v2/emergency/servers/1/callouts" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "callouts": [
    {
      "id": "armed_suspect",
      "data": {
        "PedActionOnNoActionFound": "Flee",
        "PedActionMinimumTimeoutInMs": 2000,
        "PedChanceToFleeFromPlayer": 50,
        "PedChanceToObtainWeapons": 30,
        "CalloutName": "Armed Suspect",
        "CalloutDescriptions": ["Reports of an armed suspect in the area."],
        "PedChanceToAttackPlayer": 20,
        "PedActionMaximumTimeoutInMs": 10000,
        "Enabled": true,
        "CalloutLocations": [],
        "PedChanceToSurrender": 30,
        "PedWeaponData": ["WEAPON_PISTOL"],
        "CalloutUnitsRequired": {
          "towRequired": false,
          "fireRequired": false,
          "description": "Single suspect, use caution.",
          "policeRequired": true,
          "ambulanceRequired": false
        }
      }
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
  "callouts": 1
}
```

