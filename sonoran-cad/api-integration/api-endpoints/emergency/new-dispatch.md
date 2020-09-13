---
description: >-
  This API endpoint allows you to generate and attach units to a new dispatch
  call.
---

# New Dispatch

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/new\_dispatch" %}
{% api-method-summary %}
New Dispatch
{% endapi-method-summary %}

{% api-method-description %}
The unit location API endpoint allows you to create and assign a new dispatch.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Your community's ID
{% endapi-method-parameter %}

{% api-method-parameter name="key" type="string" required=true %}
Your community's API Key
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
NEW\_DISPATCH
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of dispatch objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
NEW DISPATCH CREATED - ID: {CallId}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following 400 errors may be sent in response:
{% endapi-method-response-example-description %}

```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

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
            "description": "Traffic Stop - Blue Sedan - XP123BS",
            "notes": "",
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
| Integer \(Enumeration\) Value | Origin Description |
| :--- | :--- |
| 0 | CALLER |
| 1 | RADIO DISPATCH |
| 2 | OBSERVED |
| 3 | WALK\_UP |
{% endtab %}

{% tab title="STATUS" %}
| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | PENDING |
| 1 | ACTIVE |
| 2 | CLOSED |
{% endtab %}
{% endtabs %}

