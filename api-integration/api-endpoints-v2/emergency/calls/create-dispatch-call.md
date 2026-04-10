---
description: Create a new dispatch call.
---

# Create Dispatch Call

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls`

Create a new dispatch call and attach initial units resolved from community user IDs or account UUIDs.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

The backend requires at least one identifier target through `communityUserIds` or `accounts`.

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| `origin` | integer | Yes | Call origin enum. See `CALL_ORIGIN` below. |
| `status` | integer | Yes | Call status enum. See `CALL_STATUS` below. |
| `priority` | integer | Yes | Call priority. |
| `block` | string | Yes | Block or intersection label. |
| `address` | string | Yes | Dispatch address text. |
| `postal` | string | Yes | Postal code. |
| `title` | string | Yes | Short dispatch title. |
| `code` | string | Yes | Call code such as `211`. |
| `description` | string | Yes | Full call description. |
| `notes` | array | Yes | Initial note objects to store on the call. |
| `communityUserIds` | array of strings | No | Linked community users whose active identifiers should be attached. |
| `accounts` | array of strings (uuid) | No | Accounts whose selected identifiers should be attached. |
| `metaData` | object | No | Arbitrary string key/value metadata. |
| `deleteAfterMinutes` | integer | No | Schedule automatic deletion after creation. |

```json
{
  "origin": 0,
  "status": 1,
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "description": "Clerk reports a firearm.",
  "notes": [],
  "communityUserIds": ["player-1234"],
  "metaData": {
    "source": "integration"
  }
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

local response = sonoran:createDispatchCallV2({
    serverId = 1,
    origin = 1,
    status = 1,
    priority = 1,
    block = '101',
    address = 'Alta Street',
    postal = '100',
    title = 'Structure Fire',
    code = 'FIRE',
    description = 'Visible smoke from the roof.',
    notes = {},
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

  const response = await instance.cad.createDispatchCallV2({
    serverId: 1,
    origin: 1,
    status: 1,
    priority: 1,
    block: '101',
    address: 'Alta Street',
    postal: '100',
    title: 'Structure Fire',
    code: 'FIRE',
    description: 'Visible smoke from the roof.',
    notes: [],
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "origin": 0,
  "status": 1,
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "description": "Clerk reports a firearm.",
  "notes": [],
  "communityUserIds": ["player-1234"],
  "metaData": {
    "source": "integration"
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "origin": 0,
  "status": 1,
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "description": "Clerk reports a firearm.",
  "notes": [],
  "communityUserIds": [
    "player-1234"
  ],
  "metaData": {
    "source": "integration"
  }
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
  "origin": 0,
  "status": 1,
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "description": "Clerk reports a firearm.",
  "notes": [],
  "communityUserIds": ["player-1234"],
  "metaData": {
    "source": "integration"
  }
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "callId": 501,
  "origin": 0,
  "status": 1,
  "priority": 1,
  "block": "100",
  "address": "Mission Row",
  "postal": "9001",
  "title": "Armed Robbery",
  "code": "211",
  "primary": 12,
  "trackPrimary": false,
  "description": "Clerk reports a firearm.",
  "notes": [
    {
      "time": "2026-04-08T21:30:00Z",
      "label": "Sonoran CAD",
      "type": "text",
      "content": "Caller is hiding."
    }
  ],
  "idents": [
    12,
    18
  ],
  "metaData": {
    "source": "integration"
  },
  "updated": "2026-04-08T21:30:00Z"
}
```

## Enumeration Values

### CALL_STATUS

| Value | Description |
| --- | --- |
| `0` | `PENDING` |
| `1` | `ACTIVE` |
| `2` | `CLOSED` |

### CALL_ORIGIN

| Value | Description |
| --- | --- |
| `0` | `RADIO_DISPATCH` |
| `1` | `SELF_INITIATED` |
