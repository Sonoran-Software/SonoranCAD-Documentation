---
description: >-
  This endpoint allows you to retrieve all custom blips for a community's live
  map!
---

# Get Map Blips

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/get_blips" method="post" summary="Get Blips" %}
{% swagger-description %}
This endpoint allows you to ban a user account in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
GET_BLIPS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```json
// Array of blip objects
[
    {
        "id": 1,
        "coordinates": {
            "x": 0,
            "y": 0
        },
        "icon": "https://example.com/icon.png"
    }
]
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
    "type": "GET_BLIPS",
    "data": [
        {
            "serverId": 1 // Server ID
        },
    ]
}
```
