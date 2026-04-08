---
description: Create a custom blip.
---

# Create Blip

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/blips`



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "coordinates": {
    "x": 441.2,
    "y": -981.9,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "scene",
  "icon": "fa-circle",
  "color": "red",
  "tooltip": "Scene perimeter",
  "radius": 50.0,
  "data": [
    {
      "title": "Units",
      "text": "2"
    }
  ]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/blips" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "coordinates": {
    "x": 441.2,
    "y": -981.9,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "scene",
  "icon": "fa-circle",
  "color": "red",
  "tooltip": "Scene perimeter",
  "radius": 50.0,
  "data": [
    {
      "title": "Units",
      "text": "2"
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/blips", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "coordinates": {
    "x": 441.2,
    "y": -981.9,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "scene",
  "icon": "fa-circle",
  "color": "red",
  "tooltip": "Scene perimeter",
  "radius": 50.0,
  "data": [
    {
      "title": "Units",
      "text": "2"
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
  "coordinates": {
    "x": 441.2,
    "y": -981.9,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "scene",
  "icon": "fa-circle",
  "color": "red",
  "tooltip": "Scene perimeter",
  "radius": 50.0,
  "data": [
    {
      "title": "Units",
      "text": "2"
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/blips" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "id": 32,
  "coordinates": {
    "x": 425.5,
    "y": -979.8,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "radius",
  "icon": "fa-location-dot",
  "color": "#ff0000",
  "tooltip": "Perimeter",
  "data": [
    {
      "title": "Assigned Unit",
      "text": "A-10"
    }
  ],
  "radius": 100.0
}
```
