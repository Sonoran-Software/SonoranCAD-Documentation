---
description: Retrieve units for a specific account on a configured server.
---

# Get Account Units

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/accounts/{accountUuid}/units`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Retrieve units for a specific account on a configured server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `onlyOnline` | boolean | `true` | Only returns online identifiers for the target account. |
| `onlyUnits` | boolean | `true` | When `true`, hides dispatcher identifiers. |
| `limit` | integer | `100` | Maximum number of rows returned. |
| `offset` | integer | `0` | Number of rows to skip. |

## Example Request

{% tabs %}
{% tab title="Sonoran.lua" %}
```lua
-- luarocks install sonoran.lua
local Sonoran = require("sonoran")

local sonoran = Sonoran.createClient({
  communityId = "YOUR_COMMUNITY_ID",
  apiKey = "YOUR_API_KEY",
  defaultServerId = 1
})

local response = sonoran:getAccountUnitsV2({
    serverId = 1,
    accountUuid = '00000000-0000-0000-0000-000000000000',
    onlyOnline = true,
    onlyUnits = true,
    limit = 100,
    offset = 0,
  })

-- Inspect response.success, response.data, or response.reason as needed.
print(response.success)
```
{% endtab %}
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

  const response = await instance.cad.getAccountUnitsV2({
    serverId: 1,
    accountUuid: '00000000-0000-0000-0000-000000000000',
    onlyOnline: true,
    onlyUnits: true,
    limit: 100,
    offset: 0,
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/accounts/00000000-0000-0000-0000-000000000000/units?onlyOnline=true&onlyUnits=true&limit=100&offset=0" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/accounts/00000000-0000-0000-0000-000000000000/units?onlyOnline=true&onlyUnits=true&limit=100&offset=0", {
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
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/accounts/00000000-0000-0000-0000-000000000000/units?onlyOnline=true&onlyUnits=true&limit=100&offset=0" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "units": [
    {
      "id": 12,
      "accId": "00000000-0000-0000-0000-000000000000",
      "status": 3,
      "isPanic": false,
      "location": "Mission Row PD",
      "coordinates": {
        "x": 123.45,
        "y": -456.78,
        "z": 32.1,
        "w": 180.0
      },
      "aop": "Los Santos",
      "data": {
        "unitNum": "A-10",
        "name": "John Doe",
        "district": "Los Santos",
        "department": "LSPD",
        "subdivision": "Patrol",
        "rank": "Officer",
        "group": "CAR-51",
        "page": 0,
        "apiIds": [
          "steam:110000112345678"
        ]
      },
      "isDispatch": false
    }
  ]
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

### UNIT_PAGE

| Value | Description |
| --- | --- |
| `0` | `POLICE` |
| `1` | `FIRE` |
| `2` | `EMS` |
| `3` | `DISPATCH` |
| `-1` | `UNKNOWN` |
