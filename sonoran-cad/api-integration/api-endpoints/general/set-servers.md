---
description: This endpoint allows you to update your CAD's server configuration.
---

# Set Servers

{% hint style="warning" %}
API endpoint requires the **Plus **version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/set_servers" method="post" summary="Set Servers" %}
{% swagger-description %}
This endpoint allows you to set your community's server configuration and update the live map deployment. This contains additional valuable Live Map configuration data.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
SET_SERVERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Server config updated
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
    "type": "GET_SERVERS",
    "data": {
        "servers": [
            {
                "id": 1,
                "name": "Server 1",
                "description": "Main Server",
                "signal": "",
                "mapUrl": "",
                "mapIp": "",
                "mapPort" 0,
                "listenerPort": 3232,
                "differingOutbound": false, // Different outbound/egress IP than the mapIp
                "outboundIp": "",
                "mapPort": 30121,
                "enableMap": true,
                "isStatic": false,
                "mapType": "NORMAL",
            }
        ]
        "deployMap": true // Deploy the Live Map with these server changes
    },
}
```
