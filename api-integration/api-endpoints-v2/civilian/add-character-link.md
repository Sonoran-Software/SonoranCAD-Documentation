---
description: Link a sync-character ID to a community user or account.
---

# Add Character Link

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/civilian/character-links/{syncId}`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Link a sync-character ID to a community user or account.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `syncId` | string | Database Sync character identifier. |

## Request Body

Provide exactly one of `communityUserId` or `accountUuid`.

```json
{
  "communityUserId": "player-1234"
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

local response = sonoran.cad:addCharacterLinkV2('CHAR_123', {
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

  const response = await instance.cad.addCharacterLinkV2('CHAR_123', {
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

response = instance.cad.addCharacterLinkV2('CHAR_123', {
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
    communityId = "YOUR_COMMUNITY_ID",
    apiKey = "YOUR_API_KEY",
    defaultServerId = 1
});

var response = await sonoran.Cad.addCharacterLinkV2(
    "CHAR_123",
    new CharacterLinkTargetV2Request
    {
        AccountUuid = "00000000-0000-0000-0000-000000000000"
    }
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
  title: "Sonoran CAD v2 - Add Character Link"
  version: "1.0.0"
  description: "Link a sync-character ID to a community user or account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/civilian/character-links/{syncId}:
    put:
      summary: "Add Character Link"
      operationId: "addCharacterLink"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                accountUuid: "00000000-0000-0000-0000-000000000000"
                syncId: "citizen:1234"
                action: "ADD"
      parameters:
        -
          description: "Database Sync character identifier."
          name: "syncId"
          in: "path"
          schema:
            type: "string"
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
              communityUserId: "player-1234"
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
  --url "https://api.sonorancad.com/v2/civilian/character-links/citizen:1234" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "syncId": "citizen:1234",
  "action": "ADD"
}
```
