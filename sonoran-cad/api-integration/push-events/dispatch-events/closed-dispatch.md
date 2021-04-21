---
description: >-
  The dispatch event sends a notice to your community when a dispatch call is
  closed.
---

# Closed Dispatch

### EVENT\_DISPATCH\_CLOSED POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_DISPATCH_CLOSED",
    "data": {
        "callId": -1,
    }
}
```

