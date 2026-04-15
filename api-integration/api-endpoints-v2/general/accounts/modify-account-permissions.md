---
description: Update account permissions and account status for a community user.
---

# Modify Account Permissions

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/accounts/permissions`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Update permissions for a community account and optionally set its active status.

## Request Body

Provide exactly one account identifier using `communityUserId`, `accountUuid`, or `username`.

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
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran:setAccountPermissionsV2({
    accountUuid = '00000000-0000-0000-0000-000000000000',
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
    accountUuid: '00000000-0000-0000-0000-000000000000',
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
    "accountUuid": '00000000-0000-0000-0000-000000000000',
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
    communityId = "YOUR_COMMUNITY_ID",
    apiKey = "YOUR_API_KEY",
    defaultServerId = 1
});

var response = await sonoran.setAccountPermissionsV2(new SetAccountPermissionsV2Request
{
    AccountUuid = "00000000-0000-0000-0000-000000000000",
    Add = new[] { "dispatch" },
    Remove = new[] { "leo" }
});

Console.WriteLine(response.success);
Console.WriteLine(response.data);
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

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/accounts/permissions", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "add": [
    "POLICE",
    "DISPATCH"
  ],
  "active": true
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
  "communityUserId": "player-1234",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/general/accounts/permissions" `
  -Headers $headers `
  -Body $body
```
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
