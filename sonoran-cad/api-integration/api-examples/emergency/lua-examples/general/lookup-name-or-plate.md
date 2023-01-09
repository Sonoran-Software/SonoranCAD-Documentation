---
description: Retrieve all records associated with a name or license plate.
---

# Lookup Name or Plate

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
API response times may be increased slightly for communities with Database Sync enabled, depending upon the speed, latency and size of your in-game database.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/lookup" method="post" summary="Lookup Name or Plate" %}
{% swagger-description %}
The lookup name endpoint allows you to retrieve all records associated with a provided name or license plate.
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
LOOKUP
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array containing a lookup information object
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:
Detailed contents of the record type arrays can be found further below." %}
```
{
  "records": []
}
```
{% endswagger-response %}

{% swagger-response status="302" description="" %}
```
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
INVALID EMPTY SEARCH
```
{% endswagger-response %}
{% endswagger %}

## API Call Example

```lua
function performLookup(types, plate, partial, first, last, mi, cb)
    exports["sonorancad"]:performApiRequest({{
        ["types"] = {},
        ["plate"] = plate,
        ["partial"] = partial,
        ["first"] = first,
        ["last"] = last,
        ["mi"] = mi
    }}, "LOOKUP", function(res)
        if cb ~= nil then
            cb(res)
        end
    end)
end
```

{% hint style="warning" %}
Searches must include all name/plate data fields, but some can be left blank. Searches must include at least one field with string content (ex: first name 'John') and can not have all fields left blank.

To perform a plate based search, simply fill in the `plate` property and leave the rest blank.
{% endhint %}

| Property  | Type     | Description                                                                                              |
| --------- | -------- | -------------------------------------------------------------------------------------------------------- |
| `types`   | Array    | Array of [record types](../../../../api-endpoints/general/lookup-name-or-plate.md#record-type) to lookup |
| `plate`   | String   | Plate to lookup                                                                                          |
| `partial` | Boolean  | Partial or exact search                                                                                  |
| `first`   | String   | First name to lookup                                                                                     |
| `last`    | String   | Last name to lookup                                                                                      |
| `mi`      | String   | Middle initial to lookup                                                                                 |
| `cb`      | Function | Callback function                                                                                        |
