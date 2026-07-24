---
description: Generate temporary TURN credentials for WebRTC clients using the authenticated community API key.
---

# Get Turn Credentials

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/turn`

> **Rate limit:** `20 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Generate temporary TURN credentials for Sonoran CAD WebRTC clients. This route uses normal v2 API authentication and does not require a paid plan.

## Query Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| `userId` | string | No | Optional user identifier appended to the generated TURN username. Colons are normalized to underscores. |

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

local response = sonoran.cad:getTurnCredentialsV2({
  userId = "unit-1"
})

print(response.success)
print(response.data and response.data.ttl)
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

  const response = await instance.cad.getTurnCredentialsV2({
    userId: 'unit-1',
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

response = instance.cad.getTurnCredentialsV2({
    "userId": "unit-1",
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

var response = await sonoran.Cad.getTurnCredentialsV2(new GetTurnCredentialsV2Query
{
    UserId = "unit-1"
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
  title: "Sonoran CAD v2 - Get Turn Credentials"
  version: "1.0.0"
  description: "Generate temporary TURN credentials for WebRTC clients using the authenticated community API key."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/turn:
    get:
      summary: "Get Turn Credentials"
      operationId: "getTurnCredentials"
      parameters:
        -
          in: "query"
          name: "userId"
          required: false
          schema:
            type: "string"
          description: "Optional user identifier appended to the generated TURN username."
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                iceServers:
                  - urls:
                      - "turn:coturn.sonorancad.com:3478?transport=udp"
                      - "turn:coturn.sonorancad.com:3478?transport=tcp"
                      - "stun:coturn.sonorancad.com:3478"
                    username: "1735689600:unit-1"
                    credential: "base64-turn-credential"
                ttl: 600
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
  --url "https://api.sonorancad.com/v2/general/turn?userId=unit-1" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "iceServers": [
    {
      "urls": [
        "turn:coturn.sonorancad.com:3478?transport=udp",
        "turn:coturn.sonorancad.com:3478?transport=tcp",
        "stun:coturn.sonorancad.com:3478"
      ],
      "username": "1735689600:unit-1",
      "credential": "base64-turn-credential"
    }
  ],
  "ttl": 600
}
```
