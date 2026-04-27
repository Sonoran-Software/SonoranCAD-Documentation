---
description: Resolve an account from a Sonoran CAD account secret.
---

# Verify Secret

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/secrets/verify`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Verify an account secret and return the matched account UUID.

## Request Body

```json
{
  "secret": "00000000-0000-0000-0000-000000000000"
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

local response = sonoran.cad:verifySecretV2('00000000-0000-0000-0000-000000000000')

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:verifySecretV2('00000000-0000-0000-0000-000000000000')

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

  const response = await instance.cad.verifySecretV2('00000000-0000-0000-0000-000000000000');
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

response = instance.cad.verifySecretV2('00000000-0000-0000-0000-000000000000')

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

var response = await sonoran.Cad.verifySecretV2("YOUR_COMMUNITY_SECRET");

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Verify Secret"
  version: "1.0.0"
  description: "Resolve an account from a Sonoran CAD account secret."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/secrets/verify:
    post:
      summary: "Verify Secret"
      operationId: "verifySecret"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                00000000-0000-0000-0000-000000000000: "11111111-2222-3333-4444-555555555555"
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
              secret: "00000000-0000-0000-0000-000000000000"
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
  --url "https://api.sonorancad.com/v2/general/secrets/verify" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "secret": "00000000-0000-0000-0000-000000000000"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "00000000-0000-0000-0000-000000000000": "11111111-2222-3333-4444-555555555555"
}
```

