---
description: Build a draft record from a template and optionally send it to an active account.
---

# Send Draft

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/record-drafts`

> **Rate limit:** `10 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Build a draft record from a template and, when a target account is provided, send it to the user over the active websocket session.

## Request Body

You can optionally route the draft to a connected user with `communityUserId` or `accountUuid`.

```json
{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "communityUserId": "player-1234"
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

local response = sonoran:sendRecordDraftV2({
    recordTypeId = 1,
    replaceValues = { firstName = 'John', lastName = 'Doe' },
    apiId = '1234567890',
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

  const response = await instance.cad.sendRecordDraftV2({
    recordTypeId: 1,
    replaceValues: { firstName: 'John', lastName: 'Doe' },
    apiId: '1234567890',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/record-drafts" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "communityUserId": "player-1234"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/record-drafts", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "communityUserId": "player-1234"
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
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "communityUserId": "player-1234"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/record-drafts" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "recordTypeId": 12,
  "id": 0,
  "name": "Incident Report",
  "type": 9,
  "sections": [
    {
      "category": 0,
      "label": "Report Details",
      "fields": [
        {
          "label": "Case Number",
          "value": "",
          "uid": "case_number"
        }
      ]
    }
  ]
}
```
