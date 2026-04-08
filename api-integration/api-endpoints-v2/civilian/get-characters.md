---
description: Retrieve characters for an account or API ID.
---

# Get Characters

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/civilian/characters`

Retrieve characters for a Sonoran CAD account or a linked API ID.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `accountUuid` | string (uuid) | Optional | Target account UUID. Provide exactly one of `accountUuid` or `apiId`. |
| `apiId` | string | Optional | Target API ID. Provide exactly one of `accountUuid` or `apiId`. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/civilian/characters?apiId=steam:110000112345678" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/characters?apiId=steam:110000112345678", {
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
  -Uri "https://api.sonorancad.com/v2/civilian/characters?apiId=steam:110000112345678" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
  {
    "recordTypeId": 7,
    "id": 2451,
    "syncId": "citizen:1234",
    "name": "John Doe",
    "type": 7,
    "sections": [
      {
        "category": 0,
        "label": "Civilian Info",
        "fields": [
          {
            "label": "First Name",
            "value": "John",
            "uid": "first_name"
          }
        ]
      }
    ]
  }
]
```
