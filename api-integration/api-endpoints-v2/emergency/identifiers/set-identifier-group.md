---
description: Assign one or more identifiers to a group on a server.
---

# Set Identifier Group

<mark style="color:blue;">`PUT`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/identifier-groups/{groupName}`

Assign one or more identifiers to a group by `accountUuid`, `apiId`, `apiIds`, or `identIds`.

## Request Body

```json
{
  "identIds": [15, 18]
}
```
