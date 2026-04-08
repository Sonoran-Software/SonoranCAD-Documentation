---
description: Build a draft record from a template and optionally send it to an active account.
---

# Send Draft

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/record-drafts`

Build a draft record from a template and, when a target account is provided, send it to the user over the active websocket session.

## Request Body

```json
{
  "recordTypeId": 12,
  "replaceValues": {
    "{{plate}}": "ABC123"
  },
  "apiId": "steam:110000112345678"
}
```

## Response

Returns the generated draft record object.
