---
description: >-
  The dispatch event sends dispatch call information to your community when a
  dispatch call is created, modified, or closed.
---

# Dispatch Event

### EVENT\_DISPATCH POST

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_DISPATCH",
    "data": [
        {
            "dispatch_type": 0, // See DISPATCH_TYPE Enum
            "dispatch": {
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
                "units": [ // Array of Unit structures
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
                ]
            }
        }
    ]
}
```

### Enumeration Values

Sonoran CAD uses integer enumeration values for the `DISPATCH_TYPE`, `ORIGIN` and `STATUS` fields. See the tables below for more information.

{% tabs %}
{% tab title="DISPATCH\_TYPE" %}
| Integer \(Enumeration\) Value | Dispatch Type Description |
| :--- | :--- |
| 0 | CALL\_NEW |
| 1 | CALL\_EDIT |
| 2 | CALL\_CLOSE |
| 3 | CALL\_NOTE |
| 4 | CALL\_SELF\_CLEAR |
{% endtab %}

{% tab title="ORIGIN" %}
| Integer \(Enumeration\) Value | Origin Description |
| :--- | :--- |
| 0 | CALLER |
| 1 | RADIO DISPATCH |
| 2 | OBSERVED |
| 3 | WALK\_UP |
{% endtab %}

{% tab title="STATUS" %}
| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | PENDING |
| 1 | ACTIVE |
| 2 | CLOSED |
{% endtab %}
{% endtabs %}

