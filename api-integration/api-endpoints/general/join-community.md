---
description: Adds a Sonoran account to your CAD.
---

# Join Community

{% hint style="warning" %}
This API endpoint is not available to the public and exists for internal documentation only for the CMS program.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/sso/community" method="post" summary="Join Community" %}
{% swagger-description %}
This endpoint allows you to retrieve your community's server configuration. This contains valuable Live Map configuration data and can be used to ensure correct Live Map configs.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
JOIN_COMMUNITY
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-parameter in="body" name="internalKey" type="N/A" required="true" %}
Key for internal use only, not open to the public
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
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
    "internalKey": "" // Not disclosed to public
    "type": "JOIN_COMMUNITY",
    "data": [
        {
            "account": "000-000-000-000" // Account UUID
        }
    ]
}
```
