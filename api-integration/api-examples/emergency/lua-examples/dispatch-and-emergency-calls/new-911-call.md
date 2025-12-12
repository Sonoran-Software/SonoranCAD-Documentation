---
description: >-
  The 911 Call API endpoint allows you to send 911 calls from in-game directly
  to your dispatchers.
---

# New 911 Call

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% hint style="info" %}
It is recommended to use the "Callcommands Export" rather than a "Raw API Call" whenever possible.
{% endhint %}

## Raw API Call&#x20;

This framework export handles the [Emergency Call API endpoint](../../../../api-endpoints/emergency/dispatch-and-emergency-calls/911-call.md).

```lua
function call911(caller, location, description, postal, plate, cb)
    exports["sonorancad"]:performApiRequest({{
        ["serverId"] = GetConvar("sonoran_serverId", 1),
        ["isEmergency"] = true,
        ["caller"] = caller,
        ["location"] = location,
        ["description"] = description,
        ["metaData"] = {
            ["useCallLocation"] = true,
            ["plate"] = plate,
            ["postal"] = postal
        }
    }}, "CALL_911", cb)
end
```

### Parameters

| Property          | Type     | Description                                                         |
| ----------------- | -------- | ------------------------------------------------------------------- |
| `caller`          | String   | Name of the caller                                                  |
| `location`        | String   | Street(s) name                                                      |
| `description`     | String   | Call description                                                    |
| `useCallLocation` | Boolean  | Should the postal location be drawn when using the `/rcall` command |
| `postal`          | Integer  | Postal location of the call                                         |
| `plate`           | String   | OPTIONAL: Plate to report in the call                               |
| `cb`              | Function | OPTIONAL: Callback function                                         |

## [Callcommands](https://github.com/Sonoran-Software/sonoran_callcommands) Export

This method utilizes the [callcommands](https://github.com/Sonoran-Software/sonoran_callcommands) plugin to execute a 911 call.

```lua
-- Parameters
emergency, caller, location, description, source, silenceAlert, useCallLocation type
-- Usage example (client sided)
local pos = GetEntityCoords(PlayerPedId())
local s1, s2 = GetStreetNameAtCoord(pos.x, pos.y, pos.z)
local street1 = GetStreetNameFromHashKey(s1)
local street2 = GetStreetNameFromHashKey(s2)
local streetLabel = street1
if street2 ~= nil then
	streetLabel = streetLabel .. ' ' .. street2
end

TriggerServerEvent('SonoranCAD::callcommands:SendCallApi', true, 'Bystander', streetLabel, 'Someone is selling drugs on the street', GetPlayerServerId(PlayerId()), nil, nil, '911')
```



## Troubleshooting&#x20;

1. "`/rcall` is not drawing a postal route to the call location&#x20;
   1. If you are using the Raw API Call method, please ensure that you have `useCallLocation` set to true.
   2. On either version of the call, please ensure that the postal is a valid, integer value
2. "Units are not getting the call in-game"
   1. Please ensure that you have the [dispatchnotify ](/broken/pages/-MIHp42WkewxQos-EnNZ)plugin installed
   2. Please ensure the unit is on duty with the configured method in [dispatchnotify](/broken/pages/-MIHp42WkewxQos-EnNZ)
   3. Please ensure your server's port and IP are correctly set in the Admin -> In-game Integration -> Livemap section of CAD

