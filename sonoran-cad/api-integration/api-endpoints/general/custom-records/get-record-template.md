---
description: >-
  Sonoran CAD allows you to retrieve your custom record and report templates via
  API.
---

# Get Record Templates

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/get_templates" method="post" summary="Get Record Templates" %}
{% swagger-description %}
This endpoint allows you to retrieve all custom record and report templates in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="templateId" type="number" %}
Unique template ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_TEMPLATES
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Empty Array
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
[{RECORD TEMPLATES}]
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}
{% endswagger %}

```javascript
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "GET_TEMPLATES",
    "templateId": 123, // OPTIONAL - Matches a specific record's recordTypeId field
}
```

#### Record Formatting

Custom records require a strict format with several dozen different data fields. You can view a detailed explanation of [custom record formatting](./#record-formatting).&#x20;
