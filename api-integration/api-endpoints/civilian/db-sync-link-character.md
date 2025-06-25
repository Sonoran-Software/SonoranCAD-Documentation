---
description: >-
  This endpoint allows you to set a user's currently linked DB sync characters
  in the CAD.
---

# DB Sync: Link Character



{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/link_character" method="post" summary="Set Character Links" %}
{% swagger-description %}
This endpoint allows you to set a user's currently linked DB sync characters in the CAD.
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
Linked char sync ID '{linkId}' to user '{username}' - {User UUID}
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
    "type": "LINK_CHARACTER",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID, Typically, this is their STEAM Hex
            "syncId": "", // DB Sync ID of character, matches the GET_CHARACTERS result`syncId`
            "action": 0 // 0: ADD, 2: REMOVE
    ]
}
```

#### Sync ID

The `syncId` parameter is the unique identifier for your DB sync character. This will match the values found in the `Character Mapping Column` in your DB sync config.
