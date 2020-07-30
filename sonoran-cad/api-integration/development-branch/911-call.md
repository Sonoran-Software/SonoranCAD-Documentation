---
description: >-
  This push event sends data when a new 911/emergency call is placed via API or
  in-CAD.
---

# 911 Call

### EVENT\_911 POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_911",
    "data": [
        {
            "callId": 1234,
            "isEmergency": true, // Emergency or Civil
            "caller": "John Doe",
            "location": "1234 E Hawick Ave",
            "description": "This is a 911 call!"
        }
    ]
}
```

