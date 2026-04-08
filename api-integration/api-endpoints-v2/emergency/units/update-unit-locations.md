---
description: Update live map location data for one or more units.
---

# Update Unit Locations

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/unit-locations`

Queue and broadcast one or more unit location updates.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "updates": [
    {
      "apiId": "steam:110000112345678",
      "location": "Mission Row",
      "coordinates": {
        "x": 441.2,
        "y": -981.9,
        "z": 30.7,
        "w": 90.0
      },
      "peerId": "peer-1",
      "vehicle": {
        "model": "police3",
        "headingOffset": 0
      }
    }
  ]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/unit-locations" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "updates": [
    {
      "apiId": "steam:110000112345678",
      "location": "Mission Row",
      "coordinates": {
        "x": 441.2,
        "y": -981.9,
        "z": 30.7,
        "w": 90.0
      },
      "peerId": "peer-1",
      "vehicle": {
        "model": "police3",
        "headingOffset": 0
      }
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/unit-locations", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "updates": [
    {
      "apiId": "steam:110000112345678",
      "location": "Mission Row",
      "coordinates": {
        "x": 441.2,
        "y": -981.9,
        "z": 30.7,
        "w": 90.0
      },
      "peerId": "peer-1",
      "vehicle": {
        "model": "police3",
        "headingOffset": 0
      }
    }
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
  "updates": [
    {
      "apiId": "steam:110000112345678",
      "location": "Mission Row",
      "coordinates": {
        "x": 441.2,
        "y": -981.9,
        "z": 30.7,
        "w": 90.0
      },
      "peerId": "peer-1",
      "vehicle": {
        "model": "police3",
        "headingOffset": 0
      }
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/unit-locations" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "updated": 1
}
```
