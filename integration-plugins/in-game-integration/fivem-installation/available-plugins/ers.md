---
description: >-
  The Sonoran CAD ERS integration allows dispatchers to generate callouts from
  the live map, lookup character information, and more!
---

# Emergency Response Simulator (ERS)

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **Pro** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../other-products/server-hosting.md)!
{% endhint %}

<figure><img src="../../../../.gitbook/assets/ERS (1).png" alt=""><figcaption><p>Sonoran CAD x ERS</p></figcaption></figure>

## What is Emergency Response Simulator?

Emergency Response Simulator is a paid, third-party script for FiveM.

This advanced (co-op) PVE roleplay game mode simulates emergency service calls, where you as emergency service worker have to respond to. Whether you are a medic, firefighter, tow service operator or police officer, there is always something to do. With finetuned callouts you’ll never get bored of driving around in your service vehicle. Rush to high-priority, dangerous calls, or handle routine tasks like warning a speeder. Each callout is unique, with random outcomes that keep you curious and engaged every time you respond to an emergency.

[ERS can be purchased from Nights Software.](https://store.nights-software.com/category/ersgamemode)

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the ERS Submodule

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) to enable the ERS integration.

### 3. Update CAD Record Templates

The ERS submodule comes with three record templates (character, license and vehicle registration).

Importing and using these record templates will ensure ERS callout character, license, and vehicle registration records are automatically generated.

These records can be located in the `/sonorancad/submodules/ersintegration/SonoranCAD Records` directory.&#x20;

<figure><img src="../../../../.gitbook/assets/image (63).png" alt="" width="328"><figcaption><p>ERS Integration - SonoranCAD Custom Records</p></figcaption></figure>

{% hint style="info" %}
The `Civilian` and `Vehicle Registration` are default records. If you've modified them, it's recommended to replace them with the provided versions to ensure proper data import.
{% endhint %}

To import in Sonoran CAD, navigate to `Admin -> Customization -> Custom Records -> Import`.\
Open each JSON file and copy/paste the contents into the CAD.

<figure><img src="../../../../.gitbook/assets/image (64).png" alt="" width="375"><figcaption><p>SonoranCAD - Import Record</p></figcaption></figure>

### 4. Update night\_ers

The ERS submodules comes with two custom files that must be added to ERS in order for the submodule to function (`s_functions.lua` & `c_functions.lua`)

These files are located in:

* `/sonorancad/submodules/ersintegration/Drag Files To Client`&#x20;
* `/sonorancad/submodules/ersintegration/Drag Files To Server`

Drag-and-drop these files into `night_ers` in the `client` and `server` folders to overwrite the existing files.

<div><figure><img src="../../../../.gitbook/assets/image (67).png" alt=""><figcaption><p>ERS Integration - Server Functions File</p></figcaption></figure> <figure><img src="../../../../.gitbook/assets/image (68).png" alt=""><figcaption><p>ERS Integration - Client Functions File</p></figcaption></figure></div>

<figure><img src="../../../../.gitbook/assets/image (71).png" alt="" width="375"><figcaption><p>ERS - Client Folder </p></figcaption></figure>

## Configuration

ERS Integration is highly configurable to allow for custom records and calls. All default configuration will work with the provided CAD records seamlessly. It is only recommended to edit if you are experienced with [custom records](../../../../tutorials/customization/creating-custom-record-and-report-types.md).&#x20;

### Default Configuration

<details>

<summary>ersintegration_config.lua</summary>

```lua
--[[
    Sonoran Plugins

    Plugin Configuration

    Put all needed configuration in this file.
]]
local config = {
    enabled = true,
    pluginName = "ersintegration", -- name your plugin here
    pluginAuthor = "SonoranCAD", -- author
    configVersion = "1.0",
    -- put your configuration options below
    create911Call = true, -- Create a 911 call when an ERS callout is created
    createEmergencyCall = true, -- Create an emergency call when an ERS callout is accepted
    callPriority = 2, -- Priority of the call created in CAD (1-3) | Only used if createEmergencyCall is true
    callCodes = {
        ['Stolen_motorbike'] = '10-22'
    }, -- Call codes for each ERS callout type | Only used if createEmergencyCall is true
    autoAddCall = true, -- Automatically add members to the call when an ERS callout is accepted
    customRecords = {
        civilianRecordID = 7, -- Record ID for civilian records
        civilianValues = {
            -- Configurable mapping for SonoranCAD replaceValues.
            -- The key is what SonoranCAD expects and the value is either:
            --    • A string that matches a key in pedData, or
            --    • A function that returns a value based on pedData.
            --    • Left side of mapping is the SonoranCAD field mapping ID from Custom Records, right side is the ERS field.
            ["first"] = "FirstName",
            ["last"] = "LastName",
            ["dob"] = "DOB",
            ["sex"] = "Gender",
            ["residence"] = "Address",
            ["zip"] = "Zip",
            ["phone"] = "Phone",
            ["skin"] = "Nationality",
            -- Add more keys as needed:
            -- email = "Email"  -- Example: if pedData.Email exists.
        },
        vehicleRegistrationRecordID = 5, -- Record ID for vehicle registration records
        vehicleRegistrationValues = {
            -- Configurable mapping for SonoranCAD replaceValues.
            -- The key is what SonoranCAD expects and the value is either:
            --    • A string that matches a key in pedData, or
            --    • A function that returns a value based on pedData.
            --    • Left side of mapping is the SonoranCAD field mapping ID from Custom Records, right side is the ERS field.
            -- Registration Information
            ["status"] = function(vehicleData)
                if vehicleData.stolen then
                    return "STOLEN"
                elseif not vehicleData.mot then
                    return "EXPIRED"
                else
                    return "VALID"
                end
            end,
            ["_wsakvwigt"] = function(vehicleData)
                if vehicleData.stolen then
                    return "STOLEN"
                elseif not vehicleData.mot then
                    return "EXPIRED"
                else
                    return "VALID"
                end
            end,
            ["_imtoih149"] = function(vehicleData)
                return os.date("%m/%d/%Y", os.time() + (60 * 60 * 24 * 365)) -- +1 year from now
            end,
            -- Civilian Information
            ["first"] = function(vehicleData)
                return vehicleData.owner_name:match("^(%S+)")
            end,
            ["last"] = function(vehicleData)
                return vehicleData.owner_name:match("%s(.+)$")
            end,
            -- Vehicle Information
            ["plate"] = "license_plate",
            ["model"] = "model",
            ["color"] = function(vehicleData)
                if vehicleData.color_secondary and vehicleData.color_secondary ~= "" then
                    return vehicleData.color .. ", " .. vehicleData.color_secondary
                else
                    return vehicleData.color
                end
            end,
            ["year"] = "build_year",
            ["type"] = function(vehicleData)
                local classMap = {
                    [0] = "SEDAN", [1] = "SEDAN", [2] = "SUV", [3] = "SUV",
                    [4] = "COUPE", [5] = "COUPE", [6] = "OFFROAD", [7] = "TRUCK",
                    [8] = "MOTORCYCLE", [9] = "MARINE", [16] = "AIRCRAFT"
                }
                return classMap[vehicleData.vehicle_class] or "SEDAN"
            end,
        -- Add more keys as needed:
        -- owner = "Owner"  -- Example: if pedData.Owner exists.
        },
        licenseRecordId = 4, -- Record ID for license records
        licenseTypeField = "7eddab31daf4a0182", -- Field ID for license type
        licenseTypeConfigs = {
            DRIVER = {
                type = "DRIVER",
                is_valid = "is_license_car_valid",
                license = "license_car",
            },
            MOTORCYCLE = {
                type = "MOTORCYCLE",
                is_valid = "is_license_bike_valid",
                license = "license_bike",
            },
            BOAT = {
                type = "BOAT",
                is_valid = "is_license_boat_valid",
                license = "license_boat",
            },
            PILOT = {
                type = "PILOT",
                is_valid = "is_license_pilot_valid",
                license = "license_pilot",
            },
            CDL = {
                type = "CDL",
                is_valid = "is_license_truck_valid",
                license = "license_truck",
            },
        },
        licenseRecordValues = {
            -- License Information
            ["252c4250da9421cbd"] = function(pedData, ctx)
                return pedData[ctx.is_valid] and "VALID" or "SUSPENDED"
            end,
            ["878766af4964853a7"] = function(pedData, ctx)
                return pedData[ctx.is_valid] and "VALID" or "EXPIRED"
            end,
            ["_54iz1scv7"] = function(pedData)
                return os.date("%m/%d/%Y", os.time() + (60 * 60 * 24 * 365)) -- +1 year
            end,
            -- Civilian Information
            ["first"] = "first_name",
            ["last"] = "last_name",
            ["mi"] = "", -- No M.I. mapped
            ["dob"] = "dob",
            ["age"] = function(pedData)
                local birth = os.date("*t", os.time({year=tonumber(pedData.dob:sub(7,10)), month=tonumber(pedData.dob:sub(1,2)), day=tonumber(pedData.dob:sub(4,5))}))
                local now = os.date("*t")
                local age = now.year - birth.year
                if now.month < birth.month or (now.month == birth.month and now.day < birth.day) then
                    age = age - 1
                end
                return tostring(age)
            end,
            ["sex"] = "gender",
            ["residence"] = "address",
            ["zip"] = "postalCode",
        }
    }

}

if config.enabled then Config.RegisterPluginConfig(config.pluginName, config) end

```

</details>

### Configuration Values

<details>

<summary>Default Configuration Values</summary>

<table><thead><tr><th>Value</th><th width="113">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>create911Call</code></td><td><code>bool</code></td><td>Create a 911 call when an ERS callout is created</td></tr><tr><td><code>createEmergencyCall</code></td><td><code>bool</code></td><td>Create an emergency call when an ERS callout is accepted</td></tr><tr><td><code>callPriority</code></td><td><code>integer</code></td><td>Priority of the call created in CAD (1-3)</td></tr><tr><td><code>callCodes</code></td><td><code>array</code></td><td>Call codes for each ERS callout type. | Left side is the callout ID and right side is the corresponding 10 code</td></tr><tr><td><code>autoAddCall</code></td><td><code>bool</code></td><td>Automatically add members to the call when an ERS callout is accepted</td></tr><tr><td><code>customRecords</code></td><td><code>array</code></td><td>Array of record customization for CAD records. Please see comments in file for more information on record customization</td></tr></tbody></table>

</details>

## Features

### Live Map Callout Generation

Dispatchers can use the live map to create a new ERS callout at a specific location.

Drag-and-drop the `ERS` icon from the toolbar to a location on the map. Clicking the new ERS map icon will allow you customize the callout and settings.

<figure><img src="../../../../.gitbook/assets/b59e7ce6fd99609c128af1b0451865c2.gif" alt="" width="375"><figcaption><p>Sonoran CAD: ERS Callout Creation</p></figcaption></figure>

### Record Lookups

When a callout is first interacted with, character, license, and vehicle records will be generated in the CAD with the information.

This allows lookups in the CAD to be ran.

### Automatic Call Generation

* When a callout is generated in-game, a 911 call will be automatically created in the CAD.
  * 911 calls generated from a callout will display with location on the live map.
* When a callout is accepted by a unit:
  * A dispatch call is automatically generated.
  * The unit is automatically attached to the CAD dispatch call.
