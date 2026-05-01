---
description: Send a photo URL to active connections for a community user ID.
---

# Send Photo

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/photos`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Send a photo URL to every active connection linked to a community user ID.

## Request Body

Use `communityUserId` to target the account that should receive the photo.

```json
{
  "communityUserId": "player-1234",
  "url": "https://cdn.example.com/mugshots/example.png"
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

local response = sonoran.cad:sendPhotoV2({
    communityUserId = 'player-1234',
    url = 'https =//example.com/mugshot.png',
  })

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
local response = cad:sendPhotoV2({
    apiId = '1234567890',
    url = 'https =//example.com/mugshot.png',
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

  const response = await instance.cad.sendPhotoV2({
    communityUserId: 'player-1234',
    url: 'https://example.com/mugshot.png',
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

response = instance.cad.sendPhotoV2({
    "communityUserId": 'player-1234',
    "url": 'https://example.com/mugshot.png',
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

var response = await sonoran.Cad.sendPhotoV2(new SendPhotoV2Request
{
    CommunityUserId = "player-1234",
    Url = "https://example.com/mugshot.jpg"
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
  title: "Sonoran CAD v2 - Send Photo"
  version: "1.0.0"
  description: "Send a photo URL to active connections for a community user ID."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/photos:
    post:
      summary: "Send Photo"
      operationId: "sendPhoto"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                communityUserId: "player-1234"
                delivered: 1
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
              url: "https://cdn.example.com/mugshots/example.png"
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
  --url "https://api.sonorancad.com/v2/general/photos" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "url": "https://cdn.example.com/mugshots/example.png"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "communityUserId": "player-1234",
  "delivered": 1
}
```
