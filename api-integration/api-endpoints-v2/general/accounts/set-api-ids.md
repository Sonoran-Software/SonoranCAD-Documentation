---
description: Replace or append API IDs for a community account.
---

# Set API IDs

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/api-ids`

Set or append API IDs for a community account.

## Request Body

Provide exactly one of `communityUserId`, `username`, or `accountUuid`.

```json
{
  "communityUserId": "player-1234",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
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

local response = sonoran:setApiIdsV2({
    accountUuid = '00000000-0000-0000-0000-000000000000',
    apiIds = {'1234567890', '0987654321'},
    pushNew = true,
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

  const response = await instance.cad.setApiIdsV2({
    accountUuid: '00000000-0000-0000-0000-000000000000',
    apiIds: ['1234567890', '0987654321'],
    pushNew: true,
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/general/api-ids" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/api-ids", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "apiIds": [
    "steam:110000112345678",
    "license:abc123"
  ],
  "pushNew": true
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
  "communityUserId": "player-1234",
  "apiIds": ["steam:110000112345678", "license:abc123"],
  "pushNew": true
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/general/api-ids" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "apiIds": [
    "steam:110000112345678"
  ],
  "pushNew": true
}
```
