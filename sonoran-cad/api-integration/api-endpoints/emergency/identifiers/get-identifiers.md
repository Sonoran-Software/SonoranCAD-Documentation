---
description: >-
  Sonoran CAD allows you to retrieve all account unit identifiers via API
  endpoint.
---

# Get Identifiers

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/get_identifiers" method="post" summary="Get Account Identifiers" %}
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
GET_IDENTIFIERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```javascript
{
    "selectedIdent": 1,
    "identifiers": [
        // Array of unit objects
    ]
}
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
    "type": "GET_IDENTIFIERS",
    "data": [
        {
            "apiId": "Steam:1234", // Generally the Steam HEX
        }
    ]
}
```
