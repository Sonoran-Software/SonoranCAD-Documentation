---
description: Link a sync-character ID to a community user, account, or API ID.
---

# Add Character Link

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/civilian/character-links/{syncId}`

Link a sync-character ID to a community user, account, or API ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `syncId` | string | Database Sync character identifier. |

## Request Body

Provide exactly one of `communityUserId`, `accountUuid`, or `apiId`.

```json
{
  "communityUserId": "player-1234"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/civilian/character-links/citizen:1234" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/character-links/citizen:1234", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
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
  "communityUserId": "player-1234"
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/civilian/character-links/citizen:1234" `
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
  "syncId": "citizen:1234",
  "action": "ADD"
}
```
