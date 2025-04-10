---
description: This push event is sent when a new station alert is sent.
---

# New Station Alert

{% hint style="warning" %}
This push event requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

### EVENT\_NEW\_CALLOUT

```javascript
{
  "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
  "type": "EVENT_STATION_ALERT",
  "data": {
    "locations": [
      {
        "name": "Fire Station One",
        "open": [
          "Door 1",
          "Door 2"
        ],
        "close": [
          "Door 3"
        }
      }
    ],
    "message": "Some TTS message here!", // May also be a base 64 string for AI audio
    "colors": [
      "blue"
    ],
    "tone": "tone1", // May also be a S3 URL to hosted tone audio
  }
}
```
