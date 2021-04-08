---
description: This endpoint allows you to manually set a user's API IDs.
---

# Set API IDs

{% hint style="warning" %}
This API endpoint requires the **Standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

This endpoint allows you to manually set a user's [API ID](../../getting-started/setting-your-api-id.md). This endpoint is used in our [tablet](../../../../integration-plugins/integration-plugins/available-plugins/tablet.md) and [API ID plugin ](../../../../integration-plugins/integration-plugins/available-plugins/api-id-checker.md)to automatically link your in-game user to the CAD.

{% api-method method="post" host="https://api.sonorancad.com" path="/general/set\_api\_id" %}
{% api-method-summary %}
Set API IDs
{% endapi-method-summary %}

{% api-method-description %}

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
SET\_API\_ID
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
API ID(s) set!
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
    "type": "SET_API_ID",
    "data": [
        {
          "username": "Brian1234",
          "sessionId": "2daf5d1-8256-4373-9a", // OPTIONAL - Authentication
          "apiIds": [
              "11000010499F33C",
              "ABCD123",
          ],
          "pushNew": true, // Push new API IDs to array or override entirely
		    }
    ]
}
```

Note: The `apiIds` will automatically filter out any duplicate values.

### Optional Fields

#### Session ID

The `sessionId` field is an optional field for authentication purposes.

The following data object is [emitted from your web browser](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) via `window.parent.postMessage` and can be captured by a parent page when hosting it in a live map:

```javascript
{
  "username": "SonoranBrian",
  "session": "1234-5678-9012-3456"
}
```

This object contains your session ID, and can be captured with resources like our [in-game tablet](../../../../integration-plugins/integration-plugins/available-plugins/tablet.md).

This is how the in-game tablet and [API ID](../../../../integration-plugins/integration-plugins/available-plugins/api-id-checker.md) plugin work to automatically link your API ID when using the tablet.

#### Push New

The `pushNew` boolean determines whether or not to update the user account's existing API IDs and "push" \(add\) these new `apiIds` or to overwrite their saved API IDs entirely.

If not set, the default is `true` \(add onto existing API IDs\).

