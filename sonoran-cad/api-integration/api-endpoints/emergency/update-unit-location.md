---
description: >-
  The unit location update call allows you to update a unit's location from
  in-game.
---

# Update Unit Location

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency" %}
{% api-method-summary %}
Unit Location
{% endapi-method-summary %}

{% api-method-description %}
The unit location API endpoint allows you to update a unit's location from in-game.
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
UNIT\_LOCATION
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of unit location objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
UNIT LOCATION UPDATED
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
    "type": "UNIT_LOCATION",
    "data": [
        {
            "apiId": "STEAM:1234", // API ID entered in the unit identifiers
                                   // Typically, this is their STEAM ID
            "location": "1234 W. Example St.",
        },
        {
            "apiId": "STEAM:5678",
            "location": "5678 E. Test Ave.",
        }
    ]
}
```

#### API ID

The **apiId** field contains a unique ID that every unit identifier must have specified in Sonoran CAD. Users can set this field in their identifier to properly map unit update API calls to their CAD identifier.  
  
For more information, see our guide on setting your unit's API ID:

{% page-ref page="../../getting-started/setting-your-api-id.md" %}

#### Rate Limiting

To avoid being rate limited when frequently updating multiple unit locations, it is best to group multiple unit location update together into the **data** array field. When compared to making a separate API call with every location update, grouping multiple location updates into a single call every few seconds is more efficient.

_NOTE:_ We recommend updating unit locations in a group no more frequently than every 5 seconds.

