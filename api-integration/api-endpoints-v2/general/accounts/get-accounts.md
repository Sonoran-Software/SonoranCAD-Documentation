---
description: Retrieve paginated community accounts.
---

# Get Accounts

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/accounts`

Return paginated community accounts.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `limit` | integer | `100` | Maximum number of accounts returned. The backend enforces 1-100. |
| `offset` | integer | `0` | Number of accounts to skip. |
| `status` | integer | `1` | Filter by account status. See `ACCOUNT_STATUS` below. |
| `username` | string | Optional | Case-insensitive username filter. |

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

  const response = await instance.cad.getAccountsV2({
    limit: 25,
    offset: 0,
    username: 'john',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/accounts?limit=25&offset=0&status=1" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/accounts?limit=25&offset=0&status=1", {
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
  -Uri "https://api.sonorancad.com/v2/general/accounts?limit=25&offset=0&status=1" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "pagination": {
    "limit": 25,
    "offset": 0,
    "total": 1
  },
  "accounts": [
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
  ]
}
```

## Enumeration Values

### ACCOUNT_STATUS

| Value | Description |
| --- | --- |
| `0` | `PENDING` |
| `1` | `VALIDATED` |
| `2` | `EXPIRED` |
| `3` | `REMOVED` |
| `4` | `BANNED` |
