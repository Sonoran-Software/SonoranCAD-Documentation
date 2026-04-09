---
description: Check whether a community user ID is linked to an account.
---

# Check Community Link

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/links/check`

Resolve a `communityUserId` to the linked Sonoran CAD account UUID inside the authenticated community.

## Request Body

```json
{
  "communityUserId": "player_12345"
}
```

## Example Request

{% tabs %}
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

  const response = await instance.cad.checkCommunityLinkV2({
    communityUserId: 'player_12345',
  });
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/links/check" \
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
const response = await fetch("https://api.sonorancad.com/v2/general/links/check", {
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
  -Uri "https://api.sonorancad.com/v2/general/links/check" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

Linked:

```json
{
  "communityUserId": "player_12345",
  "linked": true,
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
```

Not linked:

```json
{
  "communityUserId": "player_12345",
  "linked": false,
  "accountUuid": null
}
```
