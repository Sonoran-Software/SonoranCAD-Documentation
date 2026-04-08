---
description: Update live map location data for one or more units.
---

# Update Unit Locations

<mark style="color:yellow;">`PATCH`</mark> `https://api.sonorancad.com/v2/emergency/servers/{serverId}/unit-locations`

Queue and broadcast one or more unit location updates.

## Request Body

```json
{
  "updates": [
    {
      "apiId": "steam:110000112345678",
      "location": "Mission Row",
      "coordinates": {
        "x": 441.2,
        "y": -981.9,
        "z": 30.7,
        "w": 90.0
      },
      "peerId": "peer-1",
      "vehicle": {
        "model": "police3",
        "headingOffset": 0
      }
    }
  ]
}
```

## Response

```json
{
  "updated": 1
}
```
