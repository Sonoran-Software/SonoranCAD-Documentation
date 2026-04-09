---
description: Assign one or more identifiers to a group on a server.
---

# Set Identifier Group

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/identifier-groups/{groupName}`

Assign one or more identifiers to a group by `communityUserId`, `communityUserIds`, `accountUuid`, or `identIds`.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `groupName` | string | Identifier group name. |

## Request Body

Provide at least one target using `communityUserId`, `communityUserIds`, `accountUuid`, or `identIds`.

```json
{
  "communityUserIds": ["player-1234"]
}
```

## Example Request

{% tabs %}
{% tab title="Sonoran.js" %}
```javascript
// npm install @sonoransoftware/sonoran.js
const Sonoran = require('@sonoransoftware/sonoran.js');

(async () => {
  const instance = new Sonoran.Instance({
    communityId: 'YOUR_COMMUNITY_ID',
    apiKey: 'YOUR_API_KEY',
    product: Sonoran.productEnums.CAD,
    serverId: 1,
  });

  const response = await instance.cad.addIdentifiersToGroupV2({
    serverId: 1,
    groupName: 'CAR-51',
    identIds: [12],
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/identifier-groups/CAR-51" \
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
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/identifier-groups/CAR-51", {
  method: "PUT",
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
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/identifier-groups/CAR-51" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "ok": true
}
```
