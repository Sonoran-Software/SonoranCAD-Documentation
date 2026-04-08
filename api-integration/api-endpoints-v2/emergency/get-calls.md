---
description: Retrieve active dispatch calls, emergency calls, and closed dispatch calls with the Sonoran CAD v2 API.
---

# Get Calls

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/calls`

Retrieve active dispatch calls, active emergency calls, and previously closed dispatch calls for a configured server.

## Authentication

This endpoint requires the `Authorization: Bearer YOUR_API_KEY` header.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | The configured Sonoran CAD server ID |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `closedLimit` | integer | `10` | Maximum number of closed dispatch calls returned |
| `closedOffset` | integer | `0` | Offset used to paginate closed dispatch calls |
| `type` | integer | `100` | Filter by call type: dispatch only, emergency only, or both |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/calls?closedLimit=25&closedOffset=0&type=100" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Successful Response

```json
{
  "activeCalls": [],
  "emergencyCalls": [],
  "closedCalls": [],
  "closedCallCount": 0
}
```

## Object Notes

* `activeCalls` contains dispatch call objects
* `emergencyCalls` contains 911/emergency call objects
* `closedCalls` contains closed dispatch call objects
* `closedCallCount` is the total number of closed dispatch calls available for pagination

## Error Responses

| Status | Description |
| --- | --- |
| `400` | Invalid query parameter values |
| `401` | Missing or invalid bearer authentication |
| `404` | The `serverId` does not belong to the authenticated community |
| `500` | The backend could not retrieve call data |

## Enumeration Values

### Call Type

| Integer | Meaning |
| --- | --- |
| `0` | DISPATCH_CALL |
| `1` | EMERGENCY_CALL |
| `100` | SEARCH_ALL |

### Call Status

| Integer | Meaning |
| --- | --- |
| `0` | PENDING |
| `1` | ACTIVE |
| `2` | CLOSED |
