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
            "user": "STEAM:1234",  // API ID or user UUID/GUID that 'owns' this record
            "useDictionary": true, // OPTION 1: Key/Value from template
            "recordId": 123,       // OPTION 1: Record ID being modified
            "replaceValues": {
                // Field UID and Value
                "first": "Brian",
                "last": "Sosnowski"
            },
            "record": null,        // OPTION 2: Full raw JSON structure
        }
    ]
}
```

### Formatting Data for Custom Records

Custom records can be easily modified with a set of key/value pairs, or full raw JSON.

Learn more about these formatting options below:

{% content-ref url="api-options-for-adding-and-modifying-records.md" %}
[api-options-for-adding-and-modifying-records.md](api-options-for-adding-and-modifying-records.md)
{% endcontent-ref %}
