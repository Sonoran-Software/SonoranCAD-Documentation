---
description: This endpoint allows you to check your Sonoran CAD subscription version.
---

# Get Version

{% swagger baseUrl="https://api.sonorancad.com" path="/general/get_version" method="post" summary="Get Version" %}
{% swagger-description %}
This API endpoint gets the current plan used by the community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_VERSION
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
0 - FREE
1 - STARTER
2 - STANDARD
3 - PLUS
4 - PRO
6 - SONORAN ONE
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
    "type": "GET_VERSION",
    "data": []
}
```
