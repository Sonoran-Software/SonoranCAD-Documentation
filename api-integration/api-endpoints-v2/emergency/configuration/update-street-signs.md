---
description: Update text on one or more configured street signs.
---

# Update Street Signs

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/street-signs`



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "ids": [1, 2],
  "text1": "Mission Row",
  "text2": "Alta St",
  "text3": "Integrity Way"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/street-signs" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "ids": [1, 2],
  "text1": "Mission Row",
  "text2": "Alta St",
  "text3": "Integrity Way"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/street-signs", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "ids": [
    1,
    2
  ],
  "text1": "Mission Row",
  "text2": "Alta St",
  "text3": "Integrity Way"
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
  "ids": [1, 2],
  "text1": "Mission Row",
  "text2": "Alta St",
  "text3": "Integrity Way"
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/street-signs" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "ids": [
    7,
    8
  ]
}
```
