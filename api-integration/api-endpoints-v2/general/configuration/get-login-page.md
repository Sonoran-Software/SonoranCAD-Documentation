---
description: Retrieve public login-page community details by custom URL or community ID.
---

# Get Login Page

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/login-page`

Return public login-page details for a community. This endpoint does not require bearer authentication.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `communityId` | string | Optional | Use the community ID instead of `url`. Provide exactly one. |
| `url` | string | Optional | Use the community website or login URL instead of `communityId`. |

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

local response = sonoran:getLoginPageV2({
    communityId = 'YOUR_COMMUNITY_ID',
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

  const response = await instance.cad.getLoginPageV2({
    communityId: 'YOUR_COMMUNITY_ID',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/login-page?communityId=examplecad" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/login-page?communityId=examplecad", {
  method: "GET",
  headers: {
    Accept: "application/json",
  },
});

const data = await response.json();
console.log(data);
```
{% endtab %}

{% tab title="PowerShell" %}
```powershell
$headers = @{
  Accept = "application/json"
}

Invoke-RestMethod `
  -Method Get `
  -Uri "https://api.sonorancad.com/v2/general/login-page?communityId=examplecad" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "comId": "examplecad",
  "name": "Example CAD",
  "timezone": "America/Phoenix",
  "customLoginUrl": "https://portal.examplecad.com/login"
}
```
