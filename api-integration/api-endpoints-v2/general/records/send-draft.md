---
description: Build a draft record from a template and optionally send it to an active account.
---

# Send Draft

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/record-drafts`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Build a draft record from a template and, when a target account is provided, send it to the user over the active websocket session.

## Request Body

You can optionally route the draft to a connected user with `communityUserId` by default, or with `roblox` or `accountUuid`.

```json
{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
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
  product = Sonoran.productEnums.CAD,
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran.cad:sendRecordDraftV2({
    recordTypeId = 1,
    replaceValues = { firstName = 'John', lastName = 'Doe' },
    communityUserId = 'player-1234',
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
local response = cad:sendRecordDraftV2({
    recordTypeId = 1,
    replaceValues = { firstName = 'John', lastName = 'Doe' },
    apiId = '1234567890',
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

  const response = await instance.cad.sendRecordDraftV2({
    recordTypeId: 1,
    replaceValues: { firstName: 'John', lastName: 'Doe' },
    communityUserId: 'player-1234',
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

response = instance.cad.sendRecordDraftV2({
    "recordTypeId": 1,
    "replaceValues": { "firstName": 'John', "lastName": 'Doe' },
    "communityUserId": 'player-1234',
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

var response = await sonoran.Cad.sendRecordDraftV2(new SendRecordDraftV2Request
{
    RecordTypeId = 12,
    ReplaceValues = new Dictionary<string, string>
    {
        ["case_number"] = "SC-2026-001"
    },
    AccountUuid = "00000000-0000-0000-0000-000000000000"
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
  title: "Sonoran CAD v2 - Send Draft"
  version: "1.0.0"
  description: "Build a draft record from a template and optionally send it to an active account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/record-drafts:
    post:
      summary: "Send Draft"
      operationId: "sendDraft"
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
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: "object"
            example:
              recordTypeId: 12
              replaceValues:
                {{plate}}: "ABC123"
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
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/record-drafts" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "communityUserId": "player-1234"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
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
```
