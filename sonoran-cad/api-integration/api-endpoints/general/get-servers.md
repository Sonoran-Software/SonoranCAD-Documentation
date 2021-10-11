---
description: >-
  This endpoint allows you to retrieve your community's server configuration.
  This contains valuable Live Map configuration data and can be used to ensure
  correct Live Map configs.
---

# Get Servers

{% hint style="warning" %}
API endpoint requires the **Plus **version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/get_servers" method="post" summary="Get Servers" %}
{% swagger-description %}
This endpoint allows you to retrieve your community's server configuration. This contains valuable Live Map configuration data and can be used to ensure correct Live Map configs.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
GET_SERVERS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
{
  "servers": [
    {
      "id": 1,
      "name": "Server 1",
      "description": "Default server description",
      "signal": null,
      "mapUrl": "https://cadapi.dev.sonoransoftware.com/map/community/map_example/index.html",
      "mapIp": "123.456.78.9",
      "mapPort": "30121",
      "differingOutbound": false, // Different outbound/egress IP than the mapIp
      "outboundIp": "",
      "listenerPort": "0000",
      "enableMap": false,
      "mapType": "POSTAL",
      "isStatic": false
    }
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
    "type": "GET_SERVERS",
    "data": []
}
```
