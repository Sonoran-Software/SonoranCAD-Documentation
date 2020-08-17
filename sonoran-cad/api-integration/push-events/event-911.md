---
description: >-
  This push event sends data when a new 911/emergency call is placed via API or
  in-CAD.
---

# Event 911

### EVENT\_911 POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_911",
    "data": [
        {
            "call": {
                "callId": 1234,
                "isEmergency": true, // Emergency or Civil
                "caller": "John Doe",
                "location": "1234 E Hawick Ave",
                "description": "This is a 911 call!"
            },
            "apiIds": ["Steam:1234", "11112222"] // User account's API ID
        }
    ]
}
```

#### API IDs

The API ID list will only be returned if the 911 call was placed via the CAD interface and not via an API call.

