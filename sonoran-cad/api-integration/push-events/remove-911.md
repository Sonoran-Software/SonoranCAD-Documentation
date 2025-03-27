---
description: This push event sends data when a 911 call is removed.
---

# Remove 911

{% hint style="warning" %}
This push event requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

### EVENT\_REMOVE\_911 POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_REMOVE_911",
    "data": [
        {
            "callIds": [1234, 5678]
        }
    ]
```
