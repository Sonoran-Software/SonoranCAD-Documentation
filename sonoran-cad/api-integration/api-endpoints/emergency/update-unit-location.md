---
description: >-
  The unit location update call allows you to update a unit's location from
  in-game.
---

# Update Unit Location

{% hint style="warning" %}
iThis API endpoint requires the **standard **version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/emergency/unit_location" method="post" summary="Unit Location" %}
{% swagger-description %}
The unit location API endpoint allows you to update a unit's location from in-game.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
UNIT_LOCATION
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of unit location objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
UNIT LOCATION UPDATED
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

The **apiId **field contains a unique ID that every unit identifier must have specified in Sonoran CAD. Users can set this field in their identifier to properly map unit update API calls to their CAD identifier.\
\
For more information, see our guide on setting your unit's API ID:

{% content-ref url="../../getting-started/setting-your-api-id.md" %}
[setting-your-api-id.md](../../getting-started/setting-your-api-id.md)
{% endcontent-ref %}

#### Rate Limiting

To avoid being rate limited when frequently updating multiple unit locations, it is best to group multiple unit location update together into the **data **array field. When compared to making a separate API call with every location update, grouping multiple location updates into a single call every few seconds is more efficient.

_NOTE:_ We recommend updating unit locations in a group no more frequently than every 5 seconds.
