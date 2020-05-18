---
description: This endpoint allows you to edit an existing license for a CAD user account.
---

# Edit License

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% hint style="danger" %}
Licenses can NOT be edited in communities using [Database Sync](../../../../tutorials/in-game-integration/database-sync-and-merge/), as all licenses are pulled from your server's in-game database.
{% endhint %}

{% api-method method="post" host="https://api.sonorancad.com" path="/civilian" %}
{% api-method-summary %}
Edit License
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to edit an existing license for a CAD user account.
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
EDIT\_LICENSE
{% endapi-method-parameter %}

{% api-method-parameter name="data" type="array" required=true %}
Array of license objects
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A successful call will be met with the following response:
{% endapi-method-response-example-description %}

```
{LICENSE OBJECT}
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
    "type": "EDIT_LICENSE",
    "data": [
        {
            "id": 100, // Unique ID - Retrieved from LOOKUP_NAME or LOOKUP_PLATE
            "type": "Drivers"
            "status": "VALID",
            "expiration": "01/01/1900",
            "person": {
                "img": "someimageurlhere.jpg",
    		        "first": "John",
    		        "last": "Doe",
    		        "mi": "A", // Middle initial can only be ONE character
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
        },
    ]
}
```

