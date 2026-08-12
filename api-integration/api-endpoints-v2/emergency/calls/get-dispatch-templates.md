---
description: Retrieve the custom dispatch call layouts configured for the authenticated community.
---

# Get Dispatch Templates

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/dispatch-templates`

Retrieve every dispatch layout for the community. Add `/{templateId}` to retrieve one layout. Use the returned field `uid` values when creating a custom dispatch call.

A template contains grouped `sections`, responsive field widths, and custom `statusOptions`. Each status option maps its community-facing label and API `id` to the canonical call behavior: `0` pending, `1` active, or `2` closed.

Fields with the `status`, `units`, or `description` binding are locked and required. The code field's visible label is controlled by the community's geographical 10-code setting.

## Example Request

{% tabs %}
{% tab title="Sonoran.lua" %}
```lua
local templates = sonoran.cad:getDispatchTemplatesV2()
local template = sonoran.cad:getDispatchTemplatesV2(1)
```
{% endtab %}
{% tab title="SonoranCADFiveM" %}
```lua
local cad = exports["sonorancad"]:getCadClient()
local templates = cad:getDispatchTemplatesV2()
```
{% endtab %}
{% tab title="Sonoran.js" %}
```javascript
const templates = await instance.cad.getDispatchTemplatesV2();
const template = await instance.cad.getDispatchTemplatesV2(1);
```
{% endtab %}
{% tab title="Sonoran.py" %}
```python
templates = instance.cad.getDispatchTemplatesV2()
template = instance.cad.getDispatchTemplatesV2(1)
```
{% endtab %}
{% tab title="Sonoran.Net" %}
```csharp
var templates = await sonoran.Cad.getDispatchTemplatesV2();
var template = await sonoran.Cad.getDispatchTemplatesV2(1);
```
{% endtab %}
{% tab title="OpenAPI" %}
```yaml
openapi: "3.0.3"
info:
  title: Sonoran CAD v2 - Dispatch Templates
  version: 1.0.0
servers:
  - url: https://api.sonorancad.com
paths:
  /v2/emergency/dispatch-templates:
    get:
      operationId: getDispatchTemplates
      security:
        - bearerAuth: []
      responses:
        '200':
          description: Community dispatch templates
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/DispatchTemplate'
  /v2/emergency/dispatch-templates/{templateId}:
    get:
      operationId: getDispatchTemplate
      security:
        - bearerAuth: []
      parameters:
        - name: templateId
          in: path
          required: true
          schema: { type: integer, minimum: 1 }
      responses:
        '200':
          description: Dispatch template
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/DispatchTemplate'
        '404': { description: Template not found }
components:
  securitySchemes:
    bearerAuth: { type: http, scheme: bearer, bearerFormat: JWT }
  schemas:
    DispatchTemplate:
      type: object
      properties:
        templateId: { type: integer }
        name: { type: string }
        version: { type: integer }
        isDefault: { type: boolean }
        statusOptions:
          type: array
          items:
            type: object
            properties:
              id: { type: string }
              label: { type: string }
              status: { type: integer, enum: [0, 1, 2] }
        sections:
          type: array
          items:
            type: object
            properties:
              uid: { type: string }
              label: { type: string }
              icon: { type: string }
              fields:
                type: array
                items:
                  type: object
                  properties:
                    uid: { type: string }
                    type: { type: string }
                    label: { type: string }
                    binding: { type: string }
                    size: { type: integer, minimum: 1, maximum: 12 }
                    required: { type: boolean }
                    locked: { type: boolean }
                    placeholder: { type: string }
                    options: { type: array, items: { type: string } }
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/dispatch-templates" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}
{% endtabs %}

## Response

```json
[
  {
    "templateId": 1,
    "name": "UK Control Room",
    "version": 2,
    "isDefault": true,
    "statusOptions": [
      { "id": "awaiting_deployment", "label": "Awaiting Deployment", "status": 0 },
      { "id": "deployed", "label": "Deployed", "status": 1 },
      { "id": "resolved", "label": "Resolved", "status": 2 }
    ],
    "sections": []
  }
]
```
