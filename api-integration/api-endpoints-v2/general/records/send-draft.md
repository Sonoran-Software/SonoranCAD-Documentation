---
description: Build a draft record from a template and optionally send it to an active account.
---

# Send Draft

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/record-drafts`

Build a draft record from a template and, when a target account is provided, send it to the user over the active websocket session.

## Request Body

```json
{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "apiId": "steam:110000112345678"
}
```

## Example Request

{% tabs %}
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
  "apiId": "steam:110000112345678"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/record-drafts", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "apiId": "steam:110000112345678"
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
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "apiId": "steam:110000112345678"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/record-drafts" `
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
