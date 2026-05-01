---
description: Retrieve all record templates for the authenticated community.
---

# Get Templates

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/templates`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Return every record template configured for the authenticated community.

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

local response = sonoran.cad:getTemplatesV2()

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
local response = cad:getTemplatesV2()

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

  const response = await instance.cad.getTemplatesV2();
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

response = instance.cad.getTemplatesV2()

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

var response = await sonoran.Cad.getTemplatesV2();

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Get Templates"
  version: "1.0.0"
  description: "Retrieve all record templates for the authenticated community."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/templates:
    get:
      summary: "Get Templates"
      operationId: "getTemplates"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                recordTypeId: 12
                id: 0
                name: "Incident Report"
                type: 9
                sections:
                  category: 0
                  label: "Report Details"
                  fields:
                    label: "Case Number"
                    value: ""
                    uid: "case_number"
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
  --url "https://api.sonorancad.com/v2/general/templates" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
  {
    "recordTypeId": 12,
    "id": 0,
    "name": "Incident Report",
    "type": 9,
    "sections": [
      {
        "category": 0,
        "label": "Report Details",
        "fields": [
          {
            "label": "Case Number",
            "value": "",
            "uid": "case_number"
          }
        ]
      }
    ]
  }
]
```

