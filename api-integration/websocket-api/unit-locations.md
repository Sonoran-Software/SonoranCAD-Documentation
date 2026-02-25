---
description: Update unit locations for the live map.
---

# Unit Locations

## Rate Limits

* Maximum of one request every 250ms
* Maximum of 25 unit update objects per request

## Websocket API

### Authentication Method

#### **Method:**

```
unitLocation
```

#### **Parameters:**

<table><thead><tr><th>Parameter</th><th>Type</th></tr></thead><tbody><tr><td><pre><code>data
</code></pre></td><td>Array of  <code>unitLocationObject</code></td></tr></tbody></table>

#### Structure unitLocationObject

```js
  {
    apiId: "SOME_API_ID",
    location: "US-101 / Exit 15",
    coordinates: { x: 123.45, y: 678.9, z: 21.0, w: 180.0 },
    peerId: "bodycam-1-123", // Used only for P2P bodycam streams
    vehicle: {
      model: 'https://example.com/model.obj', // S3 URL to a 3D map object
      zOffset: 0, // Offset model Z (height) on map
      lightZOffset: 0, // Offset light effect Z (height) on map
      sizeOffset: 0, // Increase/Decrease Size
      headingOffset: 0, // Offset heading direction for 3D model
      lights: false // Show emergency lights flashing on model
    }
  }
```

### Response

#### Success

```
{ success: boolean, error: string, count: number }
```

#### Error

```
- Unauthenticated: "Unauthenticated. Call authenticate first."
- Missing/empty array: "Missing unit location updates."
- Batch too large: "Too many unit updates in one call. Max is 25."
- Too fast: "UNIT_LOCATION updates are limited to every 200ms."
```

### Unit Location JS example (Node.js):

```js
setInterval(async () => {
  const updates = [
    {
      apiId: "OFFICER_API_ID_1",
      location: "Interstate 4 / Mile 228",
      position: { x: 8.5, y: 2.1, z: 0.0, w: 90.0 },
    },
  ];

  try {
    await connection.invoke("unitLocation", updates);
  } catch (err) {
    console.error("send failed:", err.message);
  }
}, 250);
```
