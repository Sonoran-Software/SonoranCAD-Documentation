---
description: Have your plugin handle HTTP requests sent to a special URL.
---

# HTTP Request Handling

## Plugin Code

This code only works on the Server side files since HTTP only works on servers, obviously!

{% hint style="danger" %}
You **must** return something, even if it's just a confirmation the data was received. Otherwise, the HTTP request will hang and eventually error on the client's side.
{% endhint %}

```
RegisterPluginHttpEvent("yourpluginname:hello", function(data)
    debugLog(("Got data: %s"):format(json.encode(data)))
    return { result = "ok, got some data!" }
end)
```

#### Breakdown

The framework exposes the `RegisterPluginHttpEvent` function for plugins to use (is not exported, currently). Using this function "registers" a particular type where the framework will send the POSTed payload to the callback function.

**Note: This will block the HTTP request, so take care if this is requesting data from an external source like a database.**

To actually use this, we would POST to the URL, as noted below.

Return a LUA table which will be encoded as JSON back to the requesting client.

{% swagger baseUrl="http://yourserverip:serverport" path="/sonorancad/pluginevent" method="post" summary="Plugin Event" %}
{% swagger-description %}
Send a payload to trigger a specific HTTP event that was defined in the plugin code.
{% endswagger-description %}

{% swagger-parameter in="body" name="data" type="object" %}
A JSON object containing the payload to be sent
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
The registered type this data should be sent to
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your API Key
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
Response varies based on return statement defined in the handler.
```
{% endswagger-response %}
{% endswagger %}

