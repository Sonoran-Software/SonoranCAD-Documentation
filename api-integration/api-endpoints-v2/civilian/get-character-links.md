---
description: Retrieve linked sync-character IDs for an account or API ID.
---

# Get Character Links

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/civilian/character-links`

Retrieve linked sync-character IDs for an account or linked API ID.

## Query Parameters

Provide exactly one of the following:

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | UUID | Sonoran CAD account UUID |
| `apiId` | string | API ID linked to a Sonoran CAD account |

## Response

Returns a JSON array of sync character IDs, with the selected sync character first when present.
