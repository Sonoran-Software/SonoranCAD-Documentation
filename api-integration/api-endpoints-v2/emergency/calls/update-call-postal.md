---
description: Update the postal on a dispatch call.
---

# Update Call Postal

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/postal`



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `callId` | integer | Dispatch or 911 call ID. |

## Request Body

```json
{
  "postal": "9001"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/postal" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "postal": "9001"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/postal", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "postal": "9001"
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
  "postal": "9001"
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/postal" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "callId": 501,
  "postal": "9002"
}
```
