---
description: >-
  This endpoint allows you to retrieve all characters associated with a user
  account in the CAD.
---

# Get Characters

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/civilian/get\_characters" %}
{% api-method-summary %}
Get Characters
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to retrieve all characters associated with a user account in the CAD.
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
GET\_CHARACTERS
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of character objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```javascript
// Array of character objects
[
 {
  "id": -1, // Unique Character ID
  "syncId": "STEAM:1234", // Unique Character ID from Database Sync
  "img": "someimageurlhere.jpg",
  "first": "John",
  "last": "Doe",
  "mi": "A",
  "dob": "01/01/1900",
  "age": "18",
  "sex": "M",
  "aka": "Johnny",
  "residence": "3183 E. Example Ave",
  "zip": "39493",
  "occupation": "Software Developer",
  "height": "5 10",
  "weight": "175",
  "skin": "Caucasian",
  "hair": "Brown",
  "eyes": "Hazel",
  "emergencyContact": "Sally Quinn",
  "emergencyContactNumber": "(123) 456 - 7890",
  "emergencyContactRelationship": "Sister"
 }
]
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
API ID NOT LINKED TO AN ACCOUNT IN THIS COMMUNITY
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "GET_CHARACTERS",
    "data": [
        {
            "apiId": "STEAN:1234" // API ID, Typically, this is their STEAM Hex
        },
    ]
}
```

