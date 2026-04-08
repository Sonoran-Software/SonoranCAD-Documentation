---
description: Retrieve authenticated community metadata and shared codes.
---

# Get Info

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/info`

Return the authenticated community UUID, community metadata, and shared code lists.

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/info" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/info", {
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
  -Uri "https://api.sonorancad.com/v2/general/info" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "uuid": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "community": {
    "comId": "examplecad",
    "name": "Example CAD",
    "timezone": "America/Phoenix",
    "customLoginUrl": "https://portal.examplecad.com/login"
  },
  "codes": [
    "10-8",
    "10-23"
  ]
}
```
