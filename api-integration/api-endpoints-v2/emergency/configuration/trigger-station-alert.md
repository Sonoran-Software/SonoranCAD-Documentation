---
description: Trigger a station alert for a server.
---

# Trigger Station Alert

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/stations/alert`

Trigger the station alert system by sending a station alert event to the configured server listener.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "alert": {
    "locations": [
      {
        "name": "Fire Station One",
        "open": ["Door 1", "Door 2"],
        "close": ["Door 3"]
      }
    ],
    "message": "Structure fire at 101 Alta Street",
    "colors": ["blue", "red"],
    "tone": "tone1"
  }
}
```

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

  const response = await instance.cad.triggerStationAlertV2({
    locations: [
      { name: 'Fire Station One', open: ['Door 1'], close: ['Door 2'] },
    ],
    message: 'Structure fire at 101 Alta Street',
    colors: ['blue', 'red'],
    tone: 'tone1',
  }, 1);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/stations/alert" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "alert": {
    "locations": [
      {
        "name": "Fire Station One",
        "open": ["Door 1", "Door 2"],
        "close": ["Door 3"]
      }
    ],
    "message": "Structure fire at 101 Alta Street",
    "colors": ["blue", "red"],
    "tone": "tone1"
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/stations/alert", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    alert: {
      locations: [
        {
          name: "Fire Station One",
          open: ["Door 1", "Door 2"],
          close: ["Door 3"],
        },
      ],
      message: "Structure fire at 101 Alta Street",
      colors: ["blue", "red"],
      tone: "tone1",
    },
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
  "alert": {
    "locations": [
      {
        "name": "Fire Station One",
        "open": ["Door 1", "Door 2"],
        "close": ["Door 3"]
      }
    ],
    "message": "Structure fire at 101 Alta Street",
    "colors": ["blue", "red"],
    "tone": "tone1"
  }
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/stations/alert" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1,
  "alert": {
    "locations": [
      {
        "name": "Fire Station One",
        "open": ["Door 1", "Door 2"],
        "close": ["Door 3"]
      }
    ],
    "message": "Structure fire at 101 Alta Street",
    "colors": ["blue", "red"],
    "tone": "tone1"
  }
}
```
