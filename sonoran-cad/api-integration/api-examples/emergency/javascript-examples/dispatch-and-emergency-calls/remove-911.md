---
description: >-
  This endpoint allows you to remove an existing emergency/911 call from the
  CAD.
---

# Remove 911

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Remove Emergency Call API endpoint](../../../../api-endpoints/emergency/dispatch-and-emergency-calls/remove-911.md).

```javascript
function remove911(callId) {
  exports["sonorancad"].performApiRequest({
    serverId: GetConvar("sonoran_serverId", 1),
    callId: callId
  }, "REMOVE_911", function(_) {
  });
}
```

### Parameters

| Property | Type    | Description       |
| -------- | ------- | ----------------- |
| `callId` | Integer | Call ID to remove |
