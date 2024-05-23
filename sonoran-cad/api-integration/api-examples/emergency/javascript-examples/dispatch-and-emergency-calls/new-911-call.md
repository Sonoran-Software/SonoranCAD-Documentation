---
description: >-
  The 911 Call API endpoint allows you to send 911 calls from in-game directly
  to your dispatchers.
---

# New 911 Call

{% hint style="warning" %}
This API endpoint requires the **standard** version of Sonoran CAD or higher. For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

This framework export handles the [Emergency Call API endpoint](../../../../api-endpoints/emergency/dispatch-and-emergency-calls/911-call.md).

```javascript
function call911(caller, location, description, postal, plate, cb) {
    exports["sonorancad"].performApiRequest({
        serverId: GetConvar("sonoran_serverId", 1),
        isEmergency: true,
        caller: caller,
        location: location,
        description: description,
        metaData: {
            plate: plate,
            postal: postal,
            useCallLocation: true
        }
    }, "CALL_911", cb);
}
```

### Parameters

| Property          | Type     | Description                                                         |
| ----------------- | -------- | ------------------------------------------------------------------- |
| `caller`          | String   | Name of the caller                                                  |
| `location`        | String   | Street(s) name                                                      |
| `description`     | String   | Call description                                                    |
| `postal`          | Integer  | Postal location of the call                                         |
| `plate`           | String   | OPTIONAL: Plate to report in the call                               |
| `useCallLocation` | Boolean  | Should the postal location be drawn when using the `/rcall` command |
| `cb`              | Function | OPTIONAL: Callback function                                         |

## Troubleshooting&#x20;

1. "`/rcall` is not drawing a postal route to the call location&#x20;
   1. If you are using the Raw API Call method, please ensure that you have `useCallLocation` set to true.
2. "Units are not getting the call in-game"
   1. Please ensure that you have the [dispatchnotify ](../../../../../../integration-plugins/integration-plugins/available-plugins/dispatch-notify.md)plugin installed
   2. Please ensure the unit is on duty with the configured method in [dispatchnotify](../../../../../../integration-plugins/integration-plugins/available-plugins/dispatch-notify.md)
   3. Please ensure your server's port and IP are correctly set in the Admin -> In-game Integration -> Livemap section of CAD
