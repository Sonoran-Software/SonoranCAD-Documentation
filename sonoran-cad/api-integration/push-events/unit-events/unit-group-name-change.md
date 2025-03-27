---
description: This event is fired when a unit group's name is modified.
---

# Unit Group Name Change

{% hint style="warning" %}
This push event requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

## EVENT\_UNIT\_GROUP\_CHANGE\_NAME POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_UNIT_GROUP_CHANGE_NAME",
    "data": {
        "identIds": [1, 2, 3], // Unit Identifier IDs
        "oldName": "Some Old Group",
        "newName": "My New Group Name"
    }
}
```
