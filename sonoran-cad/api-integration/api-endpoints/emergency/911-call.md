---
description: >-
  The 911 Call API endpoint allows you to send 911 calls from in-game directly
  to your dispatchers.
---

# 911 Call

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/call_911" method="post" summary="Emergency Call" %}
{% swagger-description %}
The 911 call API endpoint allows you to send 911 calls from in-game directly to your dispatchers.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
CALL_911
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of emergency call objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
EMERGENCY CALL ADDED ID: {ID}
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response" %}
```
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

### Server ID

Because Sonoran CAD allows you to separate units and dispatchers into separate servers, the serverId field ensures this emergency call is sent to the appropriate dispatcher.\
\
For more information, see our guide on [configuring multiple servers](../../../../tutorials/customization/configuring-multiple-servers.md).

### Meta Data

The `metaData` object can be used to store custom API data in the 911 call.

Additionally, the following `metaData` properties will auto-set the dispatch call information:

| Property   | Type    | Description                                        |
| ---------- | ------- | -------------------------------------------------- |
| `priority` | Integer | <p>Dispatch call priority</p><p>Values 1, 2, 3</p> |
| `block`    | String  | Dispatch Call Block                                |
| `postal`   | String  | Dispatch Call Postal                               |
| `code`     | String  | Dispatch Call 10-Code                              |
