---
description: Find out how to map QBCore player licenses to DBSync!
---

# QBCore License Mapping

### 1. Open Admin panel to License Record

You will first need to edit the License record to adapt it for how QBCore stores its licenses. Open the Admin Panel by going to the following...

`Admin Panel` -> `Customization` -> `Custom Records` -> Click `#4 - License`

![Sonoran CAD Custom Record Editor](<../../.gitbook/assets/image (301) (1).png>)

### **2**. Edit License Information Section

Replace the last three fields in the `License Information:` section with the following. Make sure to change the `type` to `text` and remove the `mask`. You can use the screenshot below as a guide. Then click `Save` **** before moving on.

{% hint style="danger" %}
**Don't forget to click Save before continuing!**
{% endhint %}

![Sonoran CAD custom record editor](<../../.gitbook/assets/image (290).png>)

### 3. Open DBSync Settings

Click `Advanced` -> `In-Game Integration` to open the DBSync settings menu.

### 4. Fill in DBSync Settings

As of writing on 2/28/2022, the following pictured settings will work for QBCore's latest version. Fill in the `Table Name`, `Character Mapping Column`, `Column Name`s, `JSON Column`s and `Friendly Mapping`s as shown below. Make sure to click `Save Mapping Config` once finished.

{% hint style="info" %}
We are aware of the misspelling "licence", this is intentional in QBCore to differentiate between another piece of data referred to as "license"
{% endhint %}

![Sonoran CAD DBSync Settings](<../../.gitbook/assets/image (298).png>)

![Sonoran CAD DBSync Friendly Mapping Settings](<../../.gitbook/assets/image (300) (1).png>)

Congratulations! You should now be all set up to display your licenses from QBCore in Sonoran CAD. Feel free to test a record lookup to verify everything is in order.

![Example QBCore DBSynced license data](<../../.gitbook/assets/image (306).png>)
