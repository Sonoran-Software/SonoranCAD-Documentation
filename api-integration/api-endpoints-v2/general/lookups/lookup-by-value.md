---
description: Search records by numeric, account-backed, or secret-backed values.
---

# Lookup By Value

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/lookups/by-value`

Search records by a typed lookup value.

## Request Body

Optional notification routing supports `notifyCommunityUserId`, `notifyAccountUuid`, or `notifyApiId`.

```json
{
  "searchType": "NUMBER",
  "value": "451",
  "notifyCommunityUserId": "player-1234",
  "types": [12]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/lookups/by-value" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "searchType": "NUMBER",
  "value": "451",
  "notifyCommunityUserId": "player-1234",
  "types": [12]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/lookups/by-value", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "searchType": "NUMBER",
  "value": "451",
  "notifyCommunityUserId": "player-1234",
  "types": [
    12
  ]
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
  "searchType": "NUMBER",
  "value": "451",
  "notifyCommunityUserId": "player-1234",
  "types": [12]
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/lookups/by-value" `
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
