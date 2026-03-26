---
description: This endpoint sets your community's Inferno Pager configuration for a specific server.
---

# Set Pager Config

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/SET_PAGER_CONFIG" method="post" summary="Set Pager Config" %}
{% swagger-description %}
This endpoint sets the Inferno Pager configuration for a specific server in your community. If `nodes` is omitted, the existing node tree for that server is preserved.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
SET_PAGER_CONFIG
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Updated pager config!
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
    "type": "SET_PAGER_CONFIG",
    "data": [
        {
            "serverId": 1,
            "natureWords": {
                "Emergency": "Emergency",
                "NonEmergency": "Non-Emergency",
                "Administrative": "Administrative"
            },
            "maxAddresses": 5,
            "maxBodyLength": 250,
            "nodes": [
                {
                    "id": "root-1",
                    "name": "Fire",
                    "description": "Fire services",
                    "permission": "fire",
                    "address": "FIRE-01",
                    "shortCode": "F1",
                    "kind": "group",
                    "children": []
                }
            ]
        }
    ]
}
```

The `nodes` property is optional. If omitted, Sonoran CAD keeps the existing node tree for that `serverId` and only updates the minimal config fields.
