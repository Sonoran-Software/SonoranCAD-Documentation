---
description: Kick or ban an account in the authenticated community.
---

# Kick Or Ban User

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/account-bans`

Kick an account from the community or apply a community ban.

## Request Body

Provide exactly one account identifier.

```json
{
  "apiId": "steam:110000112345678",
  "isBan": true
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/account-bans" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "apiId": "steam:110000112345678",
  "isBan": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/account-bans", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "apiId": "steam:110000112345678",
  "isBan": true
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
  "apiId": "steam:110000112345678",
  "isBan": true
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/account-bans" `
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
  "action": "ban",
  "message": "Account was banned."
}
```
