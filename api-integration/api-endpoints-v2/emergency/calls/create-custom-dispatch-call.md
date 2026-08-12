---
description: Create a dispatch call from a community-defined layout.
---

# Create Custom Dispatch Call

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/custom-dispatch-calls`

Create a dispatch call using a configured template. Call `GET /v2/emergency/dispatch-templates` first and key `values` by each field's `uid`.

The status field value must be a status option `id`, not the canonical numeric status. Sonoran CAD maps that option to pending, active, or closed behavior. Unit targets are supplied through the target properties and are snapshotted into the required units field. The normalized template and complete value dictionary are stored on the call, so later template edits do not change historical calls.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| `templateId` | integer | Yes | Template returned by the dispatch-template endpoint. |
| `values` | object | Yes | Field values keyed by template field `uid`. Unknown keys are rejected. |
| `identIds` | array of integers | Conditional | Active identifier IDs to attach. At least one valid unit target is required. |
| `accountUuid` | string (uuid) | Conditional | Account whose selected identifier is attached. |
| `accounts` | array of strings (uuid) | Conditional | Accounts whose selected identifiers are attached. |
| `communityUserId` | string | Conditional | One linked community user target. |
| `communityUserIds` | array of strings | Conditional | Linked community user targets. |
| `roblox` | string | Conditional | Linked Roblox target. |
| `discord` | string | Conditional | Linked Discord target. |
| `notes` | array | No | Initial call notes. |
| `metaData` | object | No | String metadata, including optional map coordinates. |
| `deleteAfterMinutes` | integer | No | Schedule automatic call deletion. |

## Example Request

{% tabs %}
{% tab title="Sonoran.lua" %}
```lua
local response = sonoran.cad:createCustomDispatchCallV2({
  serverId = 1,
  templateId = 1,
  values = {
    status = "deployed",
    description = "Reports of a disturbance outside the station.",
    code = "GRADE_1",
    caller_name = "Alex Smith"
  },
  communityUserIds = {"player-1234"}
})
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()
local response = cad:createCustomDispatchCallV2({
  templateId = 1,
  values = { status = "deployed", description = "Disturbance reported." },
  communityUserIds = {"player-1234"}
})
```
{% endtab %}
{% tab title="Sonoran.js" %}
```javascript
const response = await instance.cad.createCustomDispatchCallV2({
  serverId: 1,
  templateId: 1,
  values: {
    status: 'deployed',
    description: 'Reports of a disturbance outside the station.',
    code: 'GRADE_1',
    caller_name: 'Alex Smith',
  },
  communityUserIds: ['player-1234'],
});
```
{% endtab %}
{% tab title="Sonoran.py" %}
```python
response = instance.cad.createCustomDispatchCallV2({
    "serverId": 1,
    "templateId": 1,
    "values": {
        "status": "deployed",
        "description": "Reports of a disturbance outside the station.",
        "code": "GRADE_1",
        "caller_name": "Alex Smith",
    },
    "communityUserIds": ["player-1234"],
})
```
{% endtab %}
{% tab title="Sonoran.Net" %}
```csharp
var response = await sonoran.Cad.createCustomDispatchCallV2(new CreateCustomDispatchCallV2Request
{
    ServerId = 1,
    TemplateId = 1,
    Values = new Dictionary<string, object?>
    {
        ["status"] = "deployed",
        ["description"] = "Reports of a disturbance outside the station.",
        ["code"] = "GRADE_1",
        ["caller_name"] = "Alex Smith"
    },
    CommunityUserIds = new[] { "player-1234" }
});
```
{% endtab %}
{% tab title="OpenAPI" %}
```yaml
openapi: "3.0.3"
info:
  title: Sonoran CAD v2 - Create Custom Dispatch Call
  version: 1.0.0
servers:
  - url: https://api.sonorancad.com
paths:
  /v2/emergency/servers/{serverId}/custom-dispatch-calls:
    post:
      operationId: createCustomDispatchCall
      security:
        - bearerAuth: []
      parameters:
        - name: serverId
          in: path
          required: true
          schema: { type: integer, minimum: 1 }
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required: [templateId, values]
              properties:
                templateId: { type: integer, minimum: 1 }
                values: { type: object, additionalProperties: true }
                identIds: { type: array, items: { type: integer } }
                accountUuid: { type: string, format: uuid }
                accounts: { type: array, items: { type: string, format: uuid } }
                communityUserId: { type: string }
                communityUserIds: { type: array, items: { type: string } }
                roblox: { type: string }
                discord: { type: string }
                notes: { type: array, items: { type: object } }
                metaData: { type: object, additionalProperties: { type: string } }
                deleteAfterMinutes: { type: integer, minimum: 0 }
            example:
              templateId: 1
              values:
                status: deployed
                description: Reports of a disturbance outside the station.
                code: GRADE_1
                caller_name: Alex Smith
              communityUserIds: [player-1234]
      responses:
        '201': { description: Custom dispatch call created }
        '400': { description: Template values or required fields are invalid }
        '404': { description: Template or unit target not found }
components:
  securitySchemes:
    bearerAuth: { type: http, scheme: bearer, bearerFormat: JWT }
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/custom-dispatch-calls" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "templateId": 1,
    "values": {
      "status": "deployed",
      "description": "Reports of a disturbance outside the station.",
      "code": "GRADE_1",
      "caller_name": "Alex Smith"
    },
    "communityUserIds": ["player-1234"]
  }'
```
{% endtab %}
{% endtabs %}

## Response

The response is the stored dispatch call. It includes canonical fields for existing integrations plus `template`, `values`, and `statusId` for the customized format.
