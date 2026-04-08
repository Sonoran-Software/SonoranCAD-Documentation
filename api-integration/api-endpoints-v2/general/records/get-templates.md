---
description: Retrieve all record templates for the authenticated community.
---

# Get Templates

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/templates`

Return every record template configured for the authenticated community.

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/templates" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/templates", {
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
  -Uri "https://api.sonorancad.com/v2/general/templates" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
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
]
```
