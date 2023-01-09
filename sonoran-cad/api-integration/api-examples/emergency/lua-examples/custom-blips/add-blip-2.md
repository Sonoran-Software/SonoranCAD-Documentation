---
description: >-
  This endpoint allows you to add a new custom blip for a set amount of time to
  your community's live map!
---

# Add Temp Blip

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Add Blip API endpoint](../../../../api-endpoints/emergency/custom-blips/add-blip.md).

```lua
function addTempBlipData(blipId, blipData, waitSeconds, returnToData)
    exports["sonorancad"]:performApiRequest({{
        ["id"] = blipId,
        ["data"] = blipData
    }}, "MODIFY_BLIP", function(_)

    end)

    Citizen.CreateThread(function()
        Citizen.Wait(waitSeconds * 1000)
        exports["sonorancad"]:performApiRequest({{
            ["id"] = blipId,
            ["data"] = returnToData
        }}, "MODIFY_BLIP", function(_)

        end)
    end)
end
```

### Parameters

| Property       | Type    | Description                                     |
| -------------- | ------- | ----------------------------------------------- |
| `blipId`       | Integer | Blip ID                                         |
| `blipData`     | Table   | Table of [blip objects](add-blip.md)            |
| `waitSeconds`  | Integer | Time to wait before removing the blip (seconds) |
| `returnToData` | Table   | Table of [blip objects](add-blip.md)            |
