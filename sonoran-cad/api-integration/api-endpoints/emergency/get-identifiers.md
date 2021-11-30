---
description: >-
  Sonoran CAD allows you to retrieve all account unit identifiers via API
  endpoint.
---

# Get Account Identifiers

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/get_account_identifiers" method="post" summary="Get Account Identifiers" %}
{% swagger-description %}
This endpoint allows you to retrieve all unit identifiers for a specified account in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_ACCOUNT_IDENTIFIERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
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
{% tab title="UNIT_STATUS" %}
| nteger (Enumeration) Value | Status Description |
| -------------------------- | ------------------ |
| 0                          | UNAVAILABLE        |
| 1                          | BUSY               |
| 2                          | AVAILABLE          |
| 3                          | ENROUTE            |
| 4                          | ON\_SCENE          |
{% endtab %}
{% endtabs %}
