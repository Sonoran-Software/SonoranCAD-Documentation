---
description: Retrieve the stored community plan version metadata associated with the authenticated API key.
---

# Get Version

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/version`

Return the stored plan version metadata resolved during API authentication.

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/version" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/version", {
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
  -Uri "https://api.sonorancad.com/v2/general/version" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "version": 2,
  "name": "PLUS"
}
```
