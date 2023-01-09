---
description: >-
  This endpoint allows you to add a new custom blip to your community's live
  map!
---

# Add Blips

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Add Blip API endpoint](../../../../api-endpoints/emergency/custom-blips/add-blip.md).

```javascript
function addBlips(blips, cb) {
    exports["sonorancad"].performApiRequest(blips, "ADD_BLIP", function (res) {
        if (cb != null) {
            cb(res);
        }
    });
}
```

### Parameters

| Property | Type     | Description                                                          |
| -------- | -------- | -------------------------------------------------------------------- |
| `blips`  | Table    | Table of [blip objects](../../lua-examples/custom-blips/add-blip.md) |
| `cb`     | Function | OPTIONAL: Callback function                                          |
