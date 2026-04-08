---
description: Remove a custom record by record ID.
---

# Delete Record

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/general/records/{recordId}`

Delete a custom record by its record ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `recordId` | integer | Record ID. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/general/records/451" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/general/records/451", {
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
  -Uri "https://api.sonorancad.com/v2/general/records/451" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "recordId": 451
}
```
