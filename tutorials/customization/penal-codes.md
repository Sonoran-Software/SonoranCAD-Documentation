---
description: >-
  Sonoran CAD allows you to customize your community's penal codes, charge type
  names, bond type names, and more!
---

# Penal Codes

{% hint style="info" %}
Community customization is not included with the free version.\
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../getting-started/view-your-limits.md).
{% endhint %}

## What are penal codes?

Penal codes can easily be referenced and cited in records/reports as charges.

![Sonoran CAD - Penal Code Reference Window](<../../.gitbook/assets/image (338).png>)

![Sonoran CAD - Charges Section](<../../.gitbook/assets/image (368).png>)

### 1. Charge Types

You can create your own "Charge Type" options for penal codes. If your country does not have "felonies" you can edit or remove this option.

You can also use the "Auto Sort" feature to quickly format the order of these charge types.

Be sure to hit "Save" before exiting the page.

![Sonoran CAD - Custom Charge Types](<../../.gitbook/assets/image (369).png>)

### 2. Bond Types

You can create your own "Bond'/Bail Type" options for penal codes. Again, if your country does not use these, you can edit or remove them as needed.

You can also use the "Auto Sort" feature to quickly format the order of these charge types.

![Sonoran CAD - Custom Bond & Bail Types](<../../.gitbook/assets/image (326).png>)

### 3. Penal Codes

Adding, editing, or removing a penal code is easy. Simply click on the existing code to edit it, or press "New Penal Code" to create a new one.

![Sonoran CAD - Penal Code Management](<../../.gitbook/assets/image (361).png>)

![Sonoran CAD - Penal Code Editor](<../../.gitbook/assets/image (345).png>)

### 4. My locality doesn't call them "Penal Codes"

Sonoran CAD allows you to change the naming of "Penal Codes" to anything else you'd like.\
Learn more about our [geographical customization](geographical-settings.md).

## Import from Spreadsheet (CSV)

Sonoran CAD allows you to easily import your penal codes from a spreadsheet (.CSV) file.

{% hint style="danger" %}
**Spreadsheet (CSV) importing is only supported directly from Google sheets.**

Support will not be provided to users modifying their spreadsheets with Excel, or any other program. The official Google sheet includes specific safety checks preventing invalid formats, blank spaces, etc.
{% endhint %}

### 1. Copy the Google Sheet

Navigate to our [official penal code Google sheet ](https://docs.google.com/spreadsheets/u/0/d/10TCczXferWWFi8sYtccrqocRZ4WdpKB1s4hwRm2Iy6I/copy)and make a copy. Using a copy of our official sheet ensures your penal codes are formatted correctly.

**You may ONLY use the Google sheet directly. Editing this via Excel or any other program is NOT supported.**

![Penal Codes - Copy Sheet](<../../.gitbook/assets/image (185).png>)

### 2. Add Your Penal Codes

Now that you have copied this sheet into your Google Drive, you can add new rows and format your penal codes.

{% hint style="warning" %}
**Do NOT modify the very first row.** These names must remain the same to properly format the penal code structure.

Additionally, the `bondAmount` column must be kept as a number.\
All other columns must be formatted as text.
{% endhint %}

![](<../../.gitbook/assets/image (208).png>)

### 3. Download the CSV

In Google Sheets, navigate to File > Download > Comma Separated Values (.csv) to download the file.

![Google Sheets - Download CSV](<../../.gitbook/assets/image (155).png>)

### 4. Import the CSV File

In Sonoran CAD, navigate to Admin > Customization > Penal Codes

In the penal codes section, select the "Import" button.\
Then, select "CSV" as the import type and select your downloaded CSV file.

![Sonoran CAD - Import Data](<../../.gitbook/assets/image (97).png>)

![File Selector - Select File](<../../.gitbook/assets/image (202).png>)

After selecting the CSV file, your penal codes will be imported into the CAD and saved automatically.

### Troubleshooting

Having issues importing your CSV? [Be sure you are using and editing our Google Sheet with the Google Sheets program only](penal-codes.md#1-copy-the-google-sheet).

Our Google sheet includes specific error checking and validation to handle common mistakes.\
**Support is not provided if you are using Excel, or any other program.**

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

In Sonoran CAD, navigate to Admin > Customization > Penal Codes

In the penal codes section, select the "Import" button.\
Then, select "JSON" and paste the JSON object array of penal codes.

![Sonoran CAD - Import Data](<../../.gitbook/assets/image (97).png>)

![Sonoran CAD - Paste JSON Content](<../../.gitbook/assets/image (210).png>)

After pasting the JSON content, your penal codes will be imported into the CAD and saved automatically.
