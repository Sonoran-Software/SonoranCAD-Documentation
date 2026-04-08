---
description: Resolve an account from a Sonoran CAD account secret.
---

# Verify Secret

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/secrets/verify`

Verify an account secret and return the matched account UUID.

## Request Body

```json
{
  "secret": "00000000-0000-0000-0000-000000000000"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/secrets/verify" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "secret": "00000000-0000-0000-0000-000000000000"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/secrets/verify", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "secret": "00000000-0000-0000-0000-000000000000"
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
  "secret": "00000000-0000-0000-0000-000000000000"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/secrets/verify" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "00000000-0000-0000-0000-000000000000": "11111111-2222-3333-4444-555555555555"
}
```
