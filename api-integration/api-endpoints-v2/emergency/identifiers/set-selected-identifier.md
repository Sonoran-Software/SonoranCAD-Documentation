---
description: Set the selected identifier for an account.
---

# Set Selected Identifier

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/selected-identifier`

Set the selected identifier for an account.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |

## Request Body

```json
{
  "identId": 15
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

local response = sonoran:selectIdentifierV2('00000000-0000-0000-0000-000000000000', 12)

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

  const response = await instance.cad.selectIdentifierV2('00000000-0000-0000-0000-000000000000', 12);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/selected-identifier" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "identId": 15
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/selected-identifier", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "identId": 15
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
  "identId": 15
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/selected-identifier" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1,
  "isDispatch": false,
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
