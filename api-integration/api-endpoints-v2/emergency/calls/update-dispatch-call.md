---
description: Update editable fields on an existing dispatch call.
---

# Update Dispatch Call

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/dispatch-calls/{callId}`

Update one or more editable fields on an existing dispatch call.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |
| `callId` | integer | Dispatch or 911 call ID. |

## Request Body

Send only the fields you want to update.

```json
{
  "status": 1,
  "postal": "9002",
  "trackPrimary": true
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

local response = sonoran:updateDispatchCallV2(501, {
    serverId = 1,
    description = 'Caller confirmed the fire has spread to the garage.',
    postal = '100',
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

  const response = await instance.cad.updateDispatchCallV2(501, {
    serverId: 1,
    description: 'Caller confirmed the fire has spread to the garage.',
    postal: '100',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "status": 1,
  "postal": "9002",
  "trackPrimary": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "status": 1,
  "postal": "9002",
  "trackPrimary": true
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
  "status": 1,
  "postal": "9002",
  "trackPrimary": true
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/dispatch-calls/501" `
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
  "postal": "9002",
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
