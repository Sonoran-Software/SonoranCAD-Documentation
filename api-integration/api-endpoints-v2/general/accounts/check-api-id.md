---
description: Check whether an API ID is linked to an account in the authenticated community.
---

# Check API ID

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/general/api-ids/{apiId}`

Resolve an API ID to a Sonoran CAD username and account UUID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `apiId` | string | External API ID, such as a Steam hex. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/api-ids/steam:110000112345678" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/api-ids/steam:110000112345678", {
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
  -Uri "https://api.sonorancad.com/v2/general/api-ids/steam:110000112345678" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "apiId": "steam:110000112345678",
  "username": "ExampleUser",
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
```
