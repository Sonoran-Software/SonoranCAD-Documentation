---
description: Add a note to a dispatch call.
---

# Add Call Note

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/notes`

> **Rate limit:** `60 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `callId` | integer | Dispatch or 911 call ID. |

## Request Body

```json
{
  "note": "Suspect vehicle fleeing northbound",
  "noteType": "text",
  "label": "Integration"
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

local response = sonoran.cad:addDispatchNoteV2(501, {
    serverId = 1,
    note = 'Caller updated with additional suspect info.',
    noteType = 'text',
    label = 'Dispatcher',
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()

local response = cad:addDispatchNoteV2(501, {
    serverId = 1,
    note = 'Caller updated with additional suspect info.',
    noteType = 'text',
    label = 'Dispatcher',
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

  const response = await instance.cad.addDispatchNoteV2(501, {
    serverId: 1,
    note: 'Caller updated with additional suspect info.',
    noteType: 'text',
    label: 'Dispatcher',
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

response = instance.cad.addDispatchNoteV2(501, {
    "serverId": 1,
    "note": 'Caller updated with additional suspect info.',
    "noteType": 'text',
    "label": 'Dispatcher',
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

var response = await sonoran.Cad.addDispatchNoteV2(
    501,
    new AddDispatchNoteV2Request
    {
        ServerId = 1,
        Note = "Units advised of updated suspect vehicle information.",
        NoteType = "INFO",
        Label = "Dispatch"
    }
);

Console.WriteLine(response.success);
Console.WriteLine(response.data);
~~~
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Add Call Note"
  version: "1.0.0"
  description: "Add a note to a dispatch call."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/emergency/servers/{serverId}/dispatch-calls/{callId}/notes:
    post:
      summary: "Add Call Note"
      operationId: "addCallNote"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "object"
              example:
                callId: 501
                note: "Caller is hiding."
      parameters:
        -
          description: "Configured Sonoran CAD server ID."
          name: "serverId"
          in: "path"
          schema:
            type: "integer"
          example: 1
          required: true
        -
          description: "Dispatch or 911 call ID."
          name: "callId"
          in: "path"
          schema:
            type: "integer"
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
              note: "Suspect vehicle fleeing northbound"
              noteType: "text"
              label: "Integration"
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
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/notes" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "note": "Suspect vehicle fleeing northbound",
  "noteType": "text",
  "label": "Integration"
}'
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "callId": 501,
  "note": "Caller is hiding."
}
```

