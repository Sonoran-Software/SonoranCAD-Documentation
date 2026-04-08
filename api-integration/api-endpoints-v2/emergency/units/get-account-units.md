---
description: Retrieve units for a specific account on a configured server.
---

# Get Account Units

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/accounts/{accountUuid}/units`

Retrieve units for a specific account on a configured server.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured Sonoran CAD server ID |
| `accountUuid` | UUID | Sonoran CAD account UUID |

## Query Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `onlyOnline` | boolean | `true` | Only return online units |
| `onlyUnits` | boolean | `true` | Exclude dispatch identifiers |
| `limit` | integer | `100` | Maximum records returned |
| `offset` | integer | `0` | Records to skip |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/servers/1/accounts/00000000-0000-0000-0000-000000000000/units?onlyOnline=true" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

```json
{
  "units": []
}
```
