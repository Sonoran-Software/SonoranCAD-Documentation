---
description: >-
  This endpoint allows you to retrieve all custom blips for a community's live
  map!
---

# Remove Blip With Subtype

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

```lua
function removeWithSubtype(subType, cb)
    Utilities.CAD.getBlips(function(res)
        local dres = json.decode(res)
        local ids = {}
        if type(dres) == "table" then
            for _, v in ipairs(dres) do
                if v.subType == subType then
                    table.insert(ids, #ids + 1, v.id)
                end
            end
            Utilities.CAD.removeBlip(ids, cb)
        else
            print("No blips were returned.")
        end
    end)
end
```

### Parameters

| Property  | Type     | Description                 |
| --------- | -------- | --------------------------- |
| `subType` | String   | Blip subtype to remove      |
| `cb`      | Function | OPTIONAL: Callback function |
