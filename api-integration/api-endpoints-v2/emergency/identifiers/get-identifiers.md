---
description: Retrieve identifiers for an account.
---

# Get Identifiers

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Retrieve the selected identifier and all identifiers for an account.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |

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

local response = sonoran:getIdentifiersV2('00000000-0000-0000-0000-000000000000')

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

  const response = await instance.cad.getIdentifiersV2('00000000-0000-0000-0000-000000000000');
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

response = instance.cad.getIdentifiersV2('00000000-0000-0000-0000-000000000000')

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

var response = await sonoran.getIdentifiersV2("00000000-0000-0000-0000-000000000000");

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers", {
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
  -Uri "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers" `
  -Headers $headers
```
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Get Identifiers"
  version: "1.0.0"
  description: "Retrieve identifiers for an account."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/accounts/{accountUuid}/identifiers:
    get:
      summary: "Get Identifiers"
      operationId: "getIdentifiers"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                selectedIdent: 12
                identifiers:
                  id: 12
                  accId: "00000000-0000-0000-0000-000000000000"
                  status: 3
                  isPanic: false
                  location: "Mission Row PD"
                  coordinates:
                    x: 123.45
                    y: -456.78
                    z: 32.1
                    w: 180.0
                  aop: "Los Santos"
                  data:
                    unitNum: "A-10"
                    name: "John Doe"
                    district: "Los Santos"
                    department: "LSPD"
                    subdivision: "Patrol"
                    rank: "Officer"
                    group: "CAR-51"
                    page: 0
                    apiIds: "steam:110000112345678"
                  isDispatch: false
      parameters:
        -
          description: "Sonoran CAD account UUID."
          name: "accountUuid"
          in: "path"
          schema:
            type: "string"
          required: true
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
  "selectedIdent": 12,
  "identifiers": [
    {
      "id": 12,
      "accId": "00000000-0000-0000-0000-000000000000",
      "status": 3,
      "isPanic": false,
      "location": "Mission Row PD",
      "coordinates": {
        "x": 123.45,
        "y": -456.78,
        "z": 32.1,
        "w": 180.0
      },
      "aop": "Los Santos",
      "data": {
        "unitNum": "A-10",
        "name": "John Doe",
        "district": "Los Santos",
        "department": "LSPD",
        "subdivision": "Patrol",
        "rank": "Officer",
        "group": "CAR-51",
        "page": 0,
        "apiIds": [
          "steam:110000112345678"
        ]
      },
      "isDispatch": false
    }
  ]
}
```

## Enumeration Values

### UNIT_STATUS

| Value | Description |
| --- | --- |
| `0` | `UNAVAILABLE` |
| `1` | `BUSY` |
| `2` | `AVAILABLE` |
| `3` | `ENROUTE` |
| `4` | `ON_SCENE` |
| `100` | `OFFLINE` |

### UNIT_PAGE

| Value | Description |
| --- | --- |
| `0` | `POLICE` |
| `1` | `FIRE` |
| `2` | `EMS` |
| `3` | `DISPATCH` |
| `-1` | `UNKNOWN` |
