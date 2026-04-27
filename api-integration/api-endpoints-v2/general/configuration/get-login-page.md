---
description: Retrieve public login-page community details by custom URL or community ID.
---

# Get Login Page

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/login-page`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Return public login-page details for a community. This endpoint does not require bearer authentication.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `communityId` | string | Optional | Use the community ID instead of `url`. Provide exactly one. |
| `url` | string | Optional | Use the community website or login URL instead of `communityId`. |

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

local response = sonoran.cad:getLoginPageV2({
    communityId = 'YOUR_COMMUNITY_ID',
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:getLoginPageV2({
    communityId = 'YOUR_COMMUNITY_ID',
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

  const response = await instance.cad.getLoginPageV2({
    communityId: 'YOUR_COMMUNITY_ID',
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

response = instance.cad.getLoginPageV2({
    "communityId": 'YOUR_COMMUNITY_ID',
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

var response = await sonoran.Cad.getLoginPageV2(new GetLoginPageV2Query
{
    CommunityId = "YOUR_COMMUNITY_ID"
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
  title: "Sonoran CAD v2 - Get Login Page"
  version: "1.0.0"
  description: "Retrieve public login-page community details by custom URL or community ID."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/login-page:
    get:
      summary: "Get Login Page"
      operationId: "getLoginPage"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                comId: "examplecad"
                name: "Example CAD"
                timezone: "America/Phoenix"
                customLoginUrl: "https://portal.examplecad.com/login"
      parameters:
        -
          description: "Use the community ID instead of `url`. Provide exactly one."
          name: "communityId"
          in: "query"
          schema:
            type: "string"
          required: false
        -
          description: "Use the community website or login URL instead of `communityId`."
          name: "url"
          in: "query"
          schema:
            type: "string"
          required: false
~~~
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/login-page?communityId=examplecad" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "comId": "examplecad",
  "name": "Example CAD",
  "timezone": "America/Phoenix",
  "customLoginUrl": "https://portal.examplecad.com/login"
}
```

