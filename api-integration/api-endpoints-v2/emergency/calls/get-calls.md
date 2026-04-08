---
description: Retrieve active, emergency, and closed calls for a server.
---

# Get Calls

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/calls`

Retrieve dispatch calls, emergency calls, and recent closed calls.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID. |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `closedLimit` | integer | `10` | Maximum number of closed dispatch calls returned. |
| `closedOffset` | integer | `0` | Number of closed calls to skip. |
| `type` | integer | `100` | Call table type filter. See `CALL_TABLE_TYPE` below. |

## Example Request

{% tabs %}
{% tab title="cURL" %}
```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/calls?closedLimit=10&closedOffset=0&type=100" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Accept: application/json"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch("https://api.sonorancad.com/v2/emergency/servers/1/calls?closedLimit=10&closedOffset=0&type=100", {
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
  -Uri "https://api.sonorancad.com/v2/emergency/servers/1/calls?closedLimit=10&closedOffset=0&type=100" `
  -Headers $headers
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return `application/json`.

```json
{
  "activeCalls": [
    {
      "callId": 501,
      "origin": 0,
      "status": 1,
      "priority": 1,
      "block": "100",
      "address": "Mission Row",
      "postal": "9001",
      "title": "Armed Robbery",
      "code": "211",
      "primary": 12,
      "trackPrimary": false,
      "description": "Clerk reports a firearm.",
      "notes": [
        {
          "time": "2026-04-08T21:30:00Z",
          "label": "Sonoran CAD",
          "type": "text",
          "content": "Caller is hiding."
        }
      ],
      "idents": [
        12,
        18
      ],
      "metaData": {
        "source": "integration"
      },
      "updated": "2026-04-08T21:30:00Z"
    }
  ],
  "emergencyCalls": [
    {
      "callId": 302,
      "isEmergency": true,
      "caller": "Jane Doe",
      "location": "Innocence Blvd",
      "description": "Medical emergency reported.",
      "metaData": {
        "phone": "555-0100"
      },
      "updated": "2026-04-08T21:31:00Z"
    }
  ],
  "closedCalls": [
    {
      "callId": 480,
      "origin": 0,
      "status": 2,
      "priority": 1,
      "block": "100",
      "address": "Mission Row",
      "postal": "9001",
      "title": "Armed Robbery",
      "code": "211",
      "primary": 12,
      "trackPrimary": false,
      "description": "Clerk reports a firearm.",
      "notes": [
        {
          "time": "2026-04-08T21:30:00Z",
          "label": "Sonoran CAD",
          "type": "text",
          "content": "Caller is hiding."
        }
      ],
      "idents": [
        12,
        18
      ],
      "metaData": {
        "source": "integration"
      },
      "updated": "2026-04-08T21:30:00Z"
    }
  ],
  "closedCallCount": 18
}
```

## Enumeration Values

### CALL_TABLE_TYPE

| Value | Description |
| --- | --- |
| `0` | `DISPATCH_CALL` |
| `1` | `EMERGENCY_CALL` |
| `100` | `SEARCH_ALL` |

### CALL_STATUS

| Value | Description |
| --- | --- |
| `0` | `PENDING` |
| `1` | `ACTIVE` |
| `2` | `CLOSED` |

### CALL_ORIGIN

| Value | Description |
| --- | --- |
| `0` | `RADIO_DISPATCH` |
| `1` | `SELF_INITIATED` |
