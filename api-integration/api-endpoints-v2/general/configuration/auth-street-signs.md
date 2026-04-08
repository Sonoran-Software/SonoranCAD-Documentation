---
description: Validate a street-sign request against the configured server ID and source IP.
---

# Auth Street Signs

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/servers/{serverId}/street-sign-auth`

Validate that the requesting IP address matches the configured smart-sign server entry.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `serverId` | integer | Configured server ID for this API key |

## Example Request

```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/servers/1/street-sign-auth" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Response

Returns `authorized: true` when the server ID and requesting IP match the configured server entry.
