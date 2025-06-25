---
description: >-
  This API endpoint allows you to generate and attach units to a new dispatch
  call.
---

# New Dispatch

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/new_dispatch" method="post" summary="New Dispatch" %}
{% swagger-description %}
The unit location API endpoint allows you to create and assign a new dispatch.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
NEW_DISPATCH
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of dispatch objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
NEW DISPATCH CREATED - ID: {CallId}
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

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "NEW_DISPATCH",
    "data": [
        {
            "serverId": 1, // Default 1 - See guide on setting up multiple servers
            "origin": 0, // See ORIGIN Enum
            "status": 0, // See STATUS Enum
            "priority": 1, // 1, 2, or 3
            "block": "123",
            "address": "4234 E. Example Ave",
            "postal": "456",
            "title": "Traffic Stop",
            "code": "10-39 - Traffic Stop",
            "primary": 123, // Primary unit identifier on the call
            "trackPrimary": true, // Track the primary unit in-game with the Dispatch Notify plugin
            "description": "Traffic Stop - Blue Sedan - XP123BS",
            "notes": [], // Array of call note objects
            "metaData": {
                "someKey": "someValue" // OPTIONAL: metaData for API custom storage
            },
            "units": ["STEAM:1234"] // Array of API IDs
                                // Typically, this is their STEAM Hex
        },
    ]
}
```

{% hint style="info" %}
The "Primary" unit field in the new dispatch is set to the first unit in the `units` array, if it exists.
{% endhint %}

### Enumeration Values

Sonoran CAD uses integer enumeration values for the `origin` and `status` fields. See the tables below for more information.

{% tabs %}
{% tab title="ORIGIN" %}
| Integer (Enumeration) Value | Origin Description |
| --------------------------- | ------------------ |
| 0                           | CALLER             |
| 1                           | RADIO DISPATCH     |
| 2                           | OBSERVED           |
| 3                           | WALK\_UP           |
{% endtab %}

{% tab title="STATUS" %}
| Integer (Enumeration) Value | Status Description |
| --------------------------- | ------------------ |
| 0                           | PENDING            |
| 1                           | ACTIVE             |
| 2                           | CLOSED             |
{% endtab %}
{% endtabs %}

### Note Object

Call notes are formatted on dispatch calls with the following object:

```json
{
    "time": "12:00:00",
    "label": "A-10",
    "type": "text",
    "content": "This is a note!"
}
```
