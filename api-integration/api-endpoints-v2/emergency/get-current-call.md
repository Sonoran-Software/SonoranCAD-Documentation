---
description: Retrieve the selected identifier and active call assignment for a Sonoran CAD account with the v2 API.
---

# Get Current Call

<mark style="color:green;">`GET`</mark> `https://api.sonorancad.com/v2/emergency/accounts/{accountUuid}/current-call`

Retrieve the authenticated account's selected identifier ID and current call assignment.

## Authentication

This endpoint requires the `Authorization: Bearer YOUR_API_KEY` header.

## Path Parameters

| Name | Type | Description |
| --- | --- | --- |
| `accountUuid` | UUID | The Sonoran CAD account UUID |

## Example Request

```bash
curl --request GET \
  --url "https://api.sonorancad.com/v2/emergency/accounts/00000000-0000-0000-0000-000000000000/current-call" \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Successful Response

```json
{
  "identId": 42,
  "callId": 1007
}
```

## Notes

* `identId` is the account's currently selected identifier ID
* `callId` is the active dispatch call ID, or `-1` if the selected identifier is not attached to a call

## Error Responses

| Status | Description |
| --- | --- |
| `400` | Invalid `accountUuid` format |
| `401` | Missing or invalid bearer authentication |
| `500` | The backend could not retrieve the account's current call information |
