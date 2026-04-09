---
description: Remove a character by character ID.
---

# Delete Character

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/civilian/characters/{characterId}`

Remove a Sonoran CAD character by character ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `characterId` | integer | Character record ID. |

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

  const response = await instance.cad.removeCharacterV2(42);
  console.log(response);
})();
```
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/civilian/characters/2451" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/characters/2451", {
  method: "DELETE",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
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
  Authorization = "Bearer YOUR_API_KEY"
  Accept = "application/json"
}

Invoke-RestMethod `
  -Method Delete `
  -Uri "https://api.sonorancad.com/v2/civilian/characters/2451" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "characterId": 2451
}
```
