---
description: Trigger an Inferno/ERS pager callout for a server.
---

# Trigger Pager System

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/callouts/trigger`

Trigger the Inferno/ERS pager system by sending a new callout event to the configured server listener.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "callout": {
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
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/callouts/trigger" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "callout": {
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
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/callouts/trigger", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    callout: {
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
  "callout": {
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
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/callouts/trigger" `
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
  "callout": {
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
}
```
