---
description: This endpoint authenticates the use of our integrated street signs plugin.
---

# Auth Street Signs

{% hint style="warning" %}
This API endpoint requires the **Pro **version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/auth_streetsigns" method="post" summary="Authenticate Street Signs" %}
{% swagger-description %}
This endpoint authenticates the use of our integrated street signs plugin.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
AUTH_STREETSIGNS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="object" %}
Request object
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Success
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
Error: Server ID: x has IP set to: '1.2.3.4' -> your IP: '4.3.2.1'
Server not found with ID: 123
```
{% endswagger-response %}
{% endswagger %}

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
