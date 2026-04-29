---
description: Update account permissions and account status for a community account.
---

# Modify Account Permissions

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/accounts/permissions`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Update permissions for a community account and optionally set its active status.

## Request Body

Use `communityUserId` by default. You can also provide exactly one of `roblox`, `accountUuid`, or `username`.

```json
{
  "communityUserId": "player-1234",
  "add": ["POLICE", "DISPATCH"],
  "active": true
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

local response = sonoran.cad:setAccountPermissionsV2({
    communityUserId = 'player-1234',
    add = {'DISPATCH'},
    remove = {'CIVILIAN'},
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

  const response = await instance.cad.setAccountPermissionsV2({
    communityUserId: 'player-1234',
    add: ['DISPATCH'],
    remove: ['CIVILIAN'],
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

response = instance.cad.setAccountPermissionsV2({
    "communityUserId": 'player-1234',
    "add": ['DISPATCH'],
    "remove": ['CIVILIAN'],
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

var response = await sonoran.Cad.setAccountPermissionsV2(new SetAccountPermissionsV2Request
{
    CommunityUserId = "player-1234",
    Add = new[] { "dispatch" },
    Remove = new[] { "leo" }
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
  title: "Sonoran CAD v2 - Modify Account Permissions"
  version: "1.0.0"
  description: "Update account permissions and account status for a community user."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/accounts/permissions:
    patch:
      summary: "Modify Account Permissions"
      operationId: "modifyAccountPermissions"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                accountUuid: "00000000-0000-0000-0000-000000000000"
                permissions:
                  police: true
                  dispatch: true
                  liveMap: true
                  adminInGameIntegration: true
                active: true
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
              communityUserId: "player-1234"
              roblox: 123456789
              add:
                - "POLICE"
                - "DISPATCH"
              active: true
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
  --url "https://api.sonorancad.com/v2/general/accounts/permissions" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "permissions": {
    "police": true,
    "dispatch": true,
    "liveMap": true,
    "adminInGameIntegration": true
  },
  "active": true
}
```
