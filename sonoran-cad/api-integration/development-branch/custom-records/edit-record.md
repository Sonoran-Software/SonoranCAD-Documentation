---
description: >-
  Sonoran CAD allows you to easily modify an existing custom record in your
  community via API.
---

# Edit Record

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general" %}
{% api-method-summary %}
Edit Record
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to add a new custom record to your community.
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
EDIT\_RECORD
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of record objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{UPDATED RECORD OBJECT}
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
    "type": "EDIT_RECORD",
    "data": [
        {
            // Your record data here...
        },
    ]
}
```

#### Record Formatting

Custom records require a strict format with several dozen different data fields. Due to the complexity, it is highly recommended to create a new custom record template in the CAD UI, and then [retrieve the record template](get-record-template.md) for adding new records.

Or, view a detailed explanation of [custom record formatting](get-record-template.md). 

