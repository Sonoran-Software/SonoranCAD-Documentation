---
description: This event is sent when a unit is removed from an active dispatch call.
---

# Unit Call Clear

{% hint style="danger" %}
This event is currently not implemented in the latest `pushevents` plugin.
{% endhint %}

### EVENT\_UNIT\_CALL\_CLEAR

```javascript
{
    "key": "YOUR_API_KEY", // Authenticate legitimate event traffic
    "type": "EVENT_UNIT_CALL_CLEAR",
    "data": [
        {
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
                ]
            }
        }
    ]
}
```

### Enumeration Values

Sonoran CAD uses integer enumeration values for the unit `STATUS` field. See the tables below for more information. These values reflect the default [unit status](../../../tutorials/customization/unit-status-codes.md) options.

| Integer \(Enumeration\) Value | Status Description |
| :--- | :--- |
| 0 | UNAVAILABLE |
| 1 | BUSY |
| 2 | AVAILABLE |
| 3 | ENROUTE |
| 4 | ON\_SCENE |

