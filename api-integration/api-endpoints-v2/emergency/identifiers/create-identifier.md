---
description: Create a new identifier for an account.
---

# Create Identifier

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Create a new identifier for an account.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |

## Request Body

All identifier properties are optional in the backend. If omitted, the server uses the defaults shown below.

| Property | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `status` | integer | No | `0` | Initial identifier status. See `UNIT_STATUS` below. |
| `aop` | string | No | `""` | Optional area of patrol string. |
| `unitNum` | string | No | `"NEW UNIT"` | Displayed unit number. |
| `name` | string | No | `"NO NAME"` | Identifier display name. |
| `district` | string | No | `"NOT SET"` | District name. |
| `department` | string | No | `"NOT SET"` | Department name. |
| `subdivision` | string | No | `"NOT SET"` | Subdivision name. |
| `rank` | string | No | `"NOT SET"` | Rank label. |
| `group` | string | No | `""` | Optional persistent group name. |
| `page` | integer | No | `-1` | CAD page enum. See `UNIT_PAGE` below. |
| `isDispatch` | boolean | No | `false` | Marks the identifier as a dispatcher. |

```json
{
  "status": 0,
  "aop": "Los Santos",
  "unitNum": "A-10",
  "name": "John Doe",
  "district": "Los Santos",
  "department": "LSPD",
  "subdivision": "Patrol",
  "rank": "Officer",
  "group": "CAR-51",
  "page": 0,
  "isDispatch": false
}
```

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

local response = sonoran:createIdentifierV2('00000000-0000-0000-0000-000000000000', {
    status = 0,
    unitNum = '1A-01',
    name = 'John Doe',
    department = 'Police',
    subdivision = 'Patrol',
    rank = 'Officer',
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

  const response = await instance.cad.createIdentifierV2('00000000-0000-0000-0000-000000000000', {
    status: 0,
    unitNum: '1A-01',
    name: 'John Doe',
    department: 'Police',
    subdivision: 'Patrol',
    rank: 'Officer',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "status": 0,
  "aop": "Los Santos",
  "unitNum": "A-10",
  "name": "John Doe",
  "district": "Los Santos",
  "department": "LSPD",
  "subdivision": "Patrol",
  "rank": "Officer",
  "group": "CAR-51",
  "page": 0,
  "isDispatch": false
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "status": 0,
  "aop": "Los Santos",
  "unitNum": "A-10",
  "name": "John Doe",
  "district": "Los Santos",
  "department": "LSPD",
  "subdivision": "Patrol",
  "rank": "Officer",
  "group": "CAR-51",
  "page": 0,
  "isDispatch": false
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
  "status": 0,
  "aop": "Los Santos",
  "unitNum": "A-10",
  "name": "John Doe",
  "district": "Los Santos",
  "department": "LSPD",
  "subdivision": "Patrol",
  "rank": "Officer",
  "group": "CAR-51",
  "page": 0,
  "isDispatch": false
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "identId": 42
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
