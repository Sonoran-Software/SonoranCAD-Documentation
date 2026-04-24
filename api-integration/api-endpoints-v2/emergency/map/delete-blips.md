---
description: Delete one or more custom blips.
---

# Delete Blips

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/blips`

> **Rate limit:** `30 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "ids": [14, 15]
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

local response = sonoran.cad:deleteBlipsV2({32}, 1)

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

  const response = await instance.cad.deleteBlipsV2([32], 1);
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

response = instance.cad.deleteBlipsV2([32], 1)

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

var response = await sonoran.Cad.deleteBlipsV2(new[] { 32 }, 1);

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Delete Blips"
  version: "1.0.0"
  description: "Delete one or more custom blips."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/blips:
    delete:
      summary: "Delete Blips"
      operationId: "deleteBlips"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                ids:
                  - 32
                  - 33
      parameters:
        -
          description: "Configured Sonoran CAD server ID."
          name: "serverId"
          in: "path"
          schema:
            type: "integer"
          example: 1
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
              ids:
                - 14
                - 15
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
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/blips" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "ids": [14, 15]
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "ids": [
    32,
    33
  ]
}
```
