---
description: >-
  This endpoint allows you to retrieve your community's server configuration.
  This contains valuable Live Map configuration data and can be used to ensure
  correct Live Map configs.
---

# Get Servers

{% hint style="warning" %}
API endpoint requires the **Plus** version of Sonoran CAD or higher.  
For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general/get\_servers" %}
{% api-method-summary %}
Get Servers
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve your community's server configuration. This contains valuable Live Map configuration data and can be used to ensure correct Live Map configs.
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
GET\_SERVERS
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
    "type": "GET_SERVERS",
    "data": []
}
```

