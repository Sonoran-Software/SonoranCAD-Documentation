---
description: Assign one or more identifiers to a group on a server.
---

# Set Identifier Group

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/identifier-groups/{groupName}`

Assign one or more identifiers to a group by `accountUuid`, `apiId`, `apiIds`, or `identIds`.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `groupName` | string | Identifier group name. |

## Request Body

```json
{
  "identIds": [15, 18]
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/identifier-groups/CAR-51" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "identIds": [15, 18]
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
  "identIds": [
    15,
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
  "identIds": [15, 18]
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
