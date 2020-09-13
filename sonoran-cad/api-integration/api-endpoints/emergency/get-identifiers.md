---
description: >-
  Sonoran CAD allows you to retrieve all account unit identifiers via API
  endpoint.
---

# Get Account Identifiers

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/get\_account\_identifiers" %}
{% api-method-summary %}
Get Active Units
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve all unit identifiers for a specified account in your community.
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
GET\_ACCOUNT\_IDENTIFIERS
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

```javascript
// Array of unit objects
[
    {
     "id": -1, // Unique Identifier ID
     "accId": "123-456-7890", // Account UUID
     "status": 0, // See UNIT_STATUS Enum
     "isPanic": false, // PANIC State
     "location": "1234 E. Test Ave",
     "aop": "South District",
     "data": {
             "apiId1": "STEAM:1234", // API ID - Typically Steam Hex
             "apiId2": "STEAM:1234", // API ID - Typically Steam Hex
             "unitNum": "A-10",
             "name": "Brian Sosnowski",
             "district": "Maricopa County",
             "department": "MCSO",
             "subdivision": "Speed Enforcement",
             "rank": "CPT",
             "group": "CAR 51", // Name of unit group
             }
     }
]
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
    "type": "GET_ACCOUNT_IDENTIFIERS",
    "data": [
        {
            "serverId": 1 // Default 1 - See guide on setting up multiple servers
            "apiId": "Steam:1234", // Generally the Steam HEX
            "onlyOnline": false, // Only get identifier that this user has online
        },
    ]
}
```



### Enumeration Values

Sonoran CAD uses integer enumeration values for the unit's `status` fields. See the tables below for more information. These represent the default [unit status](../../../../tutorials/customization/unit-status-codes.md) options.

{% tabs %}
{% tab title="UNIT\_STATUS" %}
| nteger \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | UNAVAILABLE |
| 1 | BUSY |
| 2 | AVAILABLE |
| 3 | ENROUTE |
| 4 | ON\_SCENE |
{% endtab %}
{% endtabs %}

