---
description: >-
  Sonoran CAD pushes event data to your community for further integration
  possibilities. Learn more below!
---

# Push Events

{% hint style="warning" %}
All push events require the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
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

## Web Server Example

### Javascript

You can create your own web server to listen and receive Sonoran CAD events. This could be on a Discord bot, an in-game script, etc.

In addition, you may already be receiving these events in your integration framework. The integration framework can be configured to "[forward](../../../integration-plugins/integration-plugins/framework-installation.md#5.-configure-push-events)" all push events received to another custom webserver, like the example shown below. Simply set `enablePushEventForwarding` to `true` and `pushEventForwardUrl` to your webserver's http://IP:Port.

```javascript
// ----------------------------
// Webserver Handling
//  Description: Create web server and listen to CAD push events locally
// ----------------------------

// Use the JS HTTP library to create a new webserver
//    Pass any traffic to the 'handler' function
let server = require('http').createServer(handler);

// Sonoran CAD community API key
//  Used to authenticate traffic received
const API_KEY = "YOUR_API_KEY";

// Start the webserver on a specific port
//    Ensure you have this port OPEN on your external IP
//    https://portchecker.co/
let port = 30150;
server.listen(port);

// Webserver traffic handler
async function handler (req, res) {
  let data = '';            // Parsed JSON data
  let success = false;      // Successful parsing/handling
  let responseMessage = ""; // Response text back to server
  
  // Only handle POST requests
  // Only handle requests sent to /sonorancad/event (CAD push events)
  if (req.method === "POST" && req.url === '/sonorancad/event') {
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
      if (data.key === API_KEY) {
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
```
