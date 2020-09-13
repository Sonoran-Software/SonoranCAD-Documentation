---
description: Sonoran CAD allows you to retrieve detailed user account data via API.
---

# Get Account

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general/get\_account" %}
{% api-method-summary %}
Get Account
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve information on a specified account in your community.
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
GET\_ACCOUNT
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
// Account Object
  {
    "uuid": "91de0ce8-c571-11e9-9714-5600023b2434",
    "username": "SonoranBrian",
    "status": 1,
    "joined": "2019-10-12T20:41:52.400299",
    "lastLogin": "2020-08-15T13:43:17.607111",
    "permissions": {
      "civilian": true,
      "lawyer": true,
      "dmv": true,
      "police": true,
      "fire": true,
      "ems": true,
      "dispatch": true,
      "admin": true,
      "polRecAdd": true,
      "polRecEdit": true,
      "polRecRemove": true,
      "polSuper": true,
      "polEditUnit": true,
      "polEditOtherUnit": true,
      "selfDispatch": true,
      "medRecAdd": true,
      "medRecEdit": true,
      "medRecRemove": true,
      "medSuper": true,
      "fireRecAdd": true,
      "fireRecEdit": true,
      "fireRecRemove": true,
      "fireSuper": true,
      "dmvRecAdd": true,
      "dmvRecEdit": true,
      "dmvRecRemove": true,
      "dmvSuper": true,
      "lawRecAdd": true,
      "lawRecEdit": true,
      "lawRecRemove": true,
      "lawSuper": true,
      "adminAccounts": true,
      "adminPermissionKeys": true,
      "adminCustomization": true,
      "adminDepartments": true,
      "adminTenCodes": true,
      "adminPenalCodes": true,
      "adminInGameIntegration": true,
      "adminDiscordIntegration": true,
      "adminLimits": true,
      "adminLogs": true
    },
    "apiIds": [
      "123456",
      ""
    ]
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
    "type": "GET_ACCOUNT",
    "data": [
        {
            "apiId": "Steam:1234" // Generally the Steam HEX
        },
    ]
}
```

