---
description: >-
  Sonoran CAD allows you to manually add or remove user account permissions via
  API.
---

# Modify Account Permissions

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general/set\_account\_permissions" %}
{% api-method-summary %}
Modify Account Permissions
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to apply a permission key to a user in your community.
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
SET\_ACCOUNT\_PERMISSIONS
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of user account permission objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
User account permissions updated.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following 400 errors may be sent in response:
{% endapi-method-response-example-description %}

```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
A non-linked API ID will be met with the following response:
{% endapi-method-response-example-description %}

```
API ID NOT LINKED TO AN ACCOUNT IN THIS COMMUNITY
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "SET_ACCOUNT_PERMISSIONS",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID entered in the unit identifiers
                                   // Typically, this is their STEAM ID
            "permissions": [       // Array of permission names
                "POLICE",
                "POLICERECEDIT"
            ],
            "addPerm": true // Whether to ADD or REMOVE these permissions from the user
        },
    ]
}
```

| Permission String Name | Description |
| :--- | :--- |
| CIVILIAN | Access to the Civilian page |
| LAWYER | Access to the Law page |
| DMV | Access to the DMV page |
| POLICE | Access to the Police page |
| FIRE | Access to the Fire page |
| EMS | Access to the EMS page |
| DISPATCH | Access to the Dispatch page |
| ADMIN | Access to the Admin page |
| POLRECADD | Permission to add police records |
| POLRECEDIT | Permission to edit police records |
| POLRECREMOVE | Permission to remove police records |
| POLSUPER | Permission to modify police record supervisor fields |
| POLEDITUNIT | Permission to edit their unit identifier |
| POLEDITOTHERUNIT | Permission to edit other unit identifiers |
| SELFDISPATCH | Permission to enable self dispatch |
| MEDRECADD | Permission to add medical records |
| MEDRECEDIT | Permission to edit medical records |
| MEDRECREMOVE | Permission to remove medical records |
| MEDSUPER | Permission to modify medical record supervisor fields |
| FIRERECADD | Permission to add fire records |
| FIRERECEDIT | Permission to edit fire records |
| FIRERECREMOVE | Permission to remove fire records |
| FIRESUPER | Permission to modify fire record supervisor fields |
| DMVRECADD | Permission to add DMV records |
| DMVRECEDIT | Permission to edit DMV records |
| DMVRECREMOVE | Permission to remove DMV records |
| DMVSUPER | Permission to modify DMV record supervisor fields |
| LAWRECADD | Permission to add law records |
| LAWRECEDIT | Permission to edit law records |
| LAWRECREMOVE | Permission to remove law records |
| LAWSUPER | Permission to modify law record supervisor fields |
| ADMINACCOUNTS | Permission to view/modify user accounts |
| ADMINPERMISSIONKEYS | Permission to view/modify permission keys |
| ADMINCUSTOMIZATION | Permission to access the admin customization menu |
| ADMINDEPARTMENTS | Permission to modify the department structure |
| ADMINTENCODES | Permission to modify the 10-codes |
| ADMINPENALCODES | Permission to modify the penal codes |
| ADMININGAMEINTEGRATION | Permission to access the in-game integration panel |
| ADMINDISCORDINTEGRATION | Permission to access the Discord integration panel |
| ADMINLIMITS | Permission to view the community limits panel |

