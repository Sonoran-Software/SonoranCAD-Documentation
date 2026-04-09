---
description: Send a photo URL to active connections for a community user ID.
---

# Send Photo

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/photos`

Send a photo URL to every active connection linked to a community user ID.

## Request Body

Provide the target account with `communityUserId`.

```json
{
  "communityUserId": "player-1234",
  "url": "https://cdn.example.com/mugshots/example.png"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/photos" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "communityUserId": "player-1234",
  "url": "https://cdn.example.com/mugshots/example.png"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/photos", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "communityUserId": "player-1234",
  "url": "https://cdn.example.com/mugshots/example.png"
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
  "url": "https://cdn.example.com/mugshots/example.png"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/photos" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "communityUserId": "player-1234",
  "delivered": 1
}
```
