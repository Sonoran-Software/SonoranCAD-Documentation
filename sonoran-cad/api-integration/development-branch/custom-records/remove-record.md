---
description: >-
  This endpoint allows you to remove any record retrieved from a LOOKUP_NAME or
  LOOKUP_PLATE request.
---

# Remove Record

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general" %}
{% api-method-summary %}
Remove Record
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to remove any record retrieved from a LOOKUP\_NAME or LOOKUP\_PLATE request.
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
REMOVE\_RECORD
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
REMOVED RECORD {ID}
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
    "type": "REMOVE_RECORD",
    "data": [
        {
            "id": 100, // Unique ID - Retrieved from LOOKUP_NAME or LOOKUP_PLATE
        },
    ]
}
```

