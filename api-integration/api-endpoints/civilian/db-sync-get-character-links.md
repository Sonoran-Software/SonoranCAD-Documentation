---
description: >-
  This endpoint allows you to get a user's currently linked DB sync character
  IDs in the CAD.
---

# DB Sync: Get Character Links

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/get_character_links" method="post" summary="Get Character Links" %}
{% swagger-description %}
This endpoint allows you to get a user's currently linked DB sync character IDs in the CAD.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET\_CHARACTERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of character objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```javascript
// Array of character sync IDs
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
    "type": "GET_CHARACTER_LINKS",
    "data": [
        {
            "apiId": "STEAM:1234" // API ID, Typically, this is their STEAM Hex
    ]
}
```

#### Sync ID

The `syncId` parameter is the unique identifier for your DB sync character. This will match the values found in the `Character Mapping Column` in your DB sync config.
