---
description: Replace available ERS callouts for a server.
---

# Set Callouts

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/callouts`

> **Rate limit:** `2 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Replace the ERS callout configuration for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "callouts": [
    {
      "id": "armed_suspect",
      "data": {
        "PedActionOnNoActionFound": "Flee",
        "PedActionMinimumTimeoutInMs": 2000,
        "PedChanceToFleeFromPlayer": 50,
        "PedChanceToObtainWeapons": 30,
        "CalloutName": "Armed Suspect",
        "CalloutDescriptions": ["Reports of an armed suspect in the area."],
        "PedChanceToAttackPlayer": 20,
        "PedActionMaximumTimeoutInMs": 10000,
        "Enabled": true,
        "CalloutLocations": [],
        "PedChanceToSurrender": 30,
        "PedWeaponData": ["WEAPON_PISTOL"],
        "CalloutUnitsRequired": {
          "towRequired": false,
          "fireRequired": false,
          "description": "Single suspect, use caution.",
          "policeRequired": true,
          "ambulanceRequired": false
        }
      }
    }
  ]
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

local response = sonoran:setAvailableCalloutsV2({
    // See the request body above for the full callout shape.
    { id = 'armed_suspect', data = {} },
  }, 1)

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

  const response = await instance.cad.setAvailableCalloutsV2([
    // See the request body above for the full callout shape.
    { id: 'armed_suspect', data: {} },
  ], 1);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/callouts" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "callouts": [
    {
      "id": "armed_suspect",
      "data": {
        "PedActionOnNoActionFound": "Flee",
        "PedActionMinimumTimeoutInMs": 2000,
        "PedChanceToFleeFromPlayer": 50,
        "PedChanceToObtainWeapons": 30,
        "CalloutName": "Armed Suspect",
        "CalloutDescriptions": ["Reports of an armed suspect in the area."],
        "PedChanceToAttackPlayer": 20,
        "PedActionMaximumTimeoutInMs": 10000,
        "Enabled": true,
        "CalloutLocations": [],
        "PedChanceToSurrender": 30,
        "PedWeaponData": ["WEAPON_PISTOL"],
        "CalloutUnitsRequired": {
          "towRequired": false,
          "fireRequired": false,
          "description": "Single suspect, use caution.",
          "policeRequired": true,
          "ambulanceRequired": false
        }
      }
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/callouts", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    callouts: [
      {
        id: "armed_suspect",
        data: {
          PedActionOnNoActionFound: "Flee",
          PedActionMinimumTimeoutInMs: 2000,
          PedChanceToFleeFromPlayer: 50,
          PedChanceToObtainWeapons: 30,
          CalloutName: "Armed Suspect",
          CalloutDescriptions: ["Reports of an armed suspect in the area."],
          PedChanceToAttackPlayer: 20,
          PedActionMaximumTimeoutInMs: 10000,
          Enabled: true,
          CalloutLocations: [],
          PedChanceToSurrender: 30,
          PedWeaponData: ["WEAPON_PISTOL"],
          CalloutUnitsRequired: {
            towRequired: false,
            fireRequired: false,
            description: "Single suspect, use caution.",
            policeRequired: true,
            ambulanceRequired: false,
          },
        },
      },
    ],
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
  "callouts": [
    {
      "id": "armed_suspect",
      "data": {
        "PedActionOnNoActionFound": "Flee",
        "PedActionMinimumTimeoutInMs": 2000,
        "PedChanceToFleeFromPlayer": 50,
        "PedChanceToObtainWeapons": 30,
        "CalloutName": "Armed Suspect",
        "CalloutDescriptions": ["Reports of an armed suspect in the area."],
        "PedChanceToAttackPlayer": 20,
        "PedActionMaximumTimeoutInMs": 10000,
        "Enabled": true,
        "CalloutLocations": [],
        "PedChanceToSurrender": 30,
        "PedWeaponData": ["WEAPON_PISTOL"],
        "CalloutUnitsRequired": {
          "towRequired": false,
          "fireRequired": false,
          "description": "Single suspect, use caution.",
          "policeRequired": true,
          "ambulanceRequired": false
        }
      }
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/callouts" `
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
  "callouts": 1
}
```
