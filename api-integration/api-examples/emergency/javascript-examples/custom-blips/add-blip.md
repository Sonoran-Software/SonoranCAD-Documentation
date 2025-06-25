---
description: >-
  This endpoint allows you to add a new custom blip to your community's live
  map!
---

# Add Blip

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Add Blip API endpoint](../../../../api-endpoints/emergency/custom-blips/add-blip.md).

```javascript
function addBlip(coords, colorHex, subType, toolTip, icon, dataTable, cb) {
    let data = {
        ["serverId"]: GetConvar("sonoran_serverId", 1),
        ["blip"]: {
            ["id"]: -1,
            ["subType"]: subType,
            ["coordinates"]: {
                ["x"]: coords.x,
                ["y"]: coords.y
            },
            ["icon"]: icon,
            ["color"]: colorHex,
            ["tooltip"]: toolTip,
            ["data"]: dataTable
        }
    }
    exports["sonorancad"].performApiRequest(data, "ADD_BLIP", function (res) {
        if (cb !== null) {
            cb(res)
        }
    })
}
```

### Parameters

| Property    | Type     | Description                                                          |
| ----------- | -------- | -------------------------------------------------------------------- |
| `coords`    | vector2  | Coordinates of the blip on the map                                   |
| `colorHex`  | String   | Color hex of the blip                                                |
| `subType`   | String   | Blip subtype                                                         |
| `toolTip`   | String   | Blip tooltip                                                         |
| `icon`      | String   | Blip icon (from [Material UI](https://materialui.co/icon/local-atm)) |
| `dataTable` | Table    | `{{title = 'TITLE', text = 'TEXT'}}`                                 |
| `cb`        | Function | OPTIONAL: Callback function                                          |
