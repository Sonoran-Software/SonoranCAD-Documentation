---
description: This event is sent when a unit toggles their panic status.
---

# Unit Panic

### EVENT\_UNIT\_PANIC

{% hint style="warning" %}
This push event is not sent triggered via the API.  
API triggers should be listened to locally on the game server.
{% endhint %}

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_UNIT_PANIC",
    "data": [
        {
            "identId": 1, // Identifier ID
        }
    ]
}
```

