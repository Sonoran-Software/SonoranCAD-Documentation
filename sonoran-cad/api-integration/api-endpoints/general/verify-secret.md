---
description: This endpoint verifies a user account's secret ID.
---

# Verify Secret

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/verify_secret" method="post" summary="Get Account" %}
{% swagger-description %}
This endpoint verifies a user account's secret ID.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
VERIFY_SECRET
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```javascript
// Dictionary of Account UUID (key) and Secret (value)
{"91de0ce8-c571-11e9-9714-5600023b2434" : "41d2169d-3079-4a05-b92d-df2af78e8b3e"}
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
    "type": "VERIFY_SECRET",
    "data": [
        {
            "secret": "0000-0000-0000-0000" // GUID/UUID
        },
    ]
}
```
