---
description: Create a custom blip.
---

# Create Blip

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/blips`

## Request Body

```json
{
  "coordinates": {
    "x": 441.2,
    "y": -981.9,
    "z": 0.0,
    "w": 0.0
  },
  "subType": "scene",
  "icon": "fa-circle",
  "color": "red",
  "tooltip": "Scene perimeter",
  "radius": 50.0,
  "data": [
    {
      "title": "Units",
      "text": "2"
    }
  ]
}
```
