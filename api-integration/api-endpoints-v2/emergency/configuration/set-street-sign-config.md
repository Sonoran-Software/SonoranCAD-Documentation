---
description: Replace street sign configuration for a server.
---

# Set Street Sign Config

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/street-sign-config`

Replace the full street sign configuration for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
    }
  ]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
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
  "signs": [
    {
      "id": 7,
      "coordinates": {
        "x": 420.1,
        "y": -980.4,
        "z": 30.8,
        "w": 0.0
      },
      "label": "Mission Row",
      "text1": "Mission Row",
      "text2": "Integrity Way",
      "text3": ""
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/street-sign-config" `
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
  "signs": 1
}
```
