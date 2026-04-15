---
description: Retrieve paginated community accounts.
---

# Get Accounts

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/accounts`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Return paginated community accounts.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `limit` | integer | `100` | Maximum number of accounts returned. The backend enforces 1-100. |
| `offset` | integer | `0` | Number of accounts to skip. |
| `status` | integer | `1` | Filter by account status. See `ACCOUNT_STATUS` below. |
| `username` | string | Optional | Case-insensitive username filter. |

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

local response = sonoran:getAccountsV2({
    limit = 25,
    offset = 0,
    username = 'john',
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

  const response = await instance.cad.getAccountsV2({
    limit: 25,
    offset: 0,
    username: 'john',
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

response = instance.cad.getAccountsV2({
    "limit": 25,
    "offset": 0,
    "username": 'john',
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

var response = await sonoran.getAccountsV2(new GetAccountsV2Query
{
    Limit = 25,
    Offset = 0,
    Status = "ACTIVE"
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
  title: "Sonoran CAD v2 - Get Accounts"
  version: "1.0.0"
  description: "Retrieve paginated community accounts."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/accounts:
    get:
      summary: "Get Accounts"
      operationId: "getAccounts"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                pagination:
                  limit: 25
                  offset: 0
                  total: 1
                accounts:
                  uuid: "00000000-0000-0000-0000-000000000000"
                  username: "ExampleUser"
                  status: 1
                  joined: "2026-01-14T18:22:00Z"
                  lastLogin: "2026-04-08T20:55:00Z"
                  permissions:
                    police: true
                    dispatch: true
                    liveMap: true
                    adminInGameIntegration: true
                  apiIds: "steam:110000112345678"
      parameters:
        -
          description: "Maximum number of accounts returned. The backend enforces 1-100."
          name: "limit"
          in: "query"
          schema:
            type: "integer"
          required: true
        -
          description: "Number of accounts to skip."
          name: "offset"
          in: "query"
          schema:
            type: "integer"
          required: true
        -
          description: "Filter by account status. See `ACCOUNT_STATUS` below."
          name: "status"
          in: "query"
          schema:
            type: "integer"
          required: true
        -
          description: "Case-insensitive username filter."
          name: "username"
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
  --url "https://api.sonorancad.com/v2/general/accounts?limit=25&offset=0&status=1" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "pagination": {
    "limit": 25,
    "offset": 0,
    "total": 1
  },
  "accounts": [
    {
      "uuid": "00000000-0000-0000-0000-000000000000",
      "username": "ExampleUser",
      "status": 1,
      "joined": "2026-01-14T18:22:00Z",
      "lastLogin": "2026-04-08T20:55:00Z",
      "permissions": {
        "police": true,
        "dispatch": true,
        "liveMap": true,
        "adminInGameIntegration": true
      },
      "apiIds": [
        "steam:110000112345678"
      ]
    }
  ]
}
```

## Enumeration Values

### ACCOUNT_STATUS

| Value | Description |
| --- | --- |
| `0` | `PENDING` |
| `1` | `VALIDATED` |
| `2` | `EXPIRED` |
| `3` | `REMOVED` |
| `4` | `BANNED` |