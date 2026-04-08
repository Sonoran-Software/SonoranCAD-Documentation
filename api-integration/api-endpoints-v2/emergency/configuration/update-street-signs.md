---
description: Update text on one or more configured street signs.
---

# Update Street Signs

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/street-signs`

## Request Body

```json
{
  "ids": [1, 2],
  "text1": "Mission Row",
  "text2": "Alta St",
  "text3": "Integrity Way"
}
```
