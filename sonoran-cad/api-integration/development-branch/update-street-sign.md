---
description: This endpoint allows you to modify existing street signs.
---

# Update Street Sign

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.  
For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/UPDATE\_STREETSIGN" %}
{% api-method-summary %}
Update Street Sign
{% endapi-method-summary %}

{% api-method-description %}

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
UPDATE\_STREETSIGN
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of request objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
API ID(s) set!
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "UPDATE_STREETSIGN",
    "data": [
        {
          "serverId": 1, // Server Id
          "signData": {
              "ids": [1, 2],
              "text1": "",
              "text2": "",
              "text3": ""
          }
		    }
    ]
}
```

