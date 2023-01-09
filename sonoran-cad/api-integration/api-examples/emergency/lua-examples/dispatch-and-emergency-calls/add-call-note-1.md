---
description: This endpoint allows you to easily update the postal on a dispatch call.
---

# Set Call Postal

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/set_call_postal" method="post" summary="Set Call Postal" %}
{% swagger-description %}
This endpoint allows you to easily update the postal on a dispatch call.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
SET_CALL_POSTAL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
CALL 123 POSTAL SET TO 456
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

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
