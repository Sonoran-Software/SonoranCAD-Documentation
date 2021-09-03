---
description: >-
  This endpoint allows you to retrieve all active emergency calls, active
  dispatch calls, and previously closed dispatch calls.
---

# Get Calls

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/get\_calls" %}
{% api-method-summary %}
Get Calls
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve all active emergency calls, active dispatch calls, and previously closed dispatch calls.
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
GET\_CALLS
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
{
    // See below for full object structuring
    "activeCalls": [], // DISPATCH CALL Array
    "emergencyCalls": [], // EMERGENCY CALL Array
    "closedCalls": [], // CLOSED CALL Array
}
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
    "type": "GET_CALLS",
    "data": [
        {
            "serverId": 1 // Default 1 - See out guide on setting up multiple servers
        },
    ]
}
```

### Object Structuring

The GET\_CALLS API endpoint returns arrays of the following object structures:

{% tabs %}
{% tab title="Dispatch Call" %}
```javascript
{
    "callId": -1,
    "origin": 0, // See ORIGIN Enum
    "status": 0, // See CALL_STATUS Enum
    "priority": 1, // 1, 2, or 3
    "block": "123",
    "address": "4234 E. Example Ave",
    "postal": "456",
    "title": "Traffic Stop",
    "code": "10-39 - Traffic Stop",
    "description": "Traffic Stop - Blue Sedan - XP123BS",
    "notes": "",
    "units": [
     {
         "id": -1,
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
     },
    ] // Array of Unit structures
}
```
{% endtab %}

{% tab title="Emergency Call" %}
```javascript
{
    "callId": -1,
    "isEmergency": false, // CIVIL or EMERGENCY
    "caller": "John Doe",
    "location": "1234 E. Test Ave",
    "description": "Help, my cat is stuck in a tree!"
}
```
{% endtab %}
{% endtabs %}

### Enumeration Values

Sonoran CAD uses integer enumeration values for the `origin` and `status` fields. See the tables below for more information.

{% tabs %}
{% tab title="ORIGIN" %}
| Integer \(Enumeration\) Value | Origin Description |
| :--- | :--- |
| 0 | CALLER |
| 1 | RADIO DISPATCH |
| 2 | OBSERVED |
| 3 | WALK\_UP |
{% endtab %}

{% tab title="CALL\_STATUS" %}
| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | PENDING |
| 1 | ACTIVE |
| 2 | CLOSED |
{% endtab %}

{% tab title="UNIT\_STATUS" %}
These represent the default [unit status](../../../../tutorials/customization/unit-status-codes.md) options.

| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | UNAVAILABLE |
| 1 | BUSY |
| 2 | AVAILABLE |
| 3 | ENROUTE |
| 4 | ON\_SCENE |
{% endtab %}
{% endtabs %}

