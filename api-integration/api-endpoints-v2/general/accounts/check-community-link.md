---
description: Check whether a community user ID is linked to an account.
---

# Check Community Link

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/links/check`

> **Rate limit:** `30 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Resolve a `communityUserId` to the linked Sonoran CAD account UUID inside the authenticated community.

## Request Body

```json
{
  "communityUserId": "player_12345"
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

local response = sonoran.cad:checkCommunityLinkV2({
    communityUserId = 'player_12345',
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:checkCommunityLinkV2({
    communityUserId = 'player_12345',
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

  const response = await instance.cad.checkCommunityLinkV2({
    communityUserId: 'player_12345',
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

response = instance.cad.checkCommunityLinkV2({
    "communityUserId": 'player_12345',
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

var response = await sonoran.Cad.checkCommunityLinkV2(new CommunityLinkV2Request
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
  title: "Sonoran CAD v2 - Check Community Link"
  version: "1.0.0"
  description: "Check whether a community user ID is linked to an account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/links/check:
    post:
      summary: "Check Community Link"
      operationId: "checkCommunityLink"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                communityUserId: "player_12345"
                linked: true
                accountUuid: "00000000-0000-0000-0000-000000000000"
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
              communityUserId: "player_12345"
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
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/links/check" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player_12345"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

Linked:

```json
{
  "communityUserId": "player_12345",
  "linked": true,
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
```

Not linked:

```json
{
  "communityUserId": "player_12345",
  "linked": false,
  "accountUuid": null
}
```

If you want to avoid polling after creating a link code, listen for the [Community Link Verified](../../../push-events/civilian/community-link-verified.md) push event instead.
