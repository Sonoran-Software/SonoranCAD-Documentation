---
description: >-
  Sonoran CAD allows you to customize your community's penal codes, charge type
  names, bond type names, and more!
---

# Penal Codes

{% hint style="info" %}
Community customization is not included with the free version.  
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../getting-started/view-your-limits.md).
{% endhint %}

## What are penal codes?

Penal codes can easily be referenced and cited in records/reports as charges.

![Sonoran CAD - Penal Code Reference Window](../../.gitbook/assets/image%20%2853%29.png)

![Sonoran CAD - Charges Section](../../.gitbook/assets/image%20%2852%29.png)

### 1. Charge Types

You can create your own "Charge Type" options for penal codes. If your country does not have "felonies" you can edit or remove this option.

You can also use the "Auto Sort" feature to quickly format the order of these charge types.

Be sure to hit "Save" before exiting the page.

![Sonoran CAD - Custom Charge Types](../../.gitbook/assets/image%20%2856%29.png)

### 2. Bond Types

You can create your own "Bond'/Bail Type" options for penal codes. Again, if your country does not use these, you can edit or remove them as needed.

You can also use the "Auto Sort" feature to quickly format the order of these charge types.

![Sonoran CAD - Custom Bond &amp; Bail Types](../../.gitbook/assets/image%20%2854%29.png)

### 3. Penal Codes

Adding, editing, or removing a penal code is easy. Simply click on the existing code to edit it, or press "New Penal Code" to create a new one.

![Sonoran CAD - Penal Code Management](../../.gitbook/assets/image%20%2855%29.png)

![Sonoran CAD - Penal Code Editor](../../.gitbook/assets/image%20%2851%29.png)

### 4. My locality doesn't call them "Penal Codes"

Sonoran CAD allows you to change the naming of "Penal Codes" to anything else you'd like.  
Learn more about our [geographical customization](geographical-settings.md).

## Import from Spreadsheet \(CSV\)

Sonoran CAD allows you to easily import your penal codes from a spreadsheet \(.CSV\) file.

### 1. Copy the Google Sheet

Navigate to our [official penal code Google sheet ](https://docs.google.com/spreadsheets/u/0/d/10TCczXferWWFi8sYtccrqocRZ4WdpKB1s4hwRm2Iy6I/copy)and make a copy. Using a copy of our official sheet ensures your penal codes are formatted correctly.

![Penal Codes - Copy Sheet](../../.gitbook/assets/image%20%28107%29.png)

### 2. Add Your Penal Codes

Now that you have copied this sheet into your Google Drive, you can add new rows and format your penal codes.

{% hint style="warning" %}
**Do NOT modify the very first row.** These names must remain the same to properly format the penal code structure.

Additionally, the `bondAmount` column must be kept as a number.  
All other columns must be formatted as text.
{% endhint %}

![](../../.gitbook/assets/image%20%28103%29.png)

### 3. Download the CSV

In Google Sheets, navigate to File &gt; Download &gt; Comma Separated Values \(.csv\) to download the file.

![Google Sheets - Download CSV](../../.gitbook/assets/image%20%28106%29.png)

### 4. Import the CSV File

In Sonoran CAD, navigate to Admin &gt; Customization &gt; Penal Codes

In the penal codes section, select the "Import" button.  
Then, select "CSV" as the import type and select your downloaded CSV file.

![Sonoran CAD - Import Data](../../.gitbook/assets/image%20%28104%29.png)

![File Selector - Select File](../../.gitbook/assets/image%20%28105%29.png)

After selecting the CSV file, your penal codes will be imported into the CAD and saved automatically.

## Import from JSON

You can also build and format your penal codes directly into JSON. These JSON formatted penal codes can be sent via our [API endpoint](../../sonoran-cad/api-integration/api-endpoints/general/set-penal-codes.md), or pasted directly into the UI for a more user-friendly experience.

### 1. Format the JSON Structure

The JSON structure is an object array. Be sure to strictly follow the format. All keys are strings, with the exception of `bondAmount` being a number.

```javascript
[
        {
            "code": "(2)06",
            "type": "Felony",
            "title": "Armed Robbery",
            "bondType": "Federal Bail Bond",
            "jailTime": "5-10 Years",
            "bondAmount": 20000
        },
        {
            "code": "(2)07",
            "type": "Felony",
            "title": "Murder",
            "bondType": "Federal Bail Bond",
            "jailTime": "5-50 Years",
            "bondAmount": 100000
        }
    ]
```

### 2. Import the JSON Structure

In Sonoran CAD, navigate to Admin &gt; Customization &gt; Penal Codes

In the penal codes section, select the "Import" button.  
Then, select "JSON" and paste the JSON object array of penal codes.

![Sonoran CAD - Import Data](../../.gitbook/assets/image%20%28104%29.png)

![Sonoran CAD - Paste JSON Content](../../.gitbook/assets/image%20%28120%29.png)

After pasting the JSON content, your penal codes will be imported into the CAD and saved automatically.

