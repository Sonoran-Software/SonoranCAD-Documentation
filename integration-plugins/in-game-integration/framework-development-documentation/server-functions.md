---
description: >-
  This page will explain all exported functions from the SonoranCAD Core that
  can be used on the server side
---

# Server Functions

### CadIsPlayerLinked

Checks if a specific CAD API ID exists by sending a request to the API and executing a callback with the result.

```lua
exports.sonorancad.CadIsPlayerLinked(apiId, callback)
```



{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="147" align="center">Parameter</th><th width="119" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>apiId</code></td><td align="center"><code>string</code></td><td align="center">The CAD API ID to check. If empty or <code>nil</code>, the function assumes the ID does not exist.</td></tr><tr><td align="center"><code>callback</code></td><td align="center"><code>function</code></td><td align="center">A function executed after the check completes. Receives a single parameter: <code>exists</code> (<code>boolean</code>).</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. Instead, the result of the API check is passed to the `callback` function.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Checking if a CAD API ID exists
local function onApiIdCheck(exists)
    if exists then
        print("API ID exists!")
    else
        print("API ID does not exist.")
    end
end

exports.sonorancad.CadIsPlayerLinked("123456", onApiIdCheck)  -- Output depends on API response
exports.sonorancad.CadIsPlayerLinked("", onApiIdCheck)        -- Output: "API ID does not exist."
```
{% endtab %}
{% endtabs %}

***

### GetPluginConfig

Provides access to a specific plugin's configuration using the plugin name.

```lua
exports.sonorancad.GetPluginConfig(submoduleName)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="182" align="center">Parameter</th><th width="119" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>submoduleName</code></td><td align="center"><code>string</code></td><td align="center">The name of the submodule whose configuration is to be retrieved.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
<table><thead><tr><th width="122">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>table</code> or <code>nil</code></td><td><ul><li>A table containing the configuration for the specified plugin.</li><li>Returns <code>nil</code> if the plugin name is invalid or if no configuration exists.</li></ul></td></tr></tbody></table>
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Retrieving a plugin's configuration
local pluginConfig = exports.sonorancad.GetPluginConfig("callcommands")

if pluginConfig then
    print("Plugin Config:", json.encode(pluginConfig))
else
    print("Plugin not found or no configuration available.")
end
```
{% endtab %}
{% endtabs %}

***

### GetUnitByPlayerId

Retrieves the unit information associated with a player based on their identifiers.

```lua
exports.sonorancad.GetUnitByPlayerId(player)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>player</code></td><td align="center"><code>PlayerSource</code></td><td align="center">The player ID for whom the associated unit is being retrieved.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
<table><thead><tr><th width="122">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>table</code> or <code>nil</code></td><td><ul><li>A table representing the unit information for the player if found in <code>UnitCache</code>.</li><li><code>nil</code> if no associated unit is found.</li></ul></td></tr></tbody></table>
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Getting the unit associated with a player
local unit = GetUnitByPlayerId(1)

if unit then
    print("Unit found:", json.encode(unit))
else
    print("No unit associated with this player.")
end
```
{% endtab %}
{% endtabs %}

### GetUnitCache

Returns the global `UnitCache` table containing unit data.

```lua
exports.sonorancad.GetUnitCache()
```

{% tabs %}
{% tab title="Parameters" %}
None
{% endtab %}

{% tab title="Returns" %}
<table><thead><tr><th width="122">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>table</code> </td><td><ul><li>The entire <code>UnitCache</code> table, which stores unit-related data.</li><li>If <code>UnitCache</code> is empty or uninitialized, an empty table is returned.</li></ul></td></tr></tbody></table>
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Retrieving and inspecting the UnitCache
local unitCache = exports.sonorancad.GetUnitCache()

if next(unitCache) then
    print("UnitCache contains data:", json.encode(unitCache))
else
    print("UnitCache is empty or uninitialized.")
end

```
{% endtab %}
{% endtabs %}

### registerEndpoints

Registers API endpoints for use with the `sonorancad` resource.

```lua
exports.sonorancad.registerEndpoints()
```

{% tabs %}
{% tab title="Parameters" %}
None
{% endtab %}

{% tab title="Returns" %}
This function does not return a value. It registers API endpoints with `sonorancad`.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Registering the endpoints
exports.sonorancad.registerEndpoints()
print("SonoranCAD API endpoints registered.")

```
{% endtab %}
{% endtabs %}

### addBlip

Adds a new blip to the map using the SonoranCAD integration.

```lua
exports.sonorancad.addBlip(coords, colorHex, subType, toolTip, icon, dataTable, cb)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="152" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>coords</code></td><td align="center"><code>vec2 (table)</code></td><td align="center">A table containing <code>x</code> and <code>y</code> coordinates for the blip location.</td></tr><tr><td align="center"><code>colorHex</code></td><td align="center"><code>string</code></td><td align="center">The hexadecimal color code (e.g., <code>"#FF0000"</code>) for the blip.</td></tr><tr><td align="center"><code>subType</code></td><td align="center"><code>string</code></td><td align="center">The subtype of the blip (e.g., <code>police</code>, <code>fire</code>, etc.).</td></tr><tr><td align="center"><code>toolTop</code></td><td align="center"><code>string</code></td><td align="center">The tooltip text that appears when hovering over the blip.</td></tr><tr><td align="center"><code>icon</code></td><td align="center"><code>string</code></td><td align="center">The icon for the blip (e.g., a specific image or identifier for visual context).</td></tr><tr><td align="center"><code>dataTable</code></td><td align="center"><code>table</code></td><td align="center">Additional data associated with the blip, stored in a custom table.</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Usage Example" %}
```lua
-- Example: Adding a new blip to the map
exports.sonorancad.addBlip(
    { x = 123.45, y = 678.90 },
    "#FF0000",
    "police",
    "Police Station",
    "police-icon",
    { info = "Main Headquarters" },
    function(response)
        if response.success then
            print("Blip successfully added!")
        else
            print("Failed to add blip:", response.error)
        end
    end
)
```
{% endtab %}
{% endtabs %}

### addBlips

Adds multiple blips to the map using the SonoranCAD integration.

```lua
exports.sonorancad.addBlips(blips, cb)
```

{% tabs %}
{% tab title="Parameters" %}


<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>blips</code></td><td align="center"><code>table</code></td><td align="center">A table containing multiple blip data objects to be added. (See <a href="server-functions.md#addblip">addBlip</a> for blip structure)</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Adding multiple blips to the map
local blips = {
    {
        blip = {
            id = -1,
            subType = "police",
            coordinates = { x = 123.45, y = 678.90 },
            icon = "police-icon",
            color = "#FF0000",
            tooltip = "Police Station",
            data = { info = "Main Headquarters" }
        }
    },
    {
        blip = {
            id = -1,
            subType = "fire",
            coordinates = { x = 321.65, y = 987.10 },
            icon = "fire-icon",
            color = "#FFA500",
            tooltip = "Fire Department",
            data = { info = "Fire HQ" }
        }
    }
}

exports.sonorancad.addBlips(blips, function(response)
    if response.success then
        print("Blips successfully added!")
    else
        print("Failed to add blips:", response.error)
    end
end)

```
{% endtab %}
{% endtabs %}

### removeBlip

Removes one or more blips from the map using the SonoranCAD integration.

```lua
exports.sonorancad.removeBlip(ids, cb)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>ids</code></td><td align="center"><code>table</code></td><td align="center">A table containing the IDs of the blips to be removed.</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Removing blips by their IDs
local blipIds = { 101, 102, 103 }

exports.sonorancad.removeBlip(blipIds, function(response)
    if response.success then
        print("Blips successfully removed!")
    else
        print("Failed to remove blips:", response.error)
    end
end)

```
{% endtab %}
{% endtabs %}

### modifyBlipd

Modifies an existing blip's data on the map using the SonoranCAD integration.

```lua
exports.sonorancad.modifyBlipd(blipId, dataTable)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="152" align="center">Parameter</th><th width="123" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>blipId</code></td><td align="center"><code>number</code></td><td align="center">The unique ID of the blip to be modified.</td></tr><tr><td align="center"><code>dataTable</code></td><td align="center"><code>table</code></td><td align="center">A table containing the new data for the blip. See <a href="server-functions.md#addblip">addBlip</a> for blip data structure</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value. The request is sent to the `MODIFY_BLIP` endpoint.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Modifying an existing blip's data
local blipId = 101
local newData = {
    color = "#00FF00",
    tooltip = "Updated Tooltip",
    coordinates = { x = 200.0, y = 300.0 }
}

exports.sonorancad.modifyBlipd(blipId, newData)
print("Blip modification request sent.")

```
{% endtab %}
{% endtabs %}

### getBlips

Fetches the list of all active blips from the SonoranCAD system.

```lua
exports.sonorancad.getBlips(cb)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response containing the blips.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Fetching all active blips
exports.sonorancad.getBlips(function(response)
    if response.success then
        print("Active Blips:", json.encode(response.data))
    else
        print("Failed to fetch blips:", response.error)
    end
end)

```
{% endtab %}
{% endtabs %}

### removeWithSubtype

Removes all blips of a specific subtype from the map using the SonoranCAD system.

```lua
exports.sonorancad.removeWithSubtype(subType, cb)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>subType</code></td><td align="center"><code>string</code></td><td align="center">The subtype of the blips to be removed (e.g., <code>police</code>, <code>fire</code>, etc.).</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response containing the blips.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the `removeBlip` API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Removing all police blips
exports.sonorancad.removeWithSubtype("police", function(response)
    if response.success then
        print("Police blips successfully removed!")
    else
        print("Failed to remove blips:", response.error)
    end
end)

```
{% endtab %}
{% endtabs %}

### call911

The `call911` function facilitates the creation of a 911 emergency call within the SonoranCAD system by sending a structured API request.

```lua
exports.sonorancad.call911(caller, location, description, postal, plate, cb, coords, customMeta, deleteAfter)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="176" align="center">Parameter</th><th width="120" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>caller</code></td><td align="center"><code>string</code></td><td align="center">Name of the individual initiating the call.</td></tr><tr><td align="center"><code>location</code></td><td align="center"><code>string</code></td><td align="center">Description of the call's location (e.g., street address).</td></tr><tr><td align="center"><code>description</code></td><td align="center"><code>string</code></td><td align="center">Detailed information about the emergency situation.</td></tr><tr><td align="center"><code>postal</code></td><td align="center"><code>string</code></td><td align="center">Postal code corresponding to the call's location.</td></tr><tr><td align="center"><code>plate</code></td><td align="center"><code>string</code></td><td align="center">(Optional) License plate number associated with the call, if applicable.</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) Callback function to handle the API response.</td></tr><tr><td align="center"><code>coords</code></td><td align="center"><code>table</code></td><td align="center">A table containing the X and Y coordinates of the emergency call's location, typically sourced from in-game player or vehicle position. This is used to place the call accurately on the live map in CAD systems or dispatch plugins.</td></tr><tr><td align="center"><code>customMeta</code></td><td align="center"><code>table</code></td><td align="center">A flexible table for including any custom metadata relevant to the emergency call.</td></tr><tr><td align="center"><code>deleteAfter</code></td><td align="center"><code>int</code></td><td align="center">Number of minutes to automatically remove the call from CAD after</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function, if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Initiating a 911 call
exports.sonorancad.call911(
    "Jane Doe",
    "1234 Elm Street",
    "There is a fire in the building.",
    "56789",
    nil,
    function(response)
        if response.success then
            print("911 call successfully placed.")
        else
            print("Failed to place 911 call:", response.error)
        end
    end,
    { x = 84.49, y = 953.593 },
    {
        someMetaData = "yes this is metadata"
    } 
)
```
{% endtab %}
{% endtabs %}

### addTempBlipData

Temporarily modifies a blip's data in the SonoranCAD system and then reverts it back to its original data after a specified duration.

```lua
exports.sonorancad.addTempBlipData(blipId, blipData, waitSeconds, returnToData)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="176" align="center">Parameter</th><th width="120" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>blipId</code></td><td align="center"><code>number</code></td><td align="center">The unique ID of the blip to modify.</td></tr><tr><td align="center"><code>blipData</code></td><td align="center"><code>table</code></td><td align="center">A table containing the temporary data to apply to the blip. See <a href="server-functions.md#addblip">addBlip</a> for blip data structure</td></tr><tr><td align="center"><code>waitSeconds</code></td><td align="center"><code>number</code></td><td align="center">The duration in seconds for which the temporary data will be applied.</td></tr><tr><td align="center"><code>returnToData</code></td><td align="center"><code>table</code></td><td align="center">A table containing the original data to revert the blip to after the duration expires. See <a href="server-functions.md#addblip">addBlip</a> for blip data structure</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The data modification happens asynchronously using API requests.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Temporarily modifying a blip's color and tooltip
local tempData = {
    color = "#FF0000",
    tooltip = "Temporary Alert"
}

local originalData = {
    color = "#00FF00",
    tooltip = "Original Tooltip"
}

exports.sonorancad.addTempBlipData(101, tempData, 10, originalData)
print("Blip temporarily modified; it will revert in 10 seconds.")

```
{% endtab %}
{% endtabs %}

### addTempBlipColor

Temporarily changes a blip's color in the SonoranCAD system and reverts it to its original color after a specified duration.

```lua
exports.sonorancad.addTempBlipData(blipId, color, waitSeconds, returnToColor)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="189" align="center">Parameter</th><th width="120" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>blipId</code></td><td align="center"><code>number</code></td><td align="center">The unique ID of the blip to modify.</td></tr><tr><td align="center"><code>color</code></td><td align="center"><code>string</code></td><td align="center">The temporary hexadecimal color code to apply to the blip (e.g., <code>"#FF0000"</code>)</td></tr><tr><td align="center"><code>waitSeconds</code></td><td align="center"><code>number</code></td><td align="center">The duration in seconds for which the temporary data will be applied.</td></tr><tr><td align="center"><code>returnToColor</code></td><td align="center"><code>string</code></td><td align="center">The original hexadecimal color code to revert the blip to after the duration expires</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The color modification happens asynchronously using API requests.
{% endtab %}

{% tab title="Example Usage" %}
<pre class="language-lua"><code class="lang-lua">-- Example: Temporarily changing a blip's color to red
local tempColor = "#FF0000"
local originalColor = "#00FF00"

<strong>exports.sonorancad.addTempBlipColor(101, tempColor, 10, originalColor)
</strong>print("Blip color temporarily changed; it will revert in 10 seconds.")

</code></pre>
{% endtab %}
{% endtabs %}

### remove911

Removes an active 911 call from the SonoranCAD system.

```lua
exports.sonorancad.remove911(callId)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>callId</code></td><td align="center"><code>string</code></td><td align="center">The unique ID of the 911 call to be removed.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value. The removal of the 911 call is handled asynchronously through the API request.
{% endtab %}

{% tab title="Example Usage" %}
<pre class="language-lua"><code class="lang-lua">-- Example: Removing a 911 call
local callId = "12345"

<strong>exports.sonorancad.remove911(callId)
</strong>print("Request to remove 911 call sent.")
</code></pre>
{% endtab %}
{% endtabs %}

### addCallNote

Adds a note to an existing 911 call in the SonoranCAD system.

```lua
exports.sonorancad.addCallNote(callId, note)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>callId</code></td><td align="center"><code>string</code></td><td align="center">The unique ID of the 911 call to be removed.</td></tr><tr><td align="center"><code>note</code></td><td align="center"><code>string</code></td><td align="center">The content of the note to be added, typically describing the caller.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value. The addition of the call note is handled asynchronously through the API request.
{% endtab %}

{% tab title="Example Usage" %}
```
-- Example: Adding a note to an existing 911 call
local callId = "12345"
local note = "Caller reported a fire at the intersection of 5th and Main."

exports.sonorancad.addCallNote(callId, note)
print("Request to add note to 911 call sent.")

```
{% endtab %}
{% endtabs %}

### setCallPostal

Updates the postal code of an existing 911 call in the SonoranCAD system.

```lua
exports.sonorancad.setCallPostal(callId, postal)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>callId</code></td><td align="center"><code>string</code></td><td align="center">The unique ID of the 911 call to be removed.</td></tr><tr><td align="center"><code>postal</code></td><td align="center"><code>string</code></td><td align="center">The new postal code to assign to the 911 call.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value. The postal code update is handled asynchronously through the API request.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Updating the postal code of an existing 911 call
local callId = "12345"
local postal = "56789"

exports.sonorancad.setCallPostal(callId, postal)
print("Request to update postal code sent.")
```
{% endtab %}
{% endtabs %}

### performLookup

Performs a lookup in the SonoranCAD system for information associated with a license plate.

```lua
exports.sonorancad.performLookup(plate, cb)
```

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th width="132" align="center">Parameter</th><th width="161" align="center">Type</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><code>plate</code></td><td align="center"><code>string</code></td><td align="center">The license plate number to look up in the SonoranCAD system.</td></tr><tr><td align="center"><code>cb</code></td><td align="center"><code>function</code></td><td align="center">(Optional) A callback function executed with the API response.</td></tr></tbody></table>
{% endtab %}

{% tab title="Returns" %}
This function does not return a value directly. The response from the API request is passed to the `cb` callback function if provided.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Performing a lookup for a license plate
local plate = "ABC123"

exports.sonorancad.performLookup(plate, function(response)
    if response.success then
        print("Lookup successful:", json.encode(response.data))
    else
        print("Lookup failed:", response.error)
    end
end)

```
{% endtab %}
{% endtabs %}

### createDispatchCall

Creates a dispatch call in SonoranCAD

```lua
exports.sonorancad.createDispatchCall(origin, status, priority, block, address, postal, title, code, primary, trackPrimary, description, notes, metaData, units, cb)
```

{% tabs %}
{% tab title="Parameter" %}


| Parameter      | Type       | Description                                                                              |
| -------------- | ---------- | ---------------------------------------------------------------------------------------- |
| `origin`       | `number`   | Source of the dispatch call (see ORIGIN enum in SonoranCAD documentation). Typically `0` |
| `status`       | `number`   | Initial call status (see STATUS enum). Typically `0`                                     |
| `priority`     | `number`   | Call priority: `1` (high), `2` (medium), `3` (low).                                      |
| `block`        | `string`   | Block or unit number of the incident location.                                           |
| `address`      | `string`   | Full address or street description of the incident.                                      |
| `postal`       | `string`   | Postal code corresponding to the call’s location.                                        |
| `title`        | `string`   | Short title of the dispatch call (e.g., "Traffic Stop").                                 |
| `code`         | `string`   | CAD signal or code (e.g., "10-39 - Traffic Stop").                                       |
| `primary`      | `number`   | Identifier of the primary unit assigned to the call.                                     |
| `trackPrimary` | `boolean`  | Whether to track the primary unit on the live map.                                       |
| `description`  | `string`   | Detailed description of the situation.                                                   |
| `notes`        | `array`    | Array of note objects related to the call. Optional.                                     |
| `metaData`     | `array`    | Custom key-value metadata for internal tracking or display. Optional.                    |
| `units`        | `array`    | Array of unit API IDs (e.g., Steam hex IDs) to assign to the call.                       |
| `cb`           | `function` | Callback function to handle the API response.                                            |
{% endtab %}

{% tab title="Return" %}
This function does not return a value directly. The data modification happens asynchronously using API requests.
{% endtab %}

{% tab title="Example Usage" %}
```lua
-- Example: Creating a dispatch call
createDispatchCall(
    0,                              -- origin
    0,                              -- status
    1,                              -- priority (1 = High)
    "123",                          -- block number
    "1234 Elm Street",             -- address
    "56789",                        -- postal
    "Structure Fire",              -- title
    "10-70 - Structure Fire",      -- code
    456,                            -- primary unit ID
    true,                           -- trackPrimary
    "Caller reports flames visible from second floor window.", -- description
    {},                             -- notes (optional)
    { severity = "high", buildingType = "residential" },       -- custom metaData
    { "STEAM:110000112345678" },    -- units (API IDs)
    function(response)
        if response.success then
            print("Dispatch call successfully created.")
        else
            print("Failed to create dispatch call:", response.error)
        end
    end
)
```
{% endtab %}
{% endtabs %}

### cadNameLookup

Perform a name lookup in CAD (Requires "Lookups" submodule to be enabled)

{% hint style="danger" %}
This function will not work if you do not have the "Lookups" submodule enabled. The submodule is enabled by default.&#x20;
{% endhint %}

```lua
exports.sonorancad.cadNameLookup(first, last, mi, callback, autoLookup)
```

{% tabs %}
{% tab title="Parameters" %}
| Parameter    | Type       | Description                                                        |
| ------------ | ---------- | ------------------------------------------------------------------ |
| `first`      | `string`   | First Name                                                         |
| `last`       | `string`   | Last Name                                                          |
| `mi`         | `string`   | Middle Initial                                                     |
| `callback`   | `function` | Callback function to handle the API response.                      |
| `autoLookup` | `string`   | API ID of the user to perform a lookup via API ID rather than name |
{% endtab %}

{% tab title="Return" %}
This function will return the custom records related to the name as denoted in the [Custom Records](../../../api-integration/api-endpoints/general/custom-records/) section &#x20;
{% endtab %}

{% tab title="Example Usage" %}
<pre class="language-lua"><code class="lang-lua">exports.sonorancad.cadNameLookup("Jordan", "Green", "J", function(record)
<strong>    print(json.encode(record))
</strong>end, "123456789123456789")
</code></pre>
{% endtab %}
{% endtabs %}

### cadPlateLookup

Perform a plate lookup in CAD (Requires "Lookups" submodule to be enabled)

{% hint style="danger" %}
This function will not work if you do not have the "Lookups" submodule enabled. The submodule is enabled by default.
{% endhint %}

```lua
exports.sonorancad.cadPlateLookup(plate, callback, autoLookup)
```

{% tabs %}
{% tab title="Parameters" %}
| Parameter    | Type       | Description                                                        |
| ------------ | ---------- | ------------------------------------------------------------------ |
| `plate`      | `string`   | Plate number to lookup                                             |
| `callback`   | `function` | Callback function to handle the API response.                      |
| `autoLookup` | `string`   | API ID of the user to perform a lookup via API ID rather than name |
{% endtab %}

{% tab title="Return" %}
This function will return the custom records related to the plate as denoted in the [Custom Records](../../../api-integration/api-endpoints/general/custom-records/) section
{% endtab %}

{% tab title="Example Usage" %}
```lua
exports.sonorancad.cadPlateLookup("ABC123", function(record)
    print(json.encode(record))
end, "123456789123456789")
```
{% endtab %}
{% endtabs %}

### getAllWarrantsAndBolos

Retrieve all active and inactive warrants and bolos with pagination support

```lua
exports.sonorancad.getAllWarrantsAndBolos(options, cb)
```

{% tabs %}
{% tab title="Parameters" %}
| Parameter                                                  | Type                            | Description                                                                                                                                                                        |
| ---------------------------------------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `options`                                                  | `table`                         | Options for pagination and filtering. If omitted, defaults are used (Optional)                                                                                                     |
| `options.pageSize` / `options.limit`                       | `number`                        | Page size per API request. Default `100`                                                                                                                                           |
| `options.offset`                                           | `number`                        | Starting offset for pagination. Default `0`                                                                                                                                        |
| `options.maxPages` / `options.pageLimit` / `options.pages` | `number`                        | Max number of pages to fetch before stopping (caps total results). Default: no cap                                                                                                 |
| `options.statuses` / `options.status`                      | `table` \| `string` \| `number` | Status filter(s). Defaults to `{0, 1}` (open + closed). Accepts numeric values or strings: `"open"`, `"active"`, `"closed"`, `"inactive"`, `"pending"`, `"approved"`, `"rejected"` |
| `options.types`                                            | `table<number>`                 | Record types to include. Default `{2, 3}` (Warrant + BOLO)                                                                                                                         |
| `cb`                                                       | `function`                      | Callback invoked as `cb(records, meta)` where records is the aggregated list and `meta` includes paging info or an error.                                                          |


{% endtab %}

{% tab title="Example Usage" %}
```lua
exports['sonorancad']:getAllWarrantsAndBolos(function(records, meta)
    print(json.encode(records))
    print(json.encode(meta))
end)

```
{% endtab %}

{% tab title="Returns" %}
```lua
-- records (array)
{
    {
        id = 12345,
        type = 3, -- BOLO
        name = "BOLO",
        sections = {
            {
                category = 1,
                label = "Flags",
                fields = {
                    { uid = "flags", data = { flags = { "Armed", "Violent" } } }
                }
            },
            {
                category = 0,
                label = "Vehicle Information",
                fields = {
                    { uid = "plate", value = "ABC123" },
                    { uid = "make", value = "Dodge" },
                    { uid = "model", value = "Charger" },
                    { uid = "color", value = "Black" }
                }
            }
        }
    },
    {
        id = 67890,
        type = 2, -- Warrant
        name = "Warrant",
        sections = {
            {
                category = 1,
                label = "Flags",
                fields = {
                    { uid = "flags", data = { flags = { "Felony", "No Bond" } } }
                }
            },
            {
                category = 0,
                label = "Civilian Information",
                fields = {
                    { uid = "first", value = "Jane" },
                    { uid = "last", value = "Doe" },
                    { uid = "dob", value = "01/01/1990" }
                }
            }
        }
    }
}

-- meta
{
    ok = true,
    pages = 2,
    limit = 100,
    offset = 0,
    statuses = { 0, 1 }
}
```
{% endtab %}
{% endtabs %}
