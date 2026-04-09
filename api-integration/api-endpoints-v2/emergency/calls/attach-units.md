---
description: Attach identifiers or a group to a dispatch call.
---

# Attach Units

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}/attachments`

Attach identifiers or a group to a dispatch call.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `callId` | integer | Dispatch or 911 call ID. |

## Request Body

Provide either `groupName` or one or more identifier targets. Identifier targets can include `communityUserId`, `communityUserIds`, `accountUuid`, `apiId`, `apiIds`, or `identIds`.

```json
{
  "communityUserIds": ["player-1234"]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/attachments" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserIds": ["player-1234"]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/attachments", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserIds": [
    "player-1234"
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
  "communityUserIds": ["player-1234"]
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501/attachments" `
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
  "identIds": [
    12,
    18
  ]
}
```
