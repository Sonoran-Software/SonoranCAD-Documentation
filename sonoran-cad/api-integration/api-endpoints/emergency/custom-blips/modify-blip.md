---
description: This endpoint allows you to easily update a custom live map blip.
---

# Modify Blip

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/modify_blip" method="post" summary="Modify Blip" %}
{% swagger-description %}
This endpoint allows you to edit a custom blip on your live map.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
MODIFY_BLIP
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Blip 123 modified!
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}
{% endswagger %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "MODIFY_BLIP",
    "data": [
        {
            "id": 123, // Blip ID
            "coordinates": { // OPTIONAL - Coordinate Update
                "x": 0,
                "y": 1
            },
            "icon": "https://example.com/icon.png" // OPTIONAL - Icon Update
            "color": "#df03fc", // OPTIONAL - Hex Color Code
            "tooltip": "Example added from the API!" // OPTIONAL - Blip Tooltip
        },
    ]
}
```
