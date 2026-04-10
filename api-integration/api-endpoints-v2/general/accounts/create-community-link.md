---
description: Create a short-lived community user link code.
---

# Create Community Link

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/links`

Create a 4-character code for a `communityUserId`. The code is scoped to the authenticated community and expires after 10 minutes.

## Request Body

```json
{
  "communityUserId": "player_12345"
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

local response = sonoran:createCommunityLinkV2({
    communityUserId = 'player_12345',
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

  const response = await instance.cad.createCommunityLinkV2({
    communityUserId: 'player_12345',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/links" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player_12345"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/links", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    communityUserId: "player_12345",
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
  "communityUserId": "player_12345"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/links" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "code": "A7K2",
  "communityUserId": "player_12345",
  "communityUuid": "00000000-0000-0000-0000-000000000000",
  "expiresAt": "2026-04-09T19:25:00Z",
  "expiresInSeconds": 600
}
```

## Linking Account

Once a link code is created, direct the user to `sonorancad.com/id?code=ENTERCODEHERE`.

If the user is not logged in, they will be automatically redirected. The 4-digit code will be automatically entered into the ID page, processed, and the user's `communityUserId` will be linked to the community account.

Once linked, the `communityUserId` parameter can be used with any applicable v2 API endpoint.

<div><figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure> <figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure></div>
