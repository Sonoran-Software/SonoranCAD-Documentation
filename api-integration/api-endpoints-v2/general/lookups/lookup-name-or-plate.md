---
description: Search records by name or plate values.
---

# Lookup Name Or Plate

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/lookups`

Search records by name and plate values.

## Request Body

Optional notification routing supports `notifyCommunityUserId`, `notifyAccountUuid`, or `notifyApiId`.

```json
{
  "first": "John",
  "last": "Doe",
  "mi": "",
  "plate": "",
  "notifyCommunityUserId": "player-1234",
  "types": [7, 12],
  "partial": true
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/lookups" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "first": "John",
  "last": "Doe",
  "mi": "",
  "plate": "",
  "notifyCommunityUserId": "player-1234",
  "types": [7, 12],
  "partial": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/lookups", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "first": "John",
  "last": "Doe",
  "mi": "",
  "plate": "",
  "notifyCommunityUserId": "player-1234",
  "types": [
    7,
    12
  ],
  "partial": true
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
  "first": "John",
  "last": "Doe",
  "mi": "",
  "plate": "",
  "notifyCommunityUserId": "player-1234",
  "types": [7, 12],
  "partial": true
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/lookups" `
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
  },
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
]
```
