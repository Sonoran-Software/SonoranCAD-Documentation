---
description: This event is sent when a unit toggles their panic status.
---

# Unit Panic

### EVENT_UNIT_PANIC

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_UNIT_PANIC",
    "data": [
        {
            "identId": 1, // Identifier ID
            "isPanic": true
        }
    ]
}
```
