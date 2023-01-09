---
description: >-
  This endpoint allows you to retrieve all custom blips for a community's live
  map!
---

# Remove Blip With Subtype

{% hint style="warning" %}
This API endpoint requires the **pro** version of Sonoran CAD or higher.\
For more information, see our [pricing ](../../../../../../pricing/faq/)page.
{% endhint %}

```javascript
function removeWithSubtype(subType, cb) {
    Utilities.CAD.getBlips(function (res) {
        let dres = JSON.parse(res);
        let ids = [];
        if (typeof dres == "table") {
            for (let _ in dres) {
                let v = dres[_];
                if (v.subType == subType) {
                    ids.push(v.id);
                }
            }
            Utilities.CAD.removeBlip(ids, cb);
        } else {
            console.log("No blips were returned.");
        }
    });
}
```

### Parameters

| Property  | Type     | Description                 |
| --------- | -------- | --------------------------- |
| `subType` | String   | Blip subtype to remove      |
| `cb`      | Function | OPTIONAL: Callback function |
