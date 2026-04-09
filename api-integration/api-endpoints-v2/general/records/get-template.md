---
description: Retrieve a single record template by record type ID.
---

# Get Template

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/templates/{recordTypeId}`

Return one record template by its record type ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordTypeId` | integer | Custom record template ID. |

## Example Request

{% tabs %}
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

  const response = await instance.cad.getTemplatesV2(1);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/templates/12" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/templates/12", {
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
  -Uri "https://api.sonorancad.com/v2/general/templates/12" `
  -Headers $headers
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
