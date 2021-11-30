---
description: >-
  This endpoint allows you to update an existing character associated with an
  account in the CAD.
---

# Edit Character

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
Characters can NOT be edited in communities using [Database Sync](../../../../integration-plugins/database-sync-and-merge/), as all characters are pulled from your server's in-game database.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/civilian/edit_character" method="post" summary="Edit Character" %}
{% swagger-description %}
This endpoint allows you to update an existing character associated with an account in the CAD.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
EDIT_CHARACTER
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of character objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
CHARACTER {ID} EDITED FOR {USERNAME}
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
    "type": "EDIT_CHARACTER",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID - Typically, this is their Steam Hex
            "character": {}, // Custom character record
        },
    ]
}
```

#### Record Formatting

Custom records require a strict format with several dozen different data fields. You can view a detailed explanation of [custom record formatting](../general/custom-records/#record-formatting).&#x20;
