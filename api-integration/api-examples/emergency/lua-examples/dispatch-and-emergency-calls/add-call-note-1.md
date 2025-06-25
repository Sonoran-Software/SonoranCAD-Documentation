---
description: This endpoint allows you to easily update the postal on a dispatch call.
---

# Set Call Postal

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Set Call Postal API endpoint](../../../../api-endpoints/emergency/dispatch-and-emergency-calls/update-call-postal.md).

```lua
function setCallPostal(callId, postal)
    exports["sonorancad"]:performApiRequest({{
        ["serverId"] = GetConvar("sonoran_serverId", 1),
        ["callId"] = callId,
        ["postal"] = postal
    }}, "SET_CALL_POSTAL", function(_)
    end)
end
```

### Parameters

| Property | Type    | Description                |
| -------- | ------- | -------------------------- |
| `callId` | Integer | Call ID to add the note to |
| `postal` | Integer | Postal to add to the call  |
