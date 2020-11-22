---
description: This endpoint allows you to add a new character to an existing user account.
---

# New Character

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
New characters can NOT be added to communities using [Database Sync](), as all characters are pulled from your server's in-game database.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/civilian/new\_character" %}
{% api-method-summary %}
New Character
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to add a new character to an existing user account.
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
NEW\_CHARACTER
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
NEW CHARACTER ADDED TO {{ USERNAME }}
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

