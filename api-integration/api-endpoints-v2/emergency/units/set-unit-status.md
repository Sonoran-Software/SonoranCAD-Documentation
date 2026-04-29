---
description: Set status for one or more identifiers.
---

# Set Unit Status

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/status`

> **Rate limit:** `30 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Set a new unit status for one or more identifiers resolved by `communityUserId`, `communityUserIds`, `roblox`, `accountUuid`, or `identIds`.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

Use `communityUserId` or `communityUserIds` by default, or provide `roblox`, `accountUuid`, or `identIds`.

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| `communityUserId` | string | No | Updates all active identifiers for one linked community user. |
| `communityUserIds` | array of strings | No | Updates all active identifiers for multiple linked community users. |
| `roblox` | integer | No | Updates all active identifiers for the account linked to the Roblox user ID. |
| `accountUuid` | string (uuid) | No | Updates all active identifiers for the target account. |
| `identIds` | array of integers | No | Directly target one or more identifier IDs. |
| `status` | integer | Yes | Unit status enum. See `UNIT_STATUS` below. |

```json
{
  "communityUserIds": ["player-1234"],
  "status": 3
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

local response = sonoran.cad:setUnitStatusV2({
    serverId = 1,
    communityUserId = 'player-1234',
    status = 2,
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

  const response = await instance.cad.setUnitStatusV2({
    serverId: 1,
    communityUserId: 'player-1234',
    status: 2,
  });
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

response = instance.cad.setUnitStatusV2({
    "serverId": 1,
    "communityUserId": 'player-1234',
    "status": 2,
  })

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

var response = await sonoran.Cad.setUnitStatusV2(new SetUnitStatusV2Request
{
    ServerId = 1,
    CommunityUserId = "player-1234",
    Status = 3
});

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Set Unit Status"
  version: "1.0.0"
  description: "Set status for one or more identifiers."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/units/status:
    patch:
      summary: "Set Unit Status"
      operationId: "setUnitStatus"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                updated: 1
                status: "ENROUTE"
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
              communityUserIds: "player-1234"
              status: 3
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
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units/status" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserIds": ["player-1234"],
  "status": 3
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "updated": 1,
  "status": "ENROUTE"
}
```

## Enumeration Values

### UNIT_STATUS

| Value | Description |
| --- | --- |
| `0` | `UNAVAILABLE` |
| `1` | `BUSY` |
| `2` | `AVAILABLE` |
| `3` | `ENROUTE` |
| `4` | `ON_SCENE` |
| `100` | `OFFLINE` |
