---
description: Update your unit's current status in the CAD via API.
---

# Unit Status

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/unit\_status" %}
{% api-method-summary %}
Update Unit Status
{% endapi-method-summary %}

{% api-method-description %}
The unit location API endpoint allows you to update a unit's location from in-game.
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
UNIT\_STATUS
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of unit status objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
UNIT STATUS UPDATED
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
    "type": "UNIT_STATUS ",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID entered in the unit identifiers
                                   // Typically, this is their STEAM ID
            "status": 0, // Status Int (ENUM)
        },
    ]
}
```

The unit status enumeration values are shown below. These reflect the default unit status options. Your community may have changed the wording with custom [unit status codes](../../../../tutorials/customization/unit-status-codes.md).

| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | UNAVAILABLE |
| 1 | BUSY |
| 2 | AVAILABLE |
| 3 | ENROUTE |
| 4 | ON\_SCENE |

