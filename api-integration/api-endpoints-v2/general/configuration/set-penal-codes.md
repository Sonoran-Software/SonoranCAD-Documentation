---
description: Replace the community penal code configuration.
---

# Set Penal Codes

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/penal-codes`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Replace the community penal code configuration.

## Request Body

```json
{
  "codes": []
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

local response = sonoran.cad:setPenalCodesV2({
    // See the request body above for the full penal code shape.
    { code = '22107', title = 'Unsafe Lane Change', definition = 'Unsafe lane change' },
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:setPenalCodesV2({
    // See the request body above for the full penal code shape.
    { code = '22107', title = 'Unsafe Lane Change', definition = 'Unsafe lane change' },
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

  const response = await instance.cad.setPenalCodesV2([
    // See the request body above for the full penal code shape.
    { code: '22107', title: 'Unsafe Lane Change', definition: 'Unsafe lane change' },
  ]);
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

response = instance.cad.setPenalCodesV2([
    # See the request body above for the full penal code shape.
    { "code": '22107', "title": 'Unsafe Lane Change', "definition": 'Unsafe lane change' },
  ])

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

var response = await sonoran.Cad.setPenalCodesV2(new[]
{
    new PenalCodeV2
    {
        Code = "22107",
        Type = "INFRACTION",
        Title = "Unsafe Lane Change"
    }
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
  title: "Sonoran CAD v2 - Set Penal Codes"
  version: "1.0.0"
  description: "Replace the community penal code configuration."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/penal-codes:
    put:
      summary: "Set Penal Codes"
      operationId: "setPenalCodes"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                updated: 1
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
              codes: null
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
  --url "https://api.sonorancad.com/v2/general/penal-codes" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "codes": []
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "updated": 1
}
```

