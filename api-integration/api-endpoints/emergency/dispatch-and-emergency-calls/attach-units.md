---
description: This endpoint allows you to attach new units to an existing dispatch call.
---

# Attach Unit

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

## Attach Unit

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/emergency/attach_unit`

This endpoint allows you to attach new units to an existing dispatch call.

#### Request Body

| Name | Type   | Description              |
| ---- | ------ | ------------------------ |
| id   | string | Your community's ID      |
| key  | string | Your community's API Key |
| type | string | ATTACH\_UNIT             |
| data | array  | Array of request objects |

{% tabs %}
{% tab title="200 A successful call will be met with the following response:" %}
```
UNITS ATTACHED
```
{% endtab %}

{% tab title="400 The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endtab %}
{% endtabs %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "ATTACH_UNIT",
    "data": [
        {
            "serverId": 1, // Default 1 - See guide on setting up multiple servers
            "callId": 100, // Can be retrieved from the GET_CALLS API endpoint
            "units": ["STEAM:1234"], // OPTION 1: Array of API IDs
                                // Typically, this is their STEAM Hex
            "account": "000-000-0000" // OPTION 2: Attach unit via account UUID
        },
    ]
}
```
