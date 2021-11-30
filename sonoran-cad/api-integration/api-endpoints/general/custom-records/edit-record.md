---
description: >-
  Sonoran CAD allows you to easily modify an existing custom record in your
  community via API.
---

# Edit Record

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/edit_record" method="post" summary="Edit Record" %}
{% swagger-description %}
This endpoint allows you to modify an existing custom record to your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
EDIT_RECORD
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of record objects
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{UPDATED RECORD OBJECT}
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

Or, view a detailed explanation of [custom record formatting](./#record-formatting).&#x20;
