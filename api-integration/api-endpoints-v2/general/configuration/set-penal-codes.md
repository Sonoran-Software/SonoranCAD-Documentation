---
description: Replace the community penal code configuration.
---

# Set Penal Codes

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/general/penal-codes`

Replace the community penal code configuration.

## Request Body

```json
{
  "codes": []
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PUT \
  --url "https://api.sonorancad.com/v2/general/penal-codes" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "codes": []
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/penal-codes", {
  method: "PUT",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "codes": []
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
  "codes": []
}
'@

Invoke-RestMethod `
  -Method Put `
  -Uri "https://api.sonorancad.com/v2/general/penal-codes" `
  -Headers $headers `
  -Body $body
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "updated": 1
}
```
