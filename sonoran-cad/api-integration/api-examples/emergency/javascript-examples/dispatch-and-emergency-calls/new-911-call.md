---
description: >-
  The 911 Call API endpoint allows you to send 911 calls from in-game directly
  to your dispatchers.
---

# New 911 Call

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
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
function call911(caller, location, description, postal, plate, cb) {
    exports["sonorancad"].performApiRequest({
        serverId: GetConvar("sonoran_serverId", 1),
        isEmergency: true,
        caller: caller,
        location: location,
        description: description,
        metaData: {
            plate: plate,
            postal: postal
        }
    }, "CALL_911", cb);
}
```

### Parameters

| Property      | Type     | Description                           |
| ------------- | -------- | ------------------------------------- |
| `caller`      | String   | Name of the caller                    |
| `location`    | String   | Street(s) name                        |
| `description` | String   | Call description                      |
| `postal`      | Integer  | Postal location of the call           |
| `plate`       | String   | OPTIONAL: Plate to report in the call |
| `cb`          | Function | OPTIONAL: Callback function           |
