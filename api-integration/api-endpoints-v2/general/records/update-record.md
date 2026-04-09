---
description: Update an existing custom record by record ID.
---

# Update Record

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/records/{recordId}`

Update a custom record with either a full `record` payload or template replacement values.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordId` | integer | Record ID. |

## Request Body

Provide either a full `record` object or set `useDictionary` with `templateId` and `replaceValues`. When an account target is needed for the update flow, use `communityUserId`, `accountUuid`, or `apiId`.

```json
{
  "communityUserId": "player-1234",
  "useDictionary": true,
  "templateId": 12,
  "replaceValues": {
    "{{plate}}": "XYZ987"
  }
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/general/records/451" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "useDictionary": true,
  "templateId": 12,
  "replaceValues": {
    "{{plate}}": "XYZ987"
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/records/451", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "useDictionary": true,
  "templateId": 12,
  "replaceValues": {
    "{{plate}}": "XYZ987"
  }
}),
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
  "Content-Type" = "application/json"
}

$body = @'
{
  "communityUserId": "player-1234",
  "useDictionary": true,
  "templateId": 12,
  "replaceValues": {
    "{{plate}}": "XYZ987"
  }
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/general/records/451" `
  -Headers $headers `
  -Body $body
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
