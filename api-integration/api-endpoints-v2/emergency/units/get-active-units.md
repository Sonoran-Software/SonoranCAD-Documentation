---
description: Retrieve active emergency units for a configured server.
---

# Get Active Units

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units`

Retrieve active units for the specified CAD server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `includeOffline` | boolean | `false` | Include offline units |
| `onlyUnits` | boolean | `true` | Exclude active dispatchers |
| `limit` | integer | `100` | Maximum records returned |
| `offset` | integer | `0` | Records to skip |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/units?includeOffline=false&onlyUnits=true&limit=100&offset=0" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns a JSON array of unit objects.
