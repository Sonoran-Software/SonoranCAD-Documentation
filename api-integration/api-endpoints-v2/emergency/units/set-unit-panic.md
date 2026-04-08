---
description: Set panic state for one or more identifiers.
---

# Set Unit Panic

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/units/panic`

Set the panic state for one or more identifiers resolved by `accountUuid`, `apiId`, `apiIds`, or `identIds`.

## Request Body

```json
{
  "identIds": [15, 18],
  "isPanic": true
}
```

## Response

```json
{
  "updated": 2,
  "isPanic": true
}
```
