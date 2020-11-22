---
description: This endpoint allows you to remove a character associated with a CAD account.
---

# Remove Character

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
Characters can NOT be removed from communities using [Database Sync](../../../../tutorials/in-game-integration/database-sync-and-merge.md), as all characters are pulled from your server's in-game database.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/civilian/remove\_character" %}
{% api-method-summary %}
Remove Character
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to remove a character associated with a CAD account.
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
REMOVE\_CHARACTER
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of character objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
CHARACTER {ID} REMOVED FOR {USERNAME}
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

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
    "type": "REMOVE_CHARACTER",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID - Typically, this is their Steam Hex
            "id": -1, // Unique character ID - Use GET_CHARACTERS to retrieve
        },
    ]
}
```

