---
description: >-
  The Unit Panic API call allows you to automatically trigger a unit panic from
  in-game.
---

# Unit Panic

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% hint style="info" %}
Toggling a unit's panic status via the API will not send this push event. These events should be listened for locally on the game server.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/unit_panic" method="post" summary="Unit Panic" %}
{% swagger-description %}
This The unit panic API endpoint allows you to automatically trigger a unit panic from in-game.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
UNIT_PANIC
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of unit objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
UNIT PANIC UPDATED
```
{% endswagger-response %}

{% swagger-response status="400" description="The following errors may be sent in response:" %}
```
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
    "type": "UNIT_PANIC",
    "data": [
        {
            "apiId": "STEAM:5678",
            "isPanic": true,
        }
    ]
}
```
