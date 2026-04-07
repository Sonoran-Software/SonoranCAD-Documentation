---
description: This push event is sent when a new Inferno page is sent.
---

# Event Pager Reborn

{% hint style="warning" %}
This push event requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

### EVENT\_PAGER\_REBORN

```javascript
{
  "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
  "type": "EVENT_PAGER_REBORN",
  "data": {
    "addresses": [
      "FIRE-1",
      "BATTALION-1"
    ],
    "players": [
      12,
      34
    ],
    "nature": "Administrative", // Emergency, NonEmergency, or Administrative
    "body": "Respond to briefing room."
  }
}
```

### Data Fields

* `addresses`: Array of routed Inferno pager address strings selected in CAD.
* `players`: Array of numeric player IDs when paging specific players directly.
* `nature`: String enum value. Possible values are `Emergency`, `NonEmergency`, and `Administrative`.
* `body`: Message body sent with the page.
