---
description: v2 general lookup endpoints.
---

# Lookups

These endpoints search records by name or plate data, typed value lookups, and custom mapped fields.

## Endpoints

| Method | Route | Description |
| --- | --- | --- |
| `POST` | `/v2/general/lookups` | Search records by name and plate values |
| `POST` | `/v2/general/lookups/by-value` | Search records by `IDENT`, `NUMBER`, `ACCOUNT`, `SECRET`, and related typed values |
| `POST` | `/v2/general/lookups/custom` | Search records by a custom mapped lookup field |

## Common Request Notes

- Bearer authentication is required for every endpoint on this page.
- Lookup requests require a `types` array of record types to search.
- `notifyAccountUuid` or `notifyApiId` can be supplied on supported lookups to forward results to active websocket sessions.
- Invalid lookup values return structured validation errors instead of plain strings.

## Example Requests

```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/lookups" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "first": "John",
    "last": "Doe",
    "mi": "",
    "plate": "",
    "types": [7, 12],
    "partial": true
  }'
```

```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/lookups/by-value" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "searchType": "NUMBER",
    "value": "451",
    "types": [12]
  }'
```

## Response Shape

All lookup endpoints return a JSON array of matching record objects.
