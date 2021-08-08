---
description: Have your plugin handle HTTP requests sent to a special URL.
---

# HTTP Request Handling

## Plugin Code

This code only works on the Server side files since HTTP only works on servers, obviously!

{% hint style="danger" %}
You **must** return something, even if it's just a confirmation the data was received. Otherwise, the HTTP request will hang and eventually error on the client's side.
{% endhint %}

```text
RegisterPluginHttpEvent("yourpluginname:hello", function(data)
    debugLog(("Got data: %s"):format(json.encode(data)))
    return { result = "ok, got some data!" }
end)
```

#### Breakdown

The framework exposes the `RegisterPluginHttpEvent` function for plugins to use \(is not exported, currently\). Using this function "registers" a particular type where the framework will send the POSTed payload to the callback function.

**Note: This will block the HTTP request, so take care if this is requesting data from an external source like a database.**

To actually use this, we would POST to the URL, as noted below.

Return a LUA table which will be encoded as JSON back to the requesting client.

{% api-method method="post" host="http://yourserverip:serverport" path="/sonorancad/pluginevent" %}
{% api-method-summary %}
Plugin Event
{% endapi-method-summary %}

{% api-method-description %}
Send a payload to trigger a specific HTTP event that was defined in the plugin code.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="data" type="object" required=true %}
A JSON object containing the payload to be sent
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
The registered type this data should be sent to
{% endapi-method-parameter %}

{% api-method-parameter name="key" type="string" required=true %}
Your API Key
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Response varies based on return statement defined in the handler.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



