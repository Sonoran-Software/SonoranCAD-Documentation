---
description: Delete an identifier from an account.
---

# Delete Identifier

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/identifiers/{identId}`

Delete an identifier from an account.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | string (uuid) | Sonoran CAD account UUID. |
| `identId` | integer | Identifier ID. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12", {
  method: "DELETE",
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
  -Method Delete `
  -Uri "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/identifiers/12" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "identId": 12,
  "serverId": 1
}
```
