---
description: >-
  This endpoint allows you to remove any record retrieved from a LOOKUP_NAME or
  LOOKUP_PLATE request.
---

# Remove Record

{% hint style="warning" %}
This API endpoint requires the **Plus **version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/remove_record" method="post" summary="Remove Record" %}
{% swagger-description %}
This endpoint allows you to remove any record in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
REMOVE_RECORD
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of unit status objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
REMOVED RECORD {ID}
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
    "type": "REMOVE_RECORD",
    "data": [
        {
            "id": 100, // Unique ID - Retrieved from LOOKUP_NAME or LOOKUP_PLATE
        },
    ]
}
```
