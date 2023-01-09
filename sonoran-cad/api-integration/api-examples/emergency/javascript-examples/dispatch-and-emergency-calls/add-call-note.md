---
description: This endpoint allows you to add a new dispatch call note.
---

# Add Call Note

{% hint style="warning" %}
This API endpoint requires the **plus** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Add Call Note API endpoint](../../../../api-endpoints/emergency/dispatch-and-emergency-calls/add-call-note.md).

```javascript
function addCallNote(callId, note) {
    exports["sonorancad"].performApiRequest({
        serverId: GetConvar("sonoran_serverId", 1),
        callId: callId,
        note: note
    }, "ADD_CALL_NOTE", function(_) {});
}

```

### Note Object

Call notes are formatted on dispatch calls with the following object:

```json
{
    "time": "12:00:00",
    "label": "A-10",
    "type": "text",
    "content": "This is a note!"
}
```

### Parameters

| Property | Type        | Description                |
| -------- | ----------- | -------------------------- |
| `callId` | Integer     | Call ID to add the note to |
| `note`   | Note Object | See Note Object above      |
