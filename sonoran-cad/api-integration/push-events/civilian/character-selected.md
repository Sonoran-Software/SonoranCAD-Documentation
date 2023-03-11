---
description: >-
  This push event is sent when a user selects a new character in the civilian
  page.
---

# Character Selected

{% hint style="warning" %}
This push event requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

### EVENT\_CHAR\_SELECTED

```javascript
{
  "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
  "type": "EVENT_CHAR_SELECTED",
  "data": {
    "id": 1, // numerical record ID OR DB sync key string (steam hex, license, etc.)
  }
}
```
