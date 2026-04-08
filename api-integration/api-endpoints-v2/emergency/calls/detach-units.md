---
description: Detach identifiers or a group from any active dispatch call.
---

# Detach Units

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/attachments`

Detach identifiers or a group from any currently attached dispatch call.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

Provide either `groupName` or one or more identifier targets.

```json
{
  "identIds": [12, 18]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/attachments" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "identIds": [12, 18]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/attachments", {
  method: "DELETE",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "identIds": [
    12,
    18
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
  "identIds": [12, 18]
}
'@

Invoke-RestMethod `
  -Method Delete `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/attachments" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "identIds": [
    12,
    18
  ]
}
```
