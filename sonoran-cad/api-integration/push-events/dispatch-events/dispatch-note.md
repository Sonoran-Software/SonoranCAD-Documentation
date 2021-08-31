---
description: This push event sends data when a note is added to an existing dispatch call.
---

# Dispatch Note

### EVENT\_DISPATCH\_NOTE POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_DISPATCH_NOTE",
    "data": {
        "callId": -1,
        "note": "Test 123"
    }
}
```

