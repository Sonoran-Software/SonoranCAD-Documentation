---
description: >-
  Sonoran CAD pushes event data to your community for further integration
  possibilities. Learn more below!
---

# Push Events

{% hint style="warning" %}
All push events require the **Plus **version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Configuring your Listener

### 1. Admin Panel Configuration

In the admin panel, navigate to: Advanced > In-Game Integration\
Expand the "Server Events and Integrated Live Map" section.

Enter your server's public IP address and your game server's port. Sonoran CAD will send events to `http://ip:gameport/sonorancad/event` **utilizing your existing game port**.

Push event configuration is covered as a part of the [framework installation](../../../integration-plugins/integration-plugins/framework-installation.md#5-configure-push-events).

## Developer Documentation

Many of our [integration plugins](../../../integration-plugins/integration-plugins/available-plugins/) rely on these push events for full functionality. Interested in developing your own plugins? Expand the push event and API endpoint documentation in the left side drawer.

## Webserver Example

### Javascript

You can create your own webserver to listen and receive Sonoran CAD events. This could be on a Discord bot, an in-game script, etc.

In addition, you may want to "intercept" these events with your own listener (a Discord bot as an example) and _then _forward them onto your in-game listener (like our [integration framework](../../../integration-plugins/integration-plugins/framework-installation.md)). For this, simply set your IP and game port&#x20;

```javascript
// ----------------------------
// Webserver Handling
//  Description: Create and listen to CAD push events locally
// ----------------------------

// Use the JS HTTP library to create a new webserver
//    Pass any traffic to the 'handler' function
let server = require('http').createServer(handler);
let port = 30150;

// Sonoran CAD community API key
//  Used to authenticate traffic received
const API_KEY = "YOUR_API_KEY";

// Forward push event traffic to another service or script
const FORWARD_TRAFFIC = true;
const FORWARD_ENDPOINT = "123.456.789:1234";

// Start the webserver on a specific port
//    Ensure you have this port OPEN on your external IP
//    https://portchecker.co/
server.listen(port);

// Webserver traffic handler
async function handler (req, res) {
  let data = '';            // Parsed JSON data
  let success = false;      // Successful parsing/handling
  let responseMessage = ""; // Response text back to server
  
  // Only handle POST requests
  if (req.method === "POST") {
    req.on('data', function(chunk) {
      // Read and piece each part of data together
      data += chunk;
    });

    // Once we've fully read the request
    req.on('end', async function() {
      // Parse data string to a local JSON object
      data = JSON.parse(data);
      
      // Authenticate data
      //  Sonoran CAD sends your API KEY with the POST data
      //  Check this here to prevent someone random sending you requests
      if (data.key === config.authKey) {
        // Switch Case: handle each event type
        switch (data.type) {
          case "EVENT_911":
            // New 911 call placed
            // Format: https://info.sonorancad.com/sonoran-cad/api-integration/push-events/event-911
            console.log(`New 911 from ${data.caller}`);
            break;
          default:
            // Push event type isn't handled here
            responseMessage = "Invalid Type";
            success = false;
            sendResponse(success);
            break;
        }
        
        // Handle push event traffic forwarding (to our game server or other endpoint)
        if (FORWARD_TRAFFIC) {
          forwardTraffic(data);
        }
      } else {
        // Server traffic didn't have the proper API key
        responseMessage = "Authentication Key Failed!";
        success = false;
        sendResponse(success);
      }
    });
  }

  // Send response back to server
  function sendResponse(success) {
    // Return an HTTP 200 or 400 based on `success` boolean
    const statusCode = success ? 200 : 400;
    // Set response headers
    res.writeHead(statusCode, {'Content-Type': 'text/plain'});
    // Return response
    res.end(responseMessage);
  }
}

// ----------------------------
// TRAFFIC FORWARDING
// Description: Some users may wish to listen to CAD push events on
//  their local web server (Discord bot or other external service) and
//  *then* forward them onto another service.
//  This allows push events to be received in multiple areas, both a
//  Discord bot AND the game server.
// ----------------------------
// Import Axios library
// https://www.npmjs.com/package/axios
// Install command: `npm i axios` 
import axios from 'axios';
// Set the `api` object to be used, sending to our gameserver/external service
let api = axios.create({ baseURL: FORWARD_ENDPOINT });

function forwardTraffic(data) {
  // Send the POST request
  //  Format the data to JSON
  api.post(FORWARD_ENDPOINT , JSON.stringify(data))
    .then((response) => {
      // Response back from the server
      console.log(response);
    })
    .catch((err) => {
      // Error response back from the server
      console.log(err);
   });
}
```
