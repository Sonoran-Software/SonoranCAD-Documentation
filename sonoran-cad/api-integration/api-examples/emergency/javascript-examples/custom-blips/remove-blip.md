---
description: >-
  This endpoint allows you to remove custom blips from your community's live
  map.
---

# Remove Blip

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/remove_blip" method="post" summary="Remove Blip" %}
{% swagger-description %}
This endpoint allows you to remove a custom blip from the live map.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" required="true" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" required="true" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" required="true" %}
REMOVE_BLIP
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" required="true" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Blip 123 removed!
```
{% endswagger-response %}

{% swagger-response status="400" description="The following 400 errors may be sent in response:" %}
```http
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API ENDPOINT IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
```
{% endswagger-response %}
{% endswagger %}

```javascript
function removeBlip(ids, cb) {
    exports["sonorancad"].performApiRequest({
        "ids": ids
    }, "REMOVE_BLIP", function (res) {
        if (cb !== null) {
            cb(res);
        }
    });
}
```

### Parameters

| Property | Type     | Description                 |
| -------- | -------- | --------------------------- |
| `ids`    | Integer  | Blip ID to remove           |
| `cb`     | Function | OPTIONAL: Callback function |
