---
description: This endpoint allows you to kick or ban a user account in your community.
---

# Kick or Ban User

{% hint style="warning" %}
This API endpoint requires the **plus **version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/ban_user" method="post" summary="Ban User" %}
{% swagger-description %}
This endpoint allows you to ban a user account in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
BAN_USER
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of user account ban objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
User Ban: {{ ACCOUNT UUID }} Status: {{ isBan }}
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}

{% swagger-response status="404" description="A non-linked API ID will be met with the following response:" %}
```
API ID NOT LINKED TO AN ACCOUNT IN THIS COMMUNITY
```
{% endswagger-response %}
{% endswagger %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "BAN_USER",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID entered in the unit identifiers
                                   // Typically, this is their STEAM ID
            "isBan": true, // OPTIONAL: Ban (true) or un-ban (false)
            "isKick": false // OPTIONAL: Kick instead of ban
        },
    ]
}
```
