---
description: >-
  This endpoint allows you to retrieve all custom blips for a community's live
  map!
---

# Get Map Blips

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/get_blips" method="post" summary="Get Blips" %}
{% swagger-description %}
This endpoint allows you to retrieve all custom blips on your live map.
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
        "subType": "Example", // Differentiate custom blips types
        "coordinates": {
            "x": 0,
            "y": 0
        },
        "color": "#000FFF",
        "icon": "https://example.com/icon.png",
        "data": [
            {
                "title": "Example 1",
                "text": "123",
            },
            {
                "title": "Example 2",
                "text": "456",
            }
        ]
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
function getBlips(cb) {
    var data = [{
        ["serverId"]: GetConvar("sonoran_serverId", 1)
    }];
    exports["sonorancad"].performApiRequest(data, "GET_BLIPS", function (res) {
        if (cb !== null) {
            cb(res);
        }
    });
}
```

### Parameters

| Property | Type     | Description       |
| -------- | -------- | ----------------- |
| `cb`     | Function | Callback function |
