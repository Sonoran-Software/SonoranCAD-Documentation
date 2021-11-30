---
description: Sonoran CAD allows you to retrieve detailed user account data via API.
---

# Get Account

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/get_account" method="post" summary="Get Account" %}
{% swagger-description %}
This endpoint allows you to retrieve information on a specified account in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_ACCOUNT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
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
    "type": "GET_ACCOUNT",
    "data": [
        {
            "apiId": "Steam:1234", // Generally the Steam HEX
            "username": "SonoranBrian", // Sonoran CAD Username
        },
    ]
}
```

### Search Type

The search can be by the user's `apiId` or their Sonoran CAD account `username`.
