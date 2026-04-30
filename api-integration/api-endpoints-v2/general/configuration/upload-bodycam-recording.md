---
description: Upload a bodycam recording clip to Sonoran CAD through the dedicated v2 bodycam endpoint.
---

# Upload Bodycam Recording

> **Rate limit:** `30 requests per minute`  
> Authenticated v2 endpoints are rate limited per API key rather than per IP address.

Upload a single bodycam clip into Sonoran CAD's bodycam recordings system through a dedicated v2 endpoint.

{% hint style="info" %}
This API endpoint is available on **Free** and higher Sonoran CAD plans. The rolling `24` hour upload allowance depends on your plan. For more information, see our [pricing](../../../../pricing/faq/).
{% endhint %}

## Endpoint

<mark style="color:green;">`POST`</mark> `https://api.sonorancad.com/v2/general/bodycam-recordings`

#### Request Type

`multipart/form-data`

#### Authentication

Use standard v2 bearer authentication:

| Header | Value | Description |
| --- | --- | --- |
| `Authorization` | `Bearer YOUR_API_KEY` | Authenticates the request. |

#### Form Fields

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| `file` | file | Yes | A single `.webm` clip to upload. |
| `accountUuid` | string | Conditionally | Account UUID that owns the recording. Provide exactly one of `accountUuid` or `communityUserId`. |
| `communityUserId` | string | Conditionally | Community user ID that owns the recording. Provide exactly one of `accountUuid` or `communityUserId`. |
| `durationMs` | number | Yes | Clip duration in milliseconds. Must be between `1` and `120000`. |
| `identId` | number | No | Identifier ID associated with the clip. |
| `unitNumber` | string | No | Unit number to store with the recording metadata. |
| `unitLocation` | string | No | Unit location to store with the recording metadata. |

The authenticated API key determines the community. You do **not** need to send `community`, `sessionId`, `username`, or `type=bodycam`.

## Upload Limits

| Limit | Value |
| --- | --- |
| Max files per request | `1` |
| Allowed file type | `.webm` |
| Max file size | `6000000` bytes (`6 MB`) |
| Max clip duration | `120000` ms (`120` seconds) |

Bodycam uploads are also limited by your community's rolling `24` hour plan allowance:

| Plan | Max uploaded bodycam minutes per 24 hours |
| --- | --- |
| Free | `10` |
| Standard | `100` |
| Pro | `1000` |

## Frontend Video Target

The backend validates the file type, file size, and duration. It does **not** directly reject uploads by resolution or frame rate.

To match the built-in Sonoran CAD frontend bodycam flow and stay within the `6 MB` upload limit, send clips using these target settings:

| Setting | Target |
| --- | --- |
| Resolution | `960x540` |
| Frame rate | `10 FPS` |
| Format | `webm` |

The built-in frontend bodycam capture requests `960x540` at `10 FPS`, and the recording uploader encodes clips as WebM with a `300000` bps video bitrate and `64000` bps audio bitrate. Third-party integrations should match those settings as closely as possible.

## Example Request

{% hint style="warning" %}
Official SDK-specific helper methods are not currently documented for this multipart upload route. Use a raw multipart HTTP request from your runtime.
{% endhint %}

{% tabs %}
{% tab title="Sonoran.lua" %}
```lua
local http = require("socket.http")
local ltn12 = require("ltn12")

local boundary = "----SonoranBodycamBoundary"
local body = table.concat({
  "--" .. boundary,
  'Content-Disposition: form-data; name="accountUuid"',
  "",
  "USER_ACCOUNT_UUID",
  "--" .. boundary,
  'Content-Disposition: form-data; name="durationMs"',
  "",
  "90000",
  "--" .. boundary,
  'Content-Disposition: form-data; name="identId"',
  "",
  "123",
  "--" .. boundary,
  'Content-Disposition: form-data; name="unitNumber"',
  "",
  "1A-12",
  "--" .. boundary,
  'Content-Disposition: form-data; name="unitLocation"',
  "",
  "Senora Fwy / Route 68",
  "--" .. boundary,
  'Content-Disposition: form-data; name="file"; filename="bodycam-clip.webm"',
  "Content-Type: video/webm",
  "",
  "<binary webm data here>",
  "--" .. boundary .. "--",
  "",
}, "\r\n")

local response = {}
local _, status = http.request({
  url = "https://api.sonorancad.com/v2/general/bodycam-recordings",
  method = "POST",
  headers = {
    ["Authorization"] = "Bearer YOUR_API_KEY",
    ["Content-Type"] = "multipart/form-data; boundary=" .. boundary,
    ["Content-Length"] = tostring(#body),
  },
  source = ltn12.source.string(body),
  sink = ltn12.sink.table(response),
})

print(status)
print(table.concat(response))
```
{% endtab %}
{% tab title="Sonoran.js" %}
```javascript
const fs = require('fs');
const FormData = require('form-data');
const fetch = global.fetch || require('node-fetch');

const formData = new FormData();
formData.append('file', fs.createReadStream('./bodycam-clip.webm'));
formData.append('accountUuid', 'USER_ACCOUNT_UUID');
formData.append('durationMs', '90000');
formData.append('identId', '123');
formData.append('unitNumber', '1A-12');
formData.append('unitLocation', 'Senora Fwy / Route 68');

const response = await fetch('https://api.sonorancad.com/v2/general/bodycam-recordings', {
  method: 'POST',
  body: formData,
  headers: {
    Authorization: 'Bearer YOUR_API_KEY',
    ...(formData.getHeaders ? formData.getHeaders() : {}),
  },
});

console.log(await response.text());
```
{% endtab %}
{% tab title="Sonoran.py" %}
```python
import requests

with open("bodycam-clip.webm", "rb") as clip:
    response = requests.post(
        "https://api.sonorancad.com/v2/general/bodycam-recordings",
        data={
            "accountUuid": "USER_ACCOUNT_UUID",
            "durationMs": "90000",
            "identId": "123",
            "unitNumber": "1A-12",
            "unitLocation": "Senora Fwy / Route 68",
        },
        files={
            "file": ("bodycam-clip.webm", clip, "video/webm"),
        },
        headers={
            "Authorization": "Bearer YOUR_API_KEY",
        },
        timeout=120,
    )

print(response.status_code)
print(response.text)
```
{% endtab %}
{% tab title="Sonoran.Net" %}
```csharp
using System.Net.Http;
using System.Net.Http.Headers;

using HttpClient client = new HttpClient();
using MultipartFormDataContent form = new MultipartFormDataContent();
using FileStream fileStream = File.OpenRead("bodycam-clip.webm");
using StreamContent fileContent = new StreamContent(fileStream);

client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", "YOUR_API_KEY");

fileContent.Headers.ContentType = new MediaTypeHeaderValue("video/webm");
form.Add(fileContent, "file", "bodycam-clip.webm");
form.Add(new StringContent("USER_ACCOUNT_UUID"), "accountUuid");
form.Add(new StringContent("90000"), "durationMs");
form.Add(new StringContent("123"), "identId");
form.Add(new StringContent("1A-12"), "unitNumber");
form.Add(new StringContent("Senora Fwy / Route 68"), "unitLocation");

HttpResponseMessage response = await client.PostAsync(
    "https://api.sonorancad.com/v2/general/bodycam-recordings",
    form
);

Console.WriteLine((int)response.StatusCode);
Console.WriteLine(await response.Content.ReadAsStringAsync());
```
{% endtab %}
{% tab title="OpenAPI" %}
Import this YAML into Postman with **Import -> Raw text** to create a single-endpoint request collection for this route.

~~~yaml
openapi: "3.0.3"
info:
  title: "Sonoran CAD v2 - Upload Bodycam Recording"
  version: "1.0.0"
  description: "Upload a bodycam recording clip through the dedicated v2 bodycam endpoint."
servers:
  -
    url: "https://api.sonorancad.com"
paths:
  /v2/general/bodycam-recordings:
    post:
      summary: "Upload Bodycam Recording"
      operationId: "uploadBodycamRecording"
      requestBody:
        required: true
        content:
          multipart/form-data:
            schema:
              type: "object"
              required:
                - "file"
                - "durationMs"
              properties:
                file:
                  type: "string"
                  format: "binary"
                accountUuid:
                  type: "string"
                  format: "uuid"
                communityUserId:
                  type: "string"
                durationMs:
                  type: "integer"
                  minimum: 1
                  maximum: 120000
                identId:
                  type: "integer"
                unitNumber:
                  type: "string"
                unitLocation:
                  type: "string"
      responses:
        200:
          description: "Successful response"
          content:
            application/json:
              schema:
                type: "array"
                items:
                  type: "string"
              example:
                - "https://files.example.com/bodycam/community/unit/clip.webm"
        400:
          description: "Validation or upload error"
          content:
            application/problem+json:
              schema:
                type: "object"
              example:
                title: "Unable to upload bodycam recording"
                status: 400
                detail: "Bodycam uploads must be webm files."
      security:
        -
          bearerAuth:
components:
  securitySchemes:
    bearerAuth:
      type: "http"
      scheme: "bearer"
      bearerFormat: "JWT"
~~~
{% endtab %}
{% tab title="cURL" %}
```bash
curl --request POST \
  --url "https://api.sonorancad.com/v2/general/bodycam-recordings" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --form "file=@bodycam-clip.webm;type=video/webm" \
  --form "accountUuid=USER_ACCOUNT_UUID" \
  --form "durationMs=90000" \
  --form "identId=123" \
  --form "unitNumber=1A-12" \
  --form "unitLocation=Senora Fwy / Route 68"
```
{% endtab %}
{% endtabs %}

## Response

Successful requests return the uploaded file URL list.

```json
[
  "https://files.example.com/bodycam/community/unit/clip.webm"
]
```

## Common Errors

```http
Provide exactly one of accountUuid or communityUserId.
Account USER_ACCOUNT_UUID was not found in this community.
File exceeds 6000000 bytes.
Bodycam uploads must be webm files.
Bodycam uploads are limited to 10 minutes per 24 hours for the FREE plan.
Uploaded bodycam clip but failed to save recording metadata.
```
