---
description: Retrieve characters for a community user, linked Roblox user, or account.
---

# Get Characters

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/civilian/characters`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Retrieve characters for a Sonoran CAD account using `communityUserId` by default, or `roblox` or `accountUuid` as alternatives.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `communityUserId` | string | Optional | Default target option for the in-game community user ID. Provide exactly one identifier. |
| `roblox` | integer | Optional | Target the account linked to a Roblox user ID. Provide exactly one identifier. |
| `accountUuid` | string (uuid) | Optional | Target account UUID. Provide exactly one identifier. |

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

local response = sonoran.cad:getCharactersV2({
    accountUuid = '00000000-0000-0000-0000-000000000000',
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:getCharactersV2({
    accountUuid = '00000000-0000-0000-0000-000000000000',
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

  const response = await instance.cad.getCharactersV2({
    accountUuid: '00000000-0000-0000-0000-000000000000',
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

response = instance.cad.getCharactersV2({
    "accountUuid": '00000000-0000-0000-0000-000000000000',
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

var response = await sonoran.Cad.getCharactersV2(new GetCharactersV2Query
{
    CommunityUserId = "player-1234"
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
  title: "Sonoran CAD v2 - Get Characters"
  version: "1.0.0"
  description: "Retrieve characters for a community user, linked Roblox user, or account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/civilian/characters:
    get:
      summary: "Get Characters"
      operationId: "getCharacters"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                recordTypeId: 7
                id: 2451
                syncId: "citizen:1234"
                name: "John Doe"
                type: 7
                sections:
                  category: 0
                  label: "Civilian Info"
                  fields:
                    label: "First Name"
                    value: "John"
                    uid: "first_name"
      parameters:
        -
          description: "Default target option for the in-game community user ID. Provide exactly one identifier."
          name: "communityUserId"
          in: "query"
          schema:
            type: "string"
          required: false
        -
          description: "Target the account linked to a Roblox user ID. Provide exactly one identifier."
          name: "roblox"
          in: "query"
          schema:
            type: "integer"
          required: false
        -
          description: "Target account UUID. Provide exactly one identifier."
          name: "accountUuid"
          in: "query"
          schema:
            type: "string"
          required: false
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
  --url "https://api.sonorancad.com/v2/civilian/characters?communityUserId=player-1234" \
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
    "recordTypeId": 7,
    "id": 2451,
    "syncId": "citizen:1234",
    "name": "John Doe",
    "type": 7,
    "sections": [
      {
        "category": 0,
        "label": "Civilian Info",
        "fields": [
          {
            "label": "First Name",
            "value": "John",
            "uid": "first_name"
          }
        ]
      }
    ]
  }
]
```
