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

```lua
function addBlips(blips, cb)
    exports["sonorancad"]:performApiRequest(blips, "ADD_BLIP", function(res)
        if cb ~= nil then
            cb(res)
        end
    end)
end
```

### Parameters

| Property | Type     | Description                          |
| -------- | -------- | ------------------------------------ |
| `blips`  | Table    | Table of [blip objects](add-blip.md) |
| `cb`     | Function | OPTIONAL: Callback function          |
