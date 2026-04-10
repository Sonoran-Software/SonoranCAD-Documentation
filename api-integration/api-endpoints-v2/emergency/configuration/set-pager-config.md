---
description: Replace Inferno pager configuration for a server.
---

# Set Pager Config

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/pager-config`

Replace the Inferno pager configuration for a server. If `nodes` is omitted, Sonoran CAD preserves the existing node tree for that server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "natureWords": {
    "Emergency": "Emergency",
    "NonEmergency": "Non-Emergency",
    "Administrative": "Administrative"
  },
  "maxAddresses": 5,
  "maxBodyLength": 250,
  "nodes": [
    {
      "id": "root-1",
      "name": "Fire",
      "description": "Fire services",
      "permission": "fire",
      "address": "FIRE-01",
      "shortCode": "F1",
      "kind": "group",
      "children": []
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

local response = sonoran:setPagerConfigV2({
    serverId = 1,
    natureWords = {
      Emergency = 'Emergency',
      NonEmergency = 'Non-Emergency',
      Administrative = 'Administrative',
    },
    maxAddresses = 5,
    maxBodyLength = 250,
    nodes = {
      {
        id = 'root-1',
        name = 'Fire',
        description = 'Fire services',
        permission = 'fire',
        address = 'FIRE-01',
        shortCode = 'F1',
        kind = 'group',
        children = {},
      },
    },
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

  const response = await instance.cad.setPagerConfigV2({
    serverId: 1,
    natureWords: {
      Emergency: 'Emergency',
      NonEmergency: 'Non-Emergency',
      Administrative: 'Administrative',
    },
    maxAddresses: 5,
    maxBodyLength: 250,
    nodes: [
      {
        id: 'root-1',
        name: 'Fire',
        description: 'Fire services',
        permission: 'fire',
        address: 'FIRE-01',
        shortCode: 'F1',
        kind: 'group',
        children: [],
      },
    ],
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/pager-config" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "natureWords": {
    "Emergency": "Emergency",
    "NonEmergency": "Non-Emergency",
    "Administrative": "Administrative"
  },
  "maxAddresses": 5,
  "maxBodyLength": 250,
  "nodes": [
    {
      "id": "root-1",
      "name": "Fire",
      "description": "Fire services",
      "permission": "fire",
      "address": "FIRE-01",
      "shortCode": "F1",
      "kind": "group",
      "children": []
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/pager-config", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    natureWords: {
      Emergency: "Emergency",
      NonEmergency: "Non-Emergency",
      Administrative: "Administrative",
    },
    maxAddresses: 5,
    maxBodyLength: 250,
    nodes: [
      {
        id: "root-1",
        name: "Fire",
        description: "Fire services",
        permission: "fire",
        address: "FIRE-01",
        shortCode: "F1",
        kind: "group",
        children: [],
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
  "natureWords": {
    "Emergency": "Emergency",
    "NonEmergency": "Non-Emergency",
    "Administrative": "Administrative"
  },
  "maxAddresses": 5,
  "maxBodyLength": 250,
  "nodes": [
    {
      "id": "root-1",
      "name": "Fire",
      "description": "Fire services",
      "permission": "fire",
      "address": "FIRE-01",
      "shortCode": "F1",
      "kind": "group",
      "children": []
    }
  ]
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/pager-config" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "serverId": 1
}
```
