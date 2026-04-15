---
description: Replace or append API IDs for a community account.
---

# Set API IDs

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/api-ids`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Set or append API IDs for a community account.

## Request Body

Provide exactly one of `communityUserId`, `username`, or `accountUuid`.

```json
{
  "communityUserId": "player-1234",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
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

local response = sonoran.cad:setApiIdsV2({
    accountUuid = '00000000-0000-0000-0000-000000000000',
    apiIds = {'1234567890', '0987654321'},
    pushNew = true,
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

  const response = await instance.cad.setApiIdsV2({
    accountUuid: '00000000-0000-0000-0000-000000000000',
    apiIds: ['1234567890', '0987654321'],
    pushNew: true,
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

response = instance.cad.setApiIdsV2({
    "accountUuid": '00000000-0000-0000-0000-000000000000',
    "apiIds": ['1234567890', '0987654321'],
    "pushNew": True,
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

var response = await sonoran.Cad.setApiIdsV2(new SetApiIdsV2Request
{
    AccountUuid = "00000000-0000-0000-0000-000000000000",
    ApiIds = new[] { "1234567890", "0987654321" },
    PushNew = true
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
  title: "Sonoran CAD v2 - Set API IDs"
  version: "1.0.0"
  description: "Replace or append API IDs for a community account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/api-ids:
    put:
      summary: "Set API IDs"
      operationId: "setAPIIDs"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                accountUuid: "00000000-0000-0000-0000-000000000000"
                apiIds: "steam:110000112345678"
                pushNew: true
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
              apiIds:
                - "steam:110000112345678"
                - "license:abc123"
              pushNew: true
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
  --url "https://api.sonorancad.com/v2/general/api-ids" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "apiIds": [
    "steam:110000112345678"
  ],
  "pushNew": true
}
```
