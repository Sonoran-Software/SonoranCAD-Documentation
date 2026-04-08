---
description: Delete one or more custom blips.
---

# Delete Blips

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/blips`



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "ids": [14, 15]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/blips" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "ids": [14, 15]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/blips", {
  method: "DELETE",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "ids": [
    14,
    15
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
  "ids": [14, 15]
}
'@

Invoke-RestMethod `
  -Method Delete `
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
  "ids": [
    32,
    33
  ]
}
```
