---
description: Retrieve authenticated community metadata and shared codes.
---

# Get Info

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/info`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Return the authenticated community UUID, community metadata, and shared code lists.

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

local response = sonoran:getInfoV2()

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

  const response = await instance.cad.getInfoV2();
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

response = instance.cad.getInfoV2()

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

var response = await sonoran.getInfoV2();

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/info" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/info", {
  method: "GET",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
  },
});

const data = await response.json();
console.log(data);
```
{% endtab %}

{% tab title="PowerShell" %}
```powershell
$headers = @{
  Authorization = "Bearer YOUR_API_KEY"
  Accept = "application/json"
}

Invoke-RestMethod `
  -Method Get `
  -Uri "https://api.sonorancad.com/v2/general/info" `
  -Headers $headers
```
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Get Info"
  version: "1.0.0"
  description: "Retrieve authenticated community metadata and shared codes."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/info:
    get:
      summary: "Get Info"
      operationId: "getInfo"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                uuid: "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"
                community:
                  comId: "examplecad"
                  name: "Example CAD"
                  timezone: "America/Phoenix"
                  customLoginUrl: "https://portal.examplecad.com/login"
                codes:
                  - "10-8"
                  - "10-23"
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
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "uuid": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "community": {
    "comId": "examplecad",
    "name": "Example CAD",
    "timezone": "America/Phoenix",
    "customLoginUrl": "https://portal.examplecad.com/login"
  },
  "codes": [
    "10-8",
    "10-23"
  ]
}
```
