---
description: This endpoint allows you to retrieve all active units in your CAD.
---

# Get Active Units

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/get_active_units" method="post" summary="Get Active Units" %}
{% swagger-description %}
This endpoint allows you to retrieve all active units in your CAD.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_ACTIVE_UNITS
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
     "isDispatch": false,
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
    "type": "GET_ACTIVE_UNITS",
    "data": [
        {
            "serverId": 1, // Default 1 - See guide on setting up multiple servers
            "onlyUnits": true, // Don't show active dispatchers (OPTIONAL: Default = TRUE if undefined)
            "includeOffline": false, // OPTIONAL: Don't show offline units
            "limit": 100, // OPTIONAL: Default's to max 100 results
            "offset": 0, // OPTIOANL: Default's to 0 (start position for limit)
        },
    ]
}
```



### Enumeration Values

Sonoran CAD uses integer enumeration values for the unit's `status` fields. See the tables below for more information. These represent the default [unit status](../../../../../tutorials/customization/unit-status-codes.md) options.

{% tabs %}
{% tab title="UNIT_STATUS" %}
| Integer (Enumeration) Value | Status Description |
| --------------------------- | ------------------ |
| 0                           | UNAVAILABLE        |
| 1                           | BUSY               |
| 2                           | AVAILABLE          |
| 3                           | ENROUTE            |
| 4                           | ON\_SCENE          |
{% endtab %}

{% tab title="PAGE" %}
The unit's `data.page` property reflects what page in the CAD the unit is viewing.

| Integer (Enumeration) Value | Description |
| --------------------------- | ----------- |
| 0                           | POLICE      |
| 1                           | FIRE        |
| 2                           | EMS         |
| 3                           | DISPATCH    |
{% endtab %}
{% endtabs %}

