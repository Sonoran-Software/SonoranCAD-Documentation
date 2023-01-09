---
description: >-
  This endpoint allows you to remove custom blips from your community's live
  map.
---

# Remove Blip

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Remove Blip API endpoint](../../../../api-endpoints/emergency/custom-blips/remove-blip.md).

```lua
function removeBlip(ids, cb)
    exports["sonorancad"]:performApiRequest({{
        ["ids"] = ids
    }}, "REMOVE_BLIP", function(res)
        if cb ~= nil then
            cb(res)
        end
    end)
end
```

### Parameters

| Property | Type     | Description                 |
| -------- | -------- | --------------------------- |
| `ids`    | Integer  | Blip ID to remove           |
| `cb`     | Function | OPTIONAL: Callback function |
