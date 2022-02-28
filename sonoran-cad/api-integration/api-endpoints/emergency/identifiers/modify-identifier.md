---
description: This endpoint allows you to add, edit, or remove unit identifiers.
---

# Modify Identifier



{% hint style="warning" %}
This API endpoint requires the **Pro** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/modify_identifiers" method="post" summary="Modify Identifier" %}
{% swagger-description %}
This endpoint allows you to retrieve all unit identifiers for a specified account in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
MODIFY_IDENTIFIER
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```javascript
// ADD or EDIT
{
    // Unit Identifier Object
}

// REMOVE
"Identifier 123 removed!"
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
{% endswagger %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "MODIFY_IDENTIFIER",
    "data": [
        {
            "apiId": "Steam:1234", // Generally the Steam HEX
            "action": 0, // ADD
            "identifier": {
                // OPTIONAL: Only for ADD & EDIT actions
                // Identifier/unit object
            },
            "identId": 123 // OPTIONAL: Only for REMOVE action
        }
    ]
}
```

### Action Enum

The `action` property is an enumerator value with the following values:

| Enum (Int) | Description |
| ---------- | ----------- |
| 0          | ADD         |
| 1          | EDIT        |
| 2          | REMOVE      |
