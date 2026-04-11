---
description: Create a new 911 call for a server.
---

# Create 911 Call

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/calls/911`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Create a new 911 call for a server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Request Body

```json
{
  "isEmergency": true,
  "caller": "911 Caller",
  "location": "Alta St / Integrity Way",
  "description": "Shots fired",
  "deleteAfterMinutes": 15,
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

local response = sonoran:createEmergencyCallV2({
    serverId = 1,
    isEmergency = true,
    caller = 'John Doe',
    location = '101 Alta Street',
    description = 'Structure fire with visible smoke.',
    deleteAfterMinutes = 30,
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

  const response = await instance.cad.createEmergencyCallV2({
    serverId: 1,
    isEmergency: true,
    caller: 'John Doe',
    location: '101 Alta Street',
    description: 'Structure fire with visible smoke.',
    deleteAfterMinutes: 30,
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/calls/911" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "isEmergency": true,
  "caller": "911 Caller",
  "location": "Alta St / Integrity Way",
  "description": "Shots fired",
  "deleteAfterMinutes": 15,
  "metaData": {
    "source": "integration"
  }
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/calls/911", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "isEmergency": true,
  "caller": "911 Caller",
  "location": "Alta St / Integrity Way",
  "description": "Shots fired",
  "deleteAfterMinutes": 15,
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
  "isEmergency": true,
  "caller": "911 Caller",
  "location": "Alta St / Integrity Way",
  "description": "Shots fired",
  "deleteAfterMinutes": 15,
  "metaData": {
    "source": "integration"
  }
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/calls/911" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "callId": 302,
  "isEmergency": true,
  "caller": "Jane Doe",
  "location": "Innocence Blvd",
  "description": "Medical emergency reported.",
  "metaData": {
    "phone": "555-0100"
  },
  "updated": "2026-04-08T21:31:00Z"
}
```
