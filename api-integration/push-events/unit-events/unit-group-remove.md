---
description: This push event notifies your server when a unit is removed from a unit group.
---

# Unit Group Remove

{% hint style="warning" %}
This push event requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

## EVENT\_UNIT\_GROUP\_REMOVE POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_UNIT_GROUP_REMOVE",
    "data": {
        "identId": 1,
        "groupName": "Ladder 61"
    }
}
```
