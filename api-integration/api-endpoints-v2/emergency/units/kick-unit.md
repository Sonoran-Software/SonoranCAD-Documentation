---
description: Force a unit offline by community user ID.
---

# Kick Unit

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/kick`

Force the currently selected identifier for a community user ID offline.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

Provide the target unit with `communityUserId`.

```json
{
  "communityUserId": "player-1234",
  "reason": "Connection reset by integration"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units/kick" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "reason": "Connection reset by integration"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/units/kick", {
  method: "DELETE",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "reason": "Connection reset by integration"
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
  "communityUserId": "player-1234",
  "reason": "Connection reset by integration"
}
'@

Invoke-RestMethod `
  -Method Delete `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/units/kick" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "identId": 12,
  "reason": "Restarting server."
}
```
