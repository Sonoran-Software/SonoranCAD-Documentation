---
description: Retrieve active units for a specific configured server by using the Sonoran CAD v2 API.
---

# Get Active Units

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units`

Retrieve active units for the specified CAD server.

## Authentication

This endpoint requires the `Authorization: Bearer YOUR_API_KEY` header.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | The configured Sonoran CAD server ID |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `includeOffline` | boolean | `false` | Include offline units in the response |
| `onlyUnits` | boolean | `true` | Exclude active dispatchers from the response |
| `limit` | integer | `100` | Maximum number of units returned |
| `offset` | integer | `0` | Number of units to skip for pagination |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units?includeOffline=false&onlyUnits=true&limit=100&offset=0" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Successful Response

```json
[
  {
    "id": 15,
    "accId": "00000000-0000-0000-0000-000000000000",
    "status": 2,
    "isPanic": false,
    "location": "1234 E. Test Ave",
    "coordinates": {
      "x": 0.0,
      "y": 0.0
    },
    "aop": "South District",
    "data": {
      "apiId1": "STEAM:1234",
      "apiId2": "DISCORD:1234",
      "unitNum": "A-10",
      "name": "John Doe",
      "district": "Maricopa County",
      "department": "MCSO",
      "subdivision": "Patrol",
      "rank": "Deputy",
      "group": "CAR 51"
    },
    "isDispatch": false
  }
]
```

## Error Responses

| Status | Description |
| --- | --- |
| `400` | Invalid query parameter values |
| `401` | Missing or invalid bearer authentication |
| `404` | The `serverId` does not belong to the authenticated community |
| `500` | The backend could not retrieve unit data |

## Enumeration Values

The `status` field uses the standard Sonoran CAD unit status enumeration values.

| Integer | Status |
| --- | --- |
| `0` | UNAVAILABLE |
| `1` | BUSY |
| `2` | AVAILABLE |
| `3` | ENROUTE |
| `4` | ON_SCENE |
