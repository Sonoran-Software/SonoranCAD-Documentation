---
description: Retrieve all records associated with a name or license plate.
---

# Lookup Name or Plate

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
API response times may be increased slightly for communities with Database Sync enabled, depending upon the speed, latency and size of your in-game database.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/emergency" %}
{% api-method-summary %}
Lookup Name or Plate
{% endapi-method-summary %}

{% api-method-description %}
The lookup name endpoint allows you to retrieve all records associated with a provided name.
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
LOOKUP\_NAME or LOOKUP\_PLATE
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
  "vehicleCitations": [], // Object arrays of the record types
  "arrestRecords": [],
  "warrantRecords": [],
  "bolos": [],
  "licenses": [],
  "vehicleRegistrations": [],
  "generalCitations": [],
  "characters": []
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

{% tabs %}
{% tab title="Lookup Name" %}
```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "LOOKUP_NAME",
    "data": [
        {
            "apiId": "STEAM:1234", // OPTIONAL FIELD - Will return results to user's CAD
            "first": "John", // (Partial) First name
            "last": "Doe", // (Partial) Last name
            "mi": "M" // Middle Initial
        }
    ]
}
```
{% endtab %}

{% tab title="Lookup Plate" %}
```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "LOOKUP_PLATE",
    "data": [
        {
            "apiId": "STEAM:1234", // OPTIONAL FIELD - Will return results to user's CAD
            "plate": "1234ABCD" // (Partial) License plate number
        }
    ]
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Searches must include all name/plate data fields, but some can be left blank. Searches must include at least one field with string content \(ex: first name 'John'\) and can not have all fields left blank.
{% endhint %}

### API ID

Adding the API ID field is _optional_, and will send the lookup results to the user's CAD as well.

### Response Object Types

Lookup responses contain several record type arrays. Each array contains the individual record objects.  
Many record types share common `agency`, `person`, `vehicle`, etc. object fields.

{% tabs %}
{% tab title="vehicleCitations" %}
```text
"vehicleCitations": [
  {
      "flags": ["Violent", "Armed"],
      "agency": {
        "name": "John Doe",
        "recordNumber": 0,
        "date": "2020/01/01",
        "officer": "Brian Sosnowski",
        "location": "1234 E. Test St.",
        "zip": "123456",
        "badge": "A-10"
      },
      "person": {
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
      },
      "vehicle": {
        "type": "COUPE",
        "make": "FORD",
        "model": "MUSTANG",
        "color": "SILVER",
        "plate": "1234ABCD",
        "year": "2002"
      },
      "speed": {
        "vehicleSpeed": "75",
        "speedLimit": "50",
        "paceType": "RADAR",
        "date": "2020/05/10",
        "time": "",
        "fine": 350
      },
      "narrative": "This is some text here!",
      "status": {
        "signaturePrimary": "Brian Sosnowski",
        "signatureSecondary": "Hank Voight",
        "date": "2020/01/01",
        "status": "CLOSED"
      }
    }
  ]
```
{% endtab %}

{% tab title="arrestRecords" %}
```text
"arrestRecords": [
    {
      "flags": ["Violent", "Armed"],
      "agency": {
        "name": "John Doe",
        "recordNumber": 0,
        "date": "2020/01/01",
        "officer": "Brian Sosnowski",
        "location": "1234 E. Test St.",
        "zip": "123456",
        "badge": "A-10"
      },
      "person": {
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
      },
      "vehicle": {
        "type": "COUPE",
        "make": "FORD",
        "model": "MUSTANG",
        "color": "SILVER",
        "plate": "1234ABCD",
        "year": "2002"
      },
      "weapons": "N/A",
      "arrestType": "ON VIEW",
      "probationaryOfficer": "N/A",
      "charges": [
        {
          "arrestCharge": "Armed Robbery",
          "arrestChargeType": "FELONY",
          "arrestChargeCounts": 1,
          "arrestChargeCode": "(A.1) 42-328",
          "arrestBondType": "FEDERAL BAIL BOND",
          "arrestBondAmount": 100000,
          "jailTime": "5 Years"
        }
      ],
      "narrative": "Some narrative here.",
      "status": {
        "signaturePrimary": "Brian Sosnowski",
        "signatureSecondary": "Hank Voight",
        "date": "2020/01/01",
        "status": "CASE CLOSED"
      }
    },
  ],
```
{% endtab %}

{% tab title="warrantRecords" %}
```
"warrantRecords": [
    {
     "flags": ["Violent", "Armed"],
      "agency": {
        "name": "John Doe",
        "recordNumber": 0,
        "date": "2020/01/01",
        "officer": "Brian Sosnowski",
        "location": "1234 E. Test St.",
        "zip": "123456",
        "badge": "A-10"
      },
      "person": {
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
      },
      "charges": [
        {
          "arrestCharge": "Armed Robbery",
          "arrestChargeType": "FELONY",
          "arrestChargeCounts": 1,
          "arrestChargeCode": "(A.1) 42-328",
          "arrestBondType": "FEDERAL BAIL BOND",
          "arrestBondAmount": 100000,
          "jailTime": "5 Years"
        }
      ],
      "narrative": "Some narrative here.",
      "status": {
        "signaturePrimary": "Brian Sosnowski",
        "signatureSecondary": "Hank Voight",
        "date": "2020/01/01",
        "status": "ACTIVE"
      }
    },
  ],
```
{% endtab %}

{% tab title="bolos" %}
```
"bolos": [
    {
      "flags": ['ARMED', 'VIOLENT'],
      "agency": {
        "name": "John Doe",
        "recordNumber": 0,
        "date": "2020/01/01",
        "officer": "Brian Sosnowski",
        "location": "1234 E. Test St.",
        "zip": "123456",
        "badge": "A-10"
      },
      "person": {
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
      },
      "vehicle": {
        "type": "COUPE",
        "make": "FORD",
        "model": "MUSTANG",
        "color": "SILVER",
        "plate": "1234ABCD",
        "year": "2002"
      },
      "charges": [
        {
          "arrestCharge": "Armed Robbery",
          "arrestChargeType": "FELONY",
          "arrestChargeCounts": 1,
          "arrestChargeCode": "(A.1) 42-328",
          "arrestBondType": "FEDERAL BAIL BOND",
          "arrestBondAmount": 100000,
          "jailTime": "5 Years"
        }
      ],
      "narrative": "Some narrative here."
    },
  ],
```
{% endtab %}

{% tab title="licenses" %}
```
"licenses": [
    {
      "id": 1,
      "syncId": "",
      "owner": "",
      "type": "DRIVERS",
      "person": {
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
      },
      "status": "ACTIVE",
      "expiration": "2030/01/01"
    },
  ],
```
{% endtab %}

{% tab title="vehicleRegistrations" %}
```
"vehicleRegistrations": [
    {
      "id": 1,
      "syncId": "",
      "owner": "",
      "person": {
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
      },
      "vehicle": {
        "type": "COUPE",
        "make": "FORD",
        "model": "MUSTANG",
        "color": "SILVER",
        "plate": "1234ABCD",
        "year": "2002"
      },
      "status": "ACTIVE",
      "expiration": "2030/01/01"
    },
  ],
```
{% endtab %}

{% tab title="generalCitations" %}
```
"generalCitations": [
    {
      "flags": ["Violent", "Armed"],
      "agency": {
        "name": "John Doe",
        "recordNumber": 0,
        "date": "2020/01/01",
        "officer": "Brian Sosnowski",
        "location": "1234 E. Test St.",
        "zip": "123456",
        "badge": "A-10"
      },
      "person": {
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
      },
      "vehicle": {
        "type": "COUPE",
        "make": "FORD",
        "model": "MUSTANG",
        "color": "SILVER",
        "plate": "1234ABCD",
        "year": "2002"
      },
      "charges": [
        {
          "arrestCharge": "Armed Robbery",
          "arrestChargeType": "FELONY",
          "arrestChargeCounts": 1,
          "arrestChargeCode": "(A.1) 42-328",
          "arrestBondType": "FEDERAL BAIL BOND",
          "arrestBondAmount": 100000,
          "jailTime": "5 Years"
        }
      ],
      "narrative": "Some narrative here.",
      "status": {
        "signaturePrimary": "Brian Sosnowski",
        "signatureSecondary": "Hank Voight",
        "date": "2020/01/01",
        "status": "ACTIVE"
      }
    },
  ],
```
{% endtab %}

{% tab title="characters" %}
```
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
{% endtab %}
{% endtabs %}

