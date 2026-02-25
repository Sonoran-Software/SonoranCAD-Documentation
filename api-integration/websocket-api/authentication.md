---
description: All websocket API calls require authentication prior to invoking functions.
---

# Authentication

## Websocket Authentication

### Authentication Method

#### **Method:**

```
authenticate
```

#### **Parameters:**

| Parameter     | Type   |
| ------------- | ------ |
| `communityId` | String |
| `apiKey`      | String |

### Response

```
{ success: boolean, error: string, count: number }
```

### Auth JS example (Node.js) Requires:

**Add the Microsoft SignalR Library**

```
npm i @microsoft/signalr
```

<pre class="language-js"><code class="lang-js"><strong>// Import the signalr library for backend connection
</strong><strong>const signalR = require("@microsoft/signalr");
</strong>
// Establist the connection object
const connection = new signalR.HubConnectionBuilder()
  .withUrl("https://api.sonorancad.com/apiWsHub", {
    transport: signalR.HttpTransportType.WebSockets,
    skipNegotiation: true,
  })
  .withAutomaticReconnect()
  .build();

// Start the WSS connection
await connection.start();

// Replace community ID and API key
const auth = await connection.invoke("authenticate", "yourCommunityId", "yourApiKey");
if (!auth?.success) {
  throw new Error(`Authentication failed: ${auth?.error || "unknown error"}`);
}
</code></pre>
