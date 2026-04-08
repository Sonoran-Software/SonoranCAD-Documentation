---
description: v2 general record and template endpoints.
---

# Records

These endpoints manage custom record templates, record creation, record updates, record deletion, and draft payload generation.

## Endpoints

| Method | Route | Description |
| --- | --- | --- |
| `GET` | `/v2/general/templates` | Retrieve all record templates for the authenticated community |
| `GET` | `/v2/general/templates/{recordTypeId}` | Retrieve one record template by record type ID |
| `POST` | `/v2/general/records` | Create a record from a full record payload or template replacement values |
| `PATCH` | `/v2/general/records/{recordId}` | Update a record by record ID |
| `DELETE` | `/v2/general/records/{recordId}` | Remove a record by record ID |
| `POST` | `/v2/general/record-drafts` | Build a draft record from a template and optionally send it to an active account |

## Common Request Notes

- Bearer authentication is required for every endpoint on this page.
- Record create and update requests support either:
  - a full `record` object
  - `useDictionary` with template IDs and `replaceValues`
- Draft and create requests can target an account by `accountUuid` or `apiId`.

## Example Requests

```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/records" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "accountUuid": "00000000-0000-0000-0000-000000000000",
    "useDictionary": true,
    "recordTypeId": 12,
    "replaceValues": {
      "{{plate}}": "ABC123"
    }
  }'
```

```bash
curl --request PATCH \
  --url "https://api.sonorancad.com/v2/general/records/451" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "useDictionary": true,
    "templateId": 12,
    "replaceValues": {
      "{{plate}}": "XYZ987"
    }
  }'
```

## Response Shape

Template endpoints return template objects. Record endpoints return the created or updated record payload, or the removed `recordId` for deletes.
