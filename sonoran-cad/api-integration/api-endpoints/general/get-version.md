---
description: This endpoint allows you to check your Sonoran CAD subscription version.
---

# Get Version

{% api-method method="post" host="https://api.sonorancad.com" path="/general/get\_version" %}
{% api-method-summary %}
Get Version
{% endapi-method-summary %}

{% api-method-description %}
This API endpoint gets the current plan used by the community.
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
GET\_VERSION
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of request objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```text
0 - FREE
1 - STARTER
2 - STANDARD
3 - PLUS
4 - PRO
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
    "type": "GET_VERSION",
    "data": []
}
```

