---
description: Set status for one or more identifiers.
---

# Set Unit Status

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/status`

Set a new unit status for one or more identifiers resolved by `communityUserId`, `communityUserIds`, `accountUuid`, or `identIds`.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

Provide at least one target using `communityUserId`, `communityUserIds`, `accountUuid`, or `identIds`.

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| `communityUserId` | string | No | Updates all active identifiers for one linked community user. |
| `communityUserIds` | array of strings | No | Updates all active identifiers for multiple linked community users. |
| `accountUuid` | string (uuid) | No | Updates all active identifiers for the target account. |
| `identIds` | array of integers | No | Directly target one or more identifier IDs. |
| `status` | integer | Yes | Unit status enum. See `UNIT_STATUS` below. |

```json
{
  "communityUserIds": ["player-1234"],
  "status": 3
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units/status" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserIds": ["player-1234"],
  "status": 3
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/units/status", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserIds": [
    "player-1234"
  ],
  "status": 3
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
  "communityUserIds": ["player-1234"],
  "status": 3
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/units/status" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "updated": 1,
  "status": "ENROUTE"
}
```

## Enumeration Values

### UNIT_STATUS

| Value | Description |
| --- | --- |
| `0` | `UNAVAILABLE` |
| `1` | `BUSY` |
| `2` | `AVAILABLE` |
| `3` | `ENROUTE` |
| `4` | `ON_SCENE` |
| `100` | `OFFLINE` |
