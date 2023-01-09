---
description: >-
  This endpoint allows you to remove an existing emergency/911 call from the
  CAD.
---

# Remove 911

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This endpoint allows you to remove an existing emergency/911 call from the CAD.

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/remove_911" method="post" summary="Remove 911" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
REMOVE_911
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
API ID(s) set!
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
function remove911(callId) {
  exports["sonorancad"].performApiRequest({
    serverId: GetConvar("sonoran_serverId", 1),
    callId: callId
  }, "REMOVE_911", function(_) {
  });
}
```

### Parameters

| Property | Type    | Description       |
| -------- | ------- | ----------------- |
| `callId` | Integer | Call ID to remove |
