---
description: Update the primary identifier on a dispatch call.
---

# Update Call Primary

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/primary`



## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `callId` | integer | Dispatch or 911 call ID. |

## Request Body

```json
{
  "identId": 15,
  "trackPrimary": true
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/primary" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "identId": 15,
  "trackPrimary": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/primary", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "identId": 15,
  "trackPrimary": true
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
  "identId": 15,
  "trackPrimary": true
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/primary" `
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
  "identId": 12,
  "trackPrimary": true
}
```
