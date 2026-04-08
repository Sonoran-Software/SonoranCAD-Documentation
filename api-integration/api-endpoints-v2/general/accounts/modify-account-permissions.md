---
description: Update account permissions and account status for a community user.
---

# Modify Account Permissions

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/general/accounts/permissions`

Update permissions for a community account and optionally set its active status.

## Request Body

Provide exactly one account identifier using `accountUuid`, `apiId`, or `username`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/general/accounts/permissions" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/accounts/permissions", {
  method: "PATCH",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "add": [
    "POLICE",
    "DISPATCH"
  ],
  "active": true
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
  "accountUuid": "00000000-0000-0000-0000-000000000000",
  "add": ["POLICE", "DISPATCH"],
  "active": true
}
'@

Invoke-RestMethod `
  -Method Patch `
  -Uri "https://api.sonorancad.com/v2/general/accounts/permissions" `
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
  "permissions": {
    "police": true,
    "dispatch": true,
    "liveMap": true,
    "adminInGameIntegration": true
  },
  "active": true
}
```
