---
description: >-
  Sonoran CAD allows you to retrieve your custom record and report templates via
  API.
---

# Get Record Templates

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general" %}
{% api-method-summary %}
New Record
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve all custom record and report templates in your community.
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
GET\_TEMPLATES
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Empty Array
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[{RECORD TEMPLATES}]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "GET_TEMPLATES",
    "data": [
        // Array left empty to stay consistent with other API call formatting
    ]
}
```

#### Record Formatting

Custom records require a strict format with several dozen different data fields. You can view a detailed explanation of [custom record formatting](get-record-template.md). 

