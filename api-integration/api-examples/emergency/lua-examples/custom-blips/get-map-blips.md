---
description: >-
  This endpoint allows you to retrieve all custom blips for a community's live
  map!
---

# Get Map Blips

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Get Blips API endpoint](../../../../api-endpoints/emergency/custom-blips/get-map-blips.md).

```lua
function getBlips(cb)
    local data = {{
        ["serverId"] = GetConvar("sonoran_serverId", 1)
    }}
    exports["sonorancad"]:performApiRequest(data, "GET_BLIPS", function(res)
        if cb ~= nil then
            cb(res)
        end
    end)
end
```

### Parameters

| Property | Type     | Description       |
| -------- | -------- | ----------------- |
| `cb`     | Function | Callback function |
