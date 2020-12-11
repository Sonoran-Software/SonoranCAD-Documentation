---
description: >-
  The 911 Call API endpoint allows you to send 911 calls from in-game directly
  to your dispatchers.
---

# 911 Call

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency/call\_911" %}
{% api-method-summary %}
Emergency Call
{% endapi-method-summary %}

{% api-method-description %}
The 911 call API endpoint allows you to send 911 calls from in-game directly to your dispatchers.
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
CALL\_911
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of emergency call objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
EMERGENCY CALL ADDED ID: {ID}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The following 400 errors may be sent in response
{% endapi-method-response-example-description %}

```
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
    "type": "CALL_911",
    "data": [
        {
            "serverId": 1, // Server ID Integer
            "isEmergency": true, // Displays EMERGENCY or CIVIL type in the CAD
            "caller": "John Doe",
            "location": "1234 E. Test St.",
            "description": "Help, someone is breaking into my house!",
            "metaData": {
                "someKey": "someValue" // OPTIONAL: metaData for API custom storage
            },
        }
    ]
}
```

#### Server ID

Because Sonoran CAD allows you to separate units and dispatchers into separate servers, the serverId field ensures this emergency call is sent to the appropriate dispatcher.  
  
For more information, see our guide on [configuring multiple servers](../../../../tutorials/customization/configuring-multiple-servers.md).

