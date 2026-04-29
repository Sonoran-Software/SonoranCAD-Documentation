---
description: Create a new custom record using a raw record payload or template replacement values.
---

# Create Record

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/records`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Create a custom record for a target account.

## Request Body

Use `communityUserId` by default, or provide exactly one of `roblox` or `accountUuid` as the target user. Then provide either a full `record` object or set `useDictionary` with `recordTypeId` and `replaceValues`.

```json
{
  "communityUserId": "player-1234",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
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

local response = sonoran.cad:createRecordV2({
    // See the request body above for the full record payload shape.
    recordTypeId = 1,
    communityUserId = 'player-1234',
    record = {},
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

  const response = await instance.cad.createRecordV2({
    // See the request body above for the full record payload shape.
    recordTypeId: 1,
    communityUserId: 'player-1234',
    record: {},
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

response = instance.cad.createRecordV2({
    # See the request body above for the full record payload shape.
    recordTypeId: 1,
    "communityUserId": 'player-1234',
    "record": {},
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

var response = await sonoran.Cad.createRecordV2(new CreateRecordV2Request
{
    AccountUuid = "00000000-0000-0000-0000-000000000000",
    RecordTypeId = 12,
    ReplaceValues = new Dictionary<string, string>
    {
        ["case_number"] = "SC-2026-001"
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
  title: "Sonoran CAD v2 - Create Record"
  version: "1.0.0"
  description: "Create a new custom record using a raw record payload or template replacement values."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/records:
    post:
      summary: "Create Record"
      operationId: "createRecord"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                recordTypeId: 12
                id: 451
                name: "Incident Report"
                type: 9
                sections:
                  category: 0
                  label: "Report Details"
                  fields:
                    label: "Case Number"
                    value: "SC-2026-001"
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
              communityUserId: "player-1234"
              roblox: 123456789
              useDictionary: true
              recordTypeId: 12
              replaceValues:
                {{plate}}: "ABC123"
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
  --url "https://api.sonorancad.com/v2/general/records" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "recordTypeId": 12,
  "id": 451,
  "name": "Incident Report",
  "type": 9,
  "sections": [
    {
      "category": 0,
      "label": "Report Details",
      "fields": [
        {
          "label": "Case Number",
          "value": "SC-2026-001",
          "uid": "case_number"
        }
      ]
    }
  ]
}
```
