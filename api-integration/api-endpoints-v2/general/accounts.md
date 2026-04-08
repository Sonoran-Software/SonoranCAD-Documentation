---
description: v2 general account and identity endpoints.
---

# Accounts

These endpoints handle account resolution, API IDs, permissions, account secrets, and connection-targeted actions.

## Endpoints

| Method | Route | Description |
| --- | --- | --- |
| `GET` | `/v2/general/api-ids/{apiId}` | Resolve an API ID to a username and account UUID |
| `POST` | `/v2/general/permission-keys/applications` | Apply a permission key to an account resolved by API ID |
| `POST` | `/v2/general/account-bans` | Kick or ban an account in the community |
| `PUT` | `/v2/general/api-ids` | Replace or append API IDs for an account |
| `GET` | `/v2/general/accounts/account` | Retrieve a single account by `accountUuid`, `apiId`, or `username` |
| `GET` | `/v2/general/accounts` | Retrieve paginated community accounts |
| `PATCH` | `/v2/general/accounts/permissions` | Update account permissions and optional active status |
| `POST` | `/v2/general/secrets/verify` | Resolve an account from a Sonoran CAD account secret |
| `POST` | `/v2/general/photos` | Send a photo URL to active connections for an API ID |

## Common Request Notes

- Bearer authentication is required for every endpoint on this page.
- When an endpoint accepts an account identifier, provide exactly one supported identifier.
- Validation failures return structured `application/problem+json` responses.

## Example Requests

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/general/api-ids/steam:110000112345678" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/general/accounts/permissions" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "accountUuid": "00000000-0000-0000-0000-000000000000",
    "add": ["POLICE", "DISPATCH"],
    "active": true
  }'
```

## Response Shape

Responses vary by endpoint, but typically return the resolved `accountUuid`, relevant status information, and any updated permission or identity data.
