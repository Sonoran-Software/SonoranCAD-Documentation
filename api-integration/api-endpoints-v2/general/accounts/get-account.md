---
description: Retrieve a single community account by account UUID, API ID, or username.
---

# Get Account

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/accounts/account`

Return a single community account record.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `accountUuid` | string (uuid) | Optional | Target account UUID. Provide exactly one identifier. |
| `apiId` | string | Optional | Target API ID. Provide exactly one identifier. |
| `username` | string | Optional | Target username. Provide exactly one identifier. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/accounts/account?username=ExampleUser" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/accounts/account?username=ExampleUser", {
  method: "GET",
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
  -Method Get `
  -Uri "https://api.sonorancad.com/v2/general/accounts/account?username=ExampleUser" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "uuid": "00000000-0000-0000-0000-000000000000",
  "username": "ExampleUser",
  "status": 1,
  "joined": "2026-01-14T18:22:00Z",
  "lastLogin": "2026-04-08T20:55:00Z",
  "permissions": {
    "police": true,
    "dispatch": true,
    "liveMap": true,
    "adminInGameIntegration": true
  },
  "apiIds": [
    "steam:110000112345678"
  ]
}
```
