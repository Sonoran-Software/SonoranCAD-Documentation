---
description: Retrieve active emergency units for a configured server.
---

# Get Active Units

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units`

Retrieve active units for the specified CAD server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `includeOffline` | boolean | `false` | Include offline identifiers in the response. |
| `onlyUnits` | boolean | `true` | When `true`, hides active dispatchers. |
| `limit` | integer | `100` | Maximum number of rows returned. |
| `offset` | integer | `0` | Number of rows to skip. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units?includeOffline=false&onlyUnits=true&limit=100&offset=0" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/units?includeOffline=false&onlyUnits=true&limit=100&offset=0", {
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
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/units?includeOffline=false&onlyUnits=true&limit=100&offset=0" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
[
  {
    "id": 12,
    "accId": "00000000-0000-0000-0000-000000000000",
    "status": 3,
    "isPanic": false,
    "location": "Mission Row PD",
    "coordinates": {
      "x": 123.45,
      "y": -456.78,
      "z": 32.1,
      "w": 180.0
    },
    "aop": "Los Santos",
    "data": {
      "unitNum": "A-10",
      "name": "John Doe",
      "district": "Los Santos",
      "department": "LSPD",
      "subdivision": "Patrol",
      "rank": "Officer",
      "group": "CAR-51",
      "page": 0,
      "apiIds": [
        "steam:110000112345678"
      ]
    },
    "isDispatch": false
  }
]
```

## Enumeration Values

### UNIT_STATUS

| Value | Description |
| --- | --- |
| `0` | `UNAVAILABLE` |
| `1` | `BUSY` |
| `2` | `AVAILABLE` |
| `3` | `ENROUTE` |
| `4` | `ON_SCENE` |
| `100` | `OFFLINE` |

### UNIT_PAGE

| Value | Description |
| --- | --- |
| `0` | `POLICE` |
| `1` | `FIRE` |
| `2` | `EMS` |
| `3` | `DISPATCH` |
| `-1` | `UNKNOWN` |
