---
description: Unlink a sync-character ID from an account or API ID.
---

# Remove Character Link

<mark style="color:red;">`DELETE`</mark> `https://api.sonorancad.com/v2/civilian/character-links/{syncId}`

Unlink a sync-character ID from an account or API ID.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `syncId` | string | Database Sync character identifier. |

## Request Body

Provide exactly one of `accountUuid` or `apiId`.

```json
{
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
```

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request DELETE \
  --url "https://api.sonorancad.com/v2/civilian/character-links/citizen:1234" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json" \
  --header "Content-Type: application/json" \
  --data '{
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/civilian/character-links/citizen:1234", {
  method: "DELETE",
  headers: {
    Authorization: "Bearer YOUR_API_KEY",
    Accept: "application/json",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
  "accountUuid": "00000000-0000-0000-0000-000000000000"
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
  "accountUuid": "00000000-0000-0000-0000-000000000000"
}
'@

Invoke-RestMethod `
  -Method Delete `
  -Uri "https://api.sonorancad.com/v2/civilian/character-links/citizen:1234" `
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
  "syncId": "citizen:1234",
  "action": "REMOVE"
}
```
