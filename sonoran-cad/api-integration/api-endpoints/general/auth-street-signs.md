---
description: This endpoint authenticates the use of our integrated street signs plugin.
---

# Auth Street Signs

{% hint style="warning" %}
This API endpoint requires the **Pro** version of Sonoran CAD or higher.  
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general/auth\_streetsigns" %}
{% api-method-summary %}
Authenticate Street Signs
{% endapi-method-summary %}

{% api-method-description %}
This endpoint authenticates the use of our integrated street signs plugin.
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
AUTH\_STREETSIGNS
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="object" required=true %}
Request object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
Success
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following 400 errors may be sent in response:
{% endapi-method-response-example-description %}

```http
Error: Server ID: x has IP set to: '1.2.3.4' -> your IP: '4.3.2.1'
Server not found with ID: 123
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "AUTH_STREETSIGNS",
    "data": {
        "serverId": 1
    }
}
```

