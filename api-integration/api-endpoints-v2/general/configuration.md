---
description: v2 general configuration and utility endpoints.
---

# Configuration

These endpoints manage community-wide configuration, utility actions, and the public login-page lookup.

## Endpoints

| Method | Route | Description |
| --- | --- | --- |
| `PUT` | `/v2/general/penal-codes` | Replace the community penal code configuration |
| `POST` | `/v2/general/servers/{serverId}/heartbeat` | Publish a player-count heartbeat for a configured server |
| `GET` | `/v2/general/version` | Return the stored plan version metadata resolved for the API key |
| `GET` | `/v2/general/servers` | Retrieve the configured community server list |
| `PUT` | `/v2/general/servers` | Replace the configured community server list |
| `POST` | `/v2/general/servers/{serverId}/street-sign-auth` | Validate smart-sign access for a configured server and source IP |
| `PUT` | `/v2/general/postals` | Replace the community postal configuration |
| `GET` | `/v2/general/info` | Retrieve authenticated community metadata and shared code lists |
| `GET` | `/v2/general/login-page` | Retrieve public login-page details by custom URL or community ID |

## Common Request Notes

- Bearer authentication is required for every endpoint on this page except `GET /v2/general/login-page`.
- Server-scoped routes require a configured `serverId` that belongs to the authenticated API key.
- Validation and server authorization failures return structured `application/problem+json` responses.

## Example Requests

```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/servers/1/heartbeat" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "playerCount": 42
  }'
```

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/login-page?communityId=examplecad"
```

## Response Shape

Configuration endpoints return either saved configuration payloads, utility status data, or community metadata depending on the route.
