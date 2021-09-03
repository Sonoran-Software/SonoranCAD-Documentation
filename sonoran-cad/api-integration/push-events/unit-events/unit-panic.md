---
description: This event is sent when a unit toggles their panic status.
---

# Unit Panic

{% hint style="info" %}
This push event is not sent when a panic status is toggled via the API. API toggles should be listened to locally on the game server.
{% endhint %}

### EVENT\_UNIT\_PANIC

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

