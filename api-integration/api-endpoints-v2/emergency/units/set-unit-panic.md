---
description: Set panic state for one or more identifiers.
---

# Set Unit Panic

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/panic`

Set the panic state for one or more identifiers resolved by `accountUuid`, `apiId`, `apiIds`, or `identIds`.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "identIds": [15, 18],
  "isPanic": true
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units/panic" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "identIds": [15, 18],
  "isPanic": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/units/panic", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "identIds": [
    15,
    18
  ],
  "isPanic": true
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
  "identIds": [15, 18],
  "isPanic": true
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/units/panic" `
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
  "isPanic": true
}
```
