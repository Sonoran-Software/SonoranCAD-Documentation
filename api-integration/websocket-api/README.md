---
description: >-
  Access the Sonoran CAD API via WSS to reduce authentication overhead for
  frequent API calls.
---

# Websocket API

Use the websocket API for persistent, low-overhead integration traffic.

Current websocket API features include:

* Authenticating once and reusing the session for repeated calls
* Sending frequent `unitLocation` updates for the live map
* Receiving Sonoran CAD `pushEvent` messages for a specific `serverId`

