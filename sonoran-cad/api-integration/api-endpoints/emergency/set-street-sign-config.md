---
description: This endpoint sets your community's street sign configuration.
---

# Set Street Sign Config

{% hint style="warning" %}
This API endpoint requires the **pro **version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/SET_STREETSIGN_CONFIG" method="post" summary="Set Street Sign Config" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
SET_STREETSIGN_CONFIG
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
API ID(s) set!
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
    "type": "SET_STREETSIGN_CONFIG",
    "data": [
        {
          "serverId": 1, // Server Id
          "signConfig": [
              {
                  "id": 1,
                  "label": "Some street sign",
                  "text1": "",
                  "text2": "",
                  "text3": ""
              },
              {
                  "id": 2,
                  "label": "Another street sign",
                  "text1": "",
                  "text2": "",
                  "text3": ""
              }
          ]
		    }
    ]
}
```
