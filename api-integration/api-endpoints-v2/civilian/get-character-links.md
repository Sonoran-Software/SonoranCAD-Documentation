---
description: Retrieve linked sync-character IDs for a community user or account.
---

# Get Character Links

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/civilian/character-links`

Retrieve linked sync-character IDs for a community user or account.

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `communityUserId` | string | Optional | Target in-game community user ID. Provide exactly one of `communityUserId` or `accountUuid`. |
| `accountUuid` | string (uuid) | Optional | Target account UUID. Provide exactly one of `communityUserId` or `accountUuid`. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/civilian/character-links?communityUserId=player-1234" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/character-links?communityUserId=player-1234", {
  method: "GET",
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
  -Method Get `
  -Uri "https://api.sonorancad.com/v2/civilian/character-links?communityUserId=player-1234" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
  "citizen:1234",
  "citizen:5678"
]
```
