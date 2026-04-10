---
description: Update an existing identifier for an account.
---

# Update Identifier

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers/{identId}`

Update one or more editable fields on an identifier.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |
| `identId` | integer | Identifier ID. |

## Request Body

Provide at least one property to change. The backend accepts partial updates and only overwrites the fields you send.

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| `status` | integer | No | New unit status. See `UNIT_STATUS` below. |
| `aop` | string | No | New area of patrol string. |
| `unitNum` | string | No | Updated unit number. |
| `name` | string | No | Updated display name. |
| `district` | string | No | Updated district name. |
| `department` | string | No | Updated department name. |
| `subdivision` | string | No | Updated subdivision name. |
| `rank` | string | No | Updated rank label. |
| `group` | string | No | Updated persistent group name. |
| `page` | integer | No | New CAD page. See `UNIT_PAGE` below. |
| `isDispatch` | boolean | No | Marks or unmarks the identifier as a dispatcher. |

```json
{
  "status": 2,
  "group": "SUPERVISOR-1",
  "page": 3
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

local response = sonoran:updateIdentifierV2('00000000-0000-0000-0000-000000000000', 12, {
    status = 2,
    unitNum = '1A-01',
    name = 'John Doe',
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

  const response = await instance.cad.updateIdentifierV2('00000000-0000-0000-0000-000000000000', 12, {
    status: 2,
    unitNum: '1A-01',
    name: 'John Doe',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "status": 2,
  "group": "SUPERVISOR-1",
  "page": 3
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "status": 2,
  "group": "SUPERVISOR-1",
  "page": 3
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
  "status": 2,
  "group": "SUPERVISOR-1",
  "page": 3
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "identId": 12,
  "serverId": 1,
  "identifier": {
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
