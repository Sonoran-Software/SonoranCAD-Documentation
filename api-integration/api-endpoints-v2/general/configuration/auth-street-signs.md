---
description: Validate a street-sign request against the configured server ID and source IP.
---

# Auth Street Signs

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/servers/{serverId}/street-sign-auth`

Validate that the requesting IP address matches the configured smart-sign server entry.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/servers/1/street-sign-auth" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/servers/1/street-sign-auth", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
  },
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
}

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/servers/1/street-sign-auth" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "authorized": true,
  "serverId": 1
}
```
