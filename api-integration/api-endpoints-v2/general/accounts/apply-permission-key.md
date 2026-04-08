---
description: Apply a permission key to an account resolved by API ID.
---

# Apply Permission Key

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/permission-keys/applications`

Apply a Sonoran CAD permission key to the account linked to an API ID.

## Request Body

```json
{
  "apiId": "steam:110000112345678",
  "permissionKey": "YOUR_PERMISSION_KEY"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/permission-keys/applications" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "apiId": "steam:110000112345678",
  "permissionKey": "YOUR_PERMISSION_KEY"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/permission-keys/applications", {
  method: "POST",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "apiId": "steam:110000112345678",
  "permissionKey": "YOUR_PERMISSION_KEY"
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
  "permissionKey": "YOUR_PERMISSION_KEY"
}
'@

Invoke-RestMethod `
  -Method Post `
  -Uri "https://api.sonorancad.com/v2/general/permission-keys/applications" `
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
  "username": "ExampleUser",
  "message": "Permission key applied.",
  "permissions": {
    "police": true,
    "dispatch": true,
    "liveMap": true,
    "adminInGameIntegration": true
  }
}
```
