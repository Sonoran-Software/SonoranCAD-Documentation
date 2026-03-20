---
description: This endpoint retrieves your community's Inferno Pager node configuration for a specific server.
---

# Get Pager Config

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/GET_PAGER_CONFIG" method="post" summary="Get Pager Config" %}
{% swagger-description %}
This endpoint retrieves the Inferno Pager configuration for a specific server in your community.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
GET_PAGER_CONFIG
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```json
[
    {
        "id": "root-1",
        "name": "Fire",
        "description": "Fire services",
        "permission": "fire",
        "address": "FIRE-01",
        "shortCode": "F1",
        "kind": "group",
        "children": [
            {
                "id": "station-1",
                "name": "Station 1",
                "description": "",
                "permission": "fire.station1",
                "address": "FIRE-ST01",
                "shortCode": "ST1",
                "kind": "node",
                "children": []
            }
        ]
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
    "type": "GET_PAGER_CONFIG",
    "data": [
        {
            "serverId": 1 // Server ID
        }
    ]
}
```

The returned configuration is per-server, matching the Station Alert configuration pattern.
