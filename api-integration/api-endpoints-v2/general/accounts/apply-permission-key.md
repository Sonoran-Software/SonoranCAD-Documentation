---
description: Apply a permission key to an account resolved by community user ID.
---

# Apply Permission Key

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/permission-keys/applications`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Apply a Sonoran CAD permission key to the account linked to a community user ID.

## Request Body

Provide the target account with `communityUserId`.

```json
{
  "communityUserId": "player-1234",
  "permissionKey": "YOUR_PERMISSION_KEY"
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

local response = sonoran:applyPermissionKeyV2({
    apiId = '1234567890',
    permissionKey = 'DISPATCH',
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

  const response = await instance.cad.applyPermissionKeyV2({
    apiId: '1234567890',
    permissionKey: 'DISPATCH',
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

response = instance.cad.applyPermissionKeyV2({
    "apiId": '1234567890',
    "permissionKey": 'DISPATCH',
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

var response = await sonoran.applyPermissionKeyV2(new ApplyPermissionKeyV2Request
{
    ApiId = "1234567890",
    PermissionKey = "COMMAND_STAFF"
});

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/permission-keys/applications" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "permissionKey": "YOUR_PERMISSION_KEY"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/permission-keys/applications", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "permissionKey": "YOUR_PERMISSION_KEY"
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
  "permissionKey": "YOUR_PERMISSION_KEY"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/permission-keys/applications" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Apply Permission Key"
  version: "1.0.0"
  description: "Apply a permission key to an account resolved by community user ID."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/permission-keys/applications:
    post:
      summary: "Apply Permission Key"
      operationId: "applyPermissionKey"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                accountUuid: "00000000-0000-0000-0000-000000000000"
                username: "ExampleUser"
                message: "Permission key applied."
                permissions:
                  police: true
                  dispatch: true
                  liveMap: true
                  adminInGameIntegration: true
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
              permissionKey: "YOUR_PERMISSION_KEY"
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
  "username": "ExampleUser",
  "message": "Permission key applied.",
  "permissions": {
    "police": true,
    "dispatch": true,
    "liveMap": true,
    "adminInGameIntegration": true
  }
}
```
