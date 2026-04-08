---
description: Search records by a custom mapped field.
---

# Lookup By Custom Search

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/lookups/custom`

Search records by a custom lookup mapping.

## Request Body

```json
{
  "map": "drivers_license",
  "value": "D1234567",
  "types": [7],
  "partial": false
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/lookups/custom" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "map": "drivers_license",
  "value": "D1234567",
  "types": [7],
  "partial": false
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/lookups/custom", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "map": "drivers_license",
  "value": "D1234567",
  "types": [
    7
  ],
  "partial": false
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
  "map": "drivers_license",
  "value": "D1234567",
  "types": [7],
  "partial": false
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/lookups/custom" `
  -Headers $headers `
  -Body $body
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
