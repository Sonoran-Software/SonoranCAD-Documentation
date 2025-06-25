---
description: This endpoint allows you to remove a character associated with a CAD account.
---

# Remove Character

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
Characters can NOT be removed from communities using [Database Sync](../../../../integration-plugins/database-sync-and-merge/), as all characters are pulled from your server's in-game database.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/remove_character" method="post" summary="Remove Character" %}
{% swagger-description %}
This endpoint allows you to remove a character associated with a CAD account.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
REMOVE_CHARACTER
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of character objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
CHARACTER {ID} REMOVED FOR {USERNAME}
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

{% swagger-response status="404" description="" %}
```
API ID NOT LINKED TO AN ACCOUNT IN THIS COMMUNITY
```
{% endswagger-response %}
{% endswagger %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "REMOVE_CHARACTER",
    "data": [
        {
            "id": -1, // Unique character ID - Use GET_CHARACTERS to retrieve
        },
    ]
}
```
