---
description: >-
  The EVENT_UNIT_DETACH push event is sent when an identifier/unit is attached
  to a new call.
---

# Detach Unit

## EVENT\_UNIT\_DETACH Post

```javascript
{
  "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
  "type": "EVENT_DISPATCH_UNIT_DETACH",
  "data": {
    "ident": 1,          // Identifier/Unit ID
    "callId": 123        // Dispatch Call ID
  }
}
        
```

The `ident` is a unique number specifying the a unit "identifier" being attached to a call.

The `callId` represents the specific dispatch call they are being removed from.

