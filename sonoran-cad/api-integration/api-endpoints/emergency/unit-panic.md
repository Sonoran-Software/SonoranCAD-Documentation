---
description: >-
  The Unit Panic API call allows you to automatically trigger a unit panic from
  in-game.
---

# Unit Panic

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/unit\_panic" %}
{% api-method-summary %}
Unit Panic
{% endapi-method-summary %}

{% api-method-description %}
This The unit panic API endpoint allows you to automatically trigger a unit panic from in-game.
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
UNIT\_PANIC
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of unit objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
UNIT PANIC UPDATED
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following errors may be sent in response:
{% endapi-method-response-example-description %}

```
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
    "type": "UNIT_PANIC",
    "data": [
        {
            "apiId": "STEAM:5678",
            "isPanic": true,
        }
    ]
}
```

