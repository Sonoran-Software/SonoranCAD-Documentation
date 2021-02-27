# Set Servers

{% api-method method="post" host="https://api.sonorancad.com" path="/general/set\_servers" %}
{% api-method-summary %}
Set Servers
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to set your community's server configuration and update the live map deployment. This contains additional valuable Live Map configuration data.
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
SET\_SERVERS
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
Server config updated
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
    "data": [
        {
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
                    "mapPort": 30121,
                    "enableMap": true,
                    "isStatic": false,
                    "mapType": "NORMAL",
                }
            ]
            "deployMap": true // Deploy the Live Map with these server changes
        },
    ]
}
```

