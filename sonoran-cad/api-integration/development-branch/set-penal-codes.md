---
description: >-
  This API endpoint allows communities with a large number of penal codes to set
  them easily with a single API call.
---

# Set Penal Codes

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general" %}
{% api-method-summary %}
Set Penal Codes
{% endapi-method-summary %}

{% api-method-description %}
This API endpoint allows communities with a large number of penal codes to set them easily with a single API call.
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
SET\_PENAL\_CODES
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
PENAL CODES SET!
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
    "type": "SET_API_ID",
    "data": [
      {
       "code": "(2)06",
       "type": "Felony",
       "title": "Armed Robbery",
       "bondType": "Federal Bail Bond",
       "jailTime": "5-10 Years",
       "bondAmount": 20000
			 },
			 {
			  "code": "(2)07",
    	  "type": "Felony",
    	  "title": "Murder",
    	  "bondType": "Federal Bail Bond",
        "jailTime": "5-50 Years",
    	  "bondAmount": 100000
			 }
    ]
}
```

### Penal Code Format

Your penal codes must be sent as a JSON object array in the exact format shown. Depending on how your community's penal codes are structure, you may want to write a script to automate this formatting. Then, send your penal codes via API with something like [Postman](https://www.postman.com/).

![Penal Codes set via API](../../../.gitbook/assets/image%20%2859%29.png)

