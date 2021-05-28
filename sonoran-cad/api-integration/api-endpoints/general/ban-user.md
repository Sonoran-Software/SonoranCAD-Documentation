---
description: This endpoint allows you to kick or ban a user account in your community.
---

# Kick or Ban User

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general/ban\_user" %}
{% api-method-summary %}
Ban User
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to ban a user account in your community.
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
BAN\_USER
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of user account ban objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
User Ban: {{ ACCOUNT UUID }} Status: {{ isBan }}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following 400 errors may be sent in response:
{% endapi-method-response-example-description %}

```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
A non-linked API ID will be met with the following response:
{% endapi-method-response-example-description %}

```
API ID NOT LINKED TO AN ACCOUNT IN THIS COMMUNITY
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

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

