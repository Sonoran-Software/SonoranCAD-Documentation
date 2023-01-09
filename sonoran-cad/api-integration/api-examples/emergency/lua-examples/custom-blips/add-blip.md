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

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/add_blip" method="post" summary="Add Blip" %}
{% swagger-description %}
This endpoint allows you to add a custom blip to your live map.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
ADD_BLIP
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```json
// Blip object with ID set
[
    {
        "id": 1234,
        "coordinates": {
            "x": 0,
            "y": 0
        },
        "icon": "https://example.com/icon.png"
    }
]
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}
{% endswagger %}

```lua
function addBlip(coords, colorHex, subType, toolTip, icon, dataTable, cb)
    local data = {{
        ["serverId"] = GetConvar("sonoran_serverId", 1),
        ["blip"] = {
            ["id"] = -1,
            ["subType"] = subType,
            ["coordinates"] = {
                ["x"] = coords.x,
                ["y"] = coords.y
            },
            ["icon"] = icon,
            ["color"] = colorHex,
            ["tooltip"] = toolTip,
            ["data"] = dataTable
        }
    }}
    exports["sonorancad"]:performApiRequest(data, "ADD_BLIP", function(res)
        if cb ~= nil then
            cb(res)
        end
    end)
end
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
