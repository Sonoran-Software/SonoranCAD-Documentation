---
description: Set the selected character for a community user or account.
---

# Set Selected Character

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/civilian/selected-character`

Set the selected character or selected sync character for an account.

## Request Body

Provide exactly one of `communityUserId` or `accountUuid`.

```json
{
  "communityUserId": "player-1234",
  "characterId": "1042"
}
```

`characterId` may be a numeric Sonoran character ID or a sync character string ID.

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/civilian/selected-character" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "characterId": "1042"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/selected-character", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "characterId": "1042"
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
  "characterId": "1042"
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/civilian/selected-character" `
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
  "characterId": "citizen:1234"
}
```
