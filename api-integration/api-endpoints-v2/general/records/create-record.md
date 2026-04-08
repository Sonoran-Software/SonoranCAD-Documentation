---
description: Create a new custom record using a raw record payload or template replacement values.
---

# Create Record

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/records`

Create a custom record for a target account.

## Request Body

Provide exactly one of `accountUuid` or `apiId` as the target user. Then provide either a full `record` object or set `useDictionary` with `recordTypeId` and `replaceValues`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/records" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/records", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
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
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "useDictionary": true,
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  }
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/records" `
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
