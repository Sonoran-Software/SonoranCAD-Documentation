---
description: >-
  Sonoran CAD has additional record lookup capabilities via integer values for
  unit identifiers, record or supervisor status, and more!
---

# Lookup By Integer

{% hint style="warning" %}
This API endpoint requires the **Plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
API response times may be increased slightly for communities with Database Sync enabled, depending upon the speed, latency and size of your in-game database.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/general" %}
{% api-method-summary %}
Lookup By Int
{% endapi-method-summary %}

{% api-method-description %}
The lookup name endpoint allows you to retrieve all records associated with a provided name or license plate.
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
LOOKUP\_INT
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array containing a lookup information object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:  
_Detailed contents of the record type arrays can be found further below._
{% endapi-method-response-example-description %}

```
{
  "characters": [],
  "records": []
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
INVALID REQUEST TYPE
INVALID COMMUNITY ID
API IS NOT ENABLED FOR THIS COMMUNITY
INVALID API KEY
INVALID EMPTY SEARCH
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### API Call Example

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "LOOKUP",
    "data": [
        {
            "apiId": "STEAM:1234", // OPTIONAL FIELD - Will return results to user's CAD
            "searchType": 0, // 
            "value": 1, // 
            "types": [2, 3] // Search only for warrant and BOLO records
        }
    ]
}
```

{% tabs %}
{% tab title="API ID" %}
### API ID

Adding the [API ID](../getting-started/setting-your-api-id.md) field is _optional_, and will send the lookup results to the user's CAD as well.
{% endtab %}

{% tab title="Search Type" %}
### SearchType Enumerator

The `searchType` enumerator determines how your `value` integer is interpreted. 

| Enum | Description |
| :--- | :--- |
| 0 | IDENTIFIER |
| 1 | SUPERVISOR\_STATUS |
| 2 | ACTIVE\_STATUS |
| 3 | NUMBER |
{% endtab %}

{% tab title="Value" %}
### Value Integer

The `value` integer is the primary search key for the `searchType` specified.

#### Identifier \(searchType 0\)

When specifying an identifier `searchType` the `value` represents the unique identifier ID of a specific unit. You can retrieve this unique identifier ID via the [Get Identifiers endpoint](get-identifiers.md).

This will return all records associated with the provided unit identifier.

#### Supervisor Status \(searchType 1\)

When specifying a supervisor status `searchType` the `value` represents the supervisor status of the records being searched.

| Enum | Description |
| :--- | :--- |
| 0 | Open: Requires Supervisor Actions |
| 1\` | Closed: No Supervisor Actions Needed |

#### Active Status \(searchType 2\)

When specifying an active status `searchType` the `value` represents the record status of the records being searched.  
The `value` integer enumeration here is used particularly to search open/closed warrants and pending/approved/rejected DMV records.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Enum</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0</td>
      <td style="text-align:left">
        <p>Warrant: Open</p>
        <p>DMV: Pending</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>Warrant: Closed</p>
        <p>DMV: Approved</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">DMV: Rejected</td>
    </tr>
  </tbody>
</table>

#### Number \(searchType 3\)

When specifying a number `searchType` the `value` represents the unique record number being searched. You can find the specific record number via any [lookup ](lookup-name-or-plate.md)or [lookup by integer](lookup-by-integer.md) result.
{% endtab %}

{% tab title="Record Types" %}
### Record Type

The record "type" is an enumerator used to distinguish the category of the custom record/report. These integer values are entered as an array in the `types` field of the lookup call.

The `characters` object array will always be included with the search. The `types` filtering only applies to the custom records being returned.

| Enum | Description |
| :--- | :--- |
| 2 | Warrant |
| 3 | BOLO |
| 4 | License |
| 5 | Vehicle Registration |
| 8 | Custom Police Record |
| 9 | Custom Police Report |
| 10 | Custom Medical Record |
| 11 | Custom Medical Report |
| 12 | Custom Fire Record |
| 13 | Custom Fire Report |
| 14 | Custom DMV Record |
| 15 | Custom Law Record |
| 16 | Custom Law Report |
{% endtab %}

{% tab title="Response Object Types" %}
### Response Object Types

Lookup responses contain an array of `characters` and `records`.

#### Characters Formatting

All character results from the search are returned in the following object array structuring:

```javascript
"characters": [
    {
        "id": 0,
        "syncId": "",
        "img": "https://someimagepath.com",
        "first": "John",
        "last": "Doe",
        "mi": "A",
        "dob": "1900/01/01",
        "age": "100",
        "sex": "M",
        "aka": "Johnny",
        "residence": "4321 E. Example Ave",
        "zip": "12345",
        "occupation": "Software Developer",
        "height": "5 11",
        "weight": "175",
        "skin": "CAUCASIAN",
        "hair": "BROWN",
        "eyes": "HAZEL",
        "emergencyContact": "Sally May",
        "emergencyContactNumber": "123 456 7890",
        "emergencyContactRelationship": "Wife"
    }
  ]
```

#### Records Formatting

All record results are returned in an object array. For more information on custom record structuring, see the documentation below:

{% page-ref page="custom-records/" %}
{% endtab %}
{% endtabs %}

