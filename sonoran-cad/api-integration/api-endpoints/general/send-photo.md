---
description: >-
  This endpoint allows you to send an image popup to a user's CAD from in-game
  for mugshots, evidence photos, etc.
---

# Send Photo

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

{% swagger baseUrl="https://api.sonorancad.com" path="/general/send_photo" method="post" summary="Send Photo" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="string" %}
Your community's ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="key" type="string" %}
Your community's API Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
SEND_PHOTO
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="array" %}
Array of request objects
{% endswagger-parameter %}

{% swagger-response status="200" description="A successful call will be met with the following response:" %}
```
Photo sent!
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
    "type": "SEND_PHOTO",
    "data": [
        {
          "apiId": "STEAM:1234", // User API ID
          "url": "https://example.com/photo.png" // Photo URL
    ]

```
