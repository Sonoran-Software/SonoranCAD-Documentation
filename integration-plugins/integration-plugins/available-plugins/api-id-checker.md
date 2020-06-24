---
description: Check if a given API ID is linked to an account.
---

# Check API ID

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

This simple plugin exposes a check to see if an API ID exists. This is useful if you want to inform players they need to create an account on the CAD.

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_apicheck/releases)to download the API ID plugin .zip file.

### 3. Install the Plugin

1. Follow the [standard plugin installation guide](../plugin-installation/) for the API ID plugin.

## Usage

### Command

This plugin supplies the command `/apiid` which will print the player's primary identifier \(the one they should use in Settings\) to their console.

### Function

Callback output parameter: true/false if API ID exists.

```lua
cadApiIdExists("identifier_here", callback)
```

#### Example

```lua
cadApiIdExists("steam:1234567890", function(exists)
    if exists then
        print("API ID exists!")
    else
        print("API ID does not exist!")
    end
end)
```

### Event

This is a _server only_ event.

**Event Name:** SonoranCAD::apicheck:CheckPlayerLinked

**Response Event:** SonoranCAD::apicheck:CheckPlayerLinkedResponse

#### Example

```lua
-- Request
TriggerEvent("SonoranCAD::apicheck:CheckPlayerLinked", source, identifier)

-- Response
AddEventHandler("SonoranCAD::apicheck:CheckPlayerLinkedResponse", function(player, identifier, exists)
    print(("Player %s has API ID? %s"):format(player, exists))
end)
```

