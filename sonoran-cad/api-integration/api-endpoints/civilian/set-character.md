---
description: >-
  This endpoint allows you to set a user's currently selected character in the
  CAD.
---

# Set Character

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/set_character" method="post" summary="Get Characters" %}
{% swagger-description %}
This endpoint allows you to set a user's currently selected character in the CAD.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_CHARACTERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of character objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```javascript
// Array of custom record character objects
[]
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
    "type": "SET_CHARACTER",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID, Typically, this is their STEAM Hex
            "charId": 123, // ID of character, matches the GET_CHARACTERS result - either the `id` or `syncId` depending on whether or not DB sync is enabled
        },
    ]
}
```
