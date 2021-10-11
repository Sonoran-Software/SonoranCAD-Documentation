---
description: This endpoint allows you to add a new character to an existing user account.
---

# New Character

{% hint style="warning" %}
This API endpoint requires the **plus **version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
New characters can NOT be added to communities using [Database Sync](broken-reference), as all characters are pulled from your server's in-game database.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/new_character" method="post" summary="New Character" %}
{% swagger-description %}
This endpoint allows you to add a new character to an existing user account.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
NEW_CHARACTER
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of character objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
NEW CHARACTER ADDED TO {{ USERNAME }}
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
    "type": "NEW_CHARACTER",
    "data": [
        {
            "apiId": "STEAN:1234", // API ID, Typically, this is their STEAM Hex
            "character": {} // Custom character record
        },
    ]
}
```

#### Record Formatting

Custom records require a strict format with several dozen different data fields. You can view a detailed explanation of [custom record formatting](../general/custom-records/#record-formatting). 
