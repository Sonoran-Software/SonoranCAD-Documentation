---
description: Update your unit's current status in the CAD via API.
---

# Unit Status

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/unit_status" method="post" summary="Update Unit Status" %}
{% swagger-description %}
The unit location API endpoint allows you to update a unit's location from in-game.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
UNIT_STATUS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of unit status objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
UNIT STATUS UPDATED
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
    "type": "UNIT_STATUS",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID entered in the unit identifiers
                                   // Typically, this is their STEAM ID
            "status": 0,           // Status Int (ENUM)
            "serverId": 1          // Server ID
        },
    ]
}
```

The unit status enumeration values are shown below. These reflect the default unit status options. Your community may have changed the wording with custom [unit status codes](../../../../../tutorials/customization/unit-status-codes.md).

| Integer (Enumeration) Value | Status Description |
| --------------------------- | ------------------ |
| 0                           | UNAVAILABLE        |
| 1                           | BUSY               |
| 2                           | AVAILABLE          |
| 3                           | ENROUTE            |
| 4                           | ON\_SCENE          |
