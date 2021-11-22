---
description: >-
  View all of our API endpoints, learn about our data structuring, and integrate
  your framework with Sonoran CAD.
---

# API Endpoints

{% hint style="info" %}
API endpoints are not enabled with the free version of Sonoran CAD.\
For more information, see our [pricing](../../../pricing/faq/) or view how to check your community [limits](../../../tutorials/getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Available API Endpoints

### Emergency Endpoints

View all emergency endpoints including unit actions, emergency calls, dispatching, and more!

{% content-ref url="emergency/" %}
[emergency](emergency/)
{% endcontent-ref %}

### Civilian Endpoints

View all civilian endpoints including creating new characters, modifying licenses, vehicle registrations, and more!

{% content-ref url="civilian/" %}
[civilian](civilian/)
{% endcontent-ref %}

### General Endpoints

View all general endpoints for user account actions, administrative actions, and more!

{% content-ref url="general/" %}
[general](general/)
{% endcontent-ref %}

## API Code Examples

### Javascript

Javascript can be used in Discord bots, FiveM scripts, and more.

This example makes a [unit panic request](emergency/unit-panic.md) based on a unit's API ID. This uses the [Axios library](https://www.npmjs.com/package/axios) to help make the HTTP POST request.

The server response is then logged to console.

```javascript
// Import Axios library
// https://www.npmjs.com/package/axios
// Install command: `npm i axios` 
import axios from 'axios';
// Set the API URL (CAD backend)
let baseURL = 'https://api.sonorancad.com';
// Set the `api` object to be used
let api = axios.create({ baseURL });

// Format the POST body data
// https://info.sonorancad.com/sonoran-cad/api-integration/api-endpoints/emergency/unit-panic
const data = {
  id: 'YOUR_COMMUNITY_ID',
  key: 'YOUR_API_KEY',
  type: 'UNIT_PANIC',
  data: [
    {
      apiId: "STEAM:5678",
      isPanic: true,
    }
  ],
};

// Send the POST request
//  Format the data to JSON
api.post('/emergency/unit_panic', JSON.stringify(data))
  .then((response) => {
    // Response back from the backend
    console.log(response);
  })
  .catch((err) => {
    // Error response back from the backend
    console.log(err);
 });
```

