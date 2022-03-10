---
description: Learn how to create custom record and report types for your community!
---

# Creating Custom Record and Report Types

{% hint style="danger" %}
Custom record and reports are limited based upon your subscription version.\
For more information, please view our [pricing page](../../pricing/faq/).
{% endhint %}

## What are custom records and reports?

Sonoran CAD allows your community to create custom records and incident reports for police, fire, and EMS services. This tutorial will cover the basics of creating a new custom report or record and general usage of the system.

## Video Tutorial

View our [video tutorial](https://youtu.be/UclCEnm5FHM) on creating custom reports and records.

## Creating a new Report or Record:

### 1. Navigate to the Record Editor

Navigate to Admin > Customization > Custom Records

### 2. Select the new Record Type

From the "New Record Type" dropdown, select the desired record type.\
\
Records follow the standard record editing and lookup system, and require a civilian or vehicle field to be searched.\
\
Reports can be searched in the unit's report center via number or identifier.

![Sonoran CAD's Custom Record Types](<../../.gitbook/assets/image (1).png>)

### 3. Add Custom and Pre-made Sections

Add your desired custom and premade sections, edit fields, and more!

![Select custom or premade sections from the dropdown buttons](<../../.gitbook/assets/image (2).png>)

If your section is a custom character or vehicle field, you can toggle on the search button. This allows the section to be filled via when creating a new one.

The enable duplicate button allows users to click and create a new copy of the section while filing the record.

![Sonoran CAD: Custom Record Section Options](<../../.gitbook/assets/image (169).png>)

{% tabs %}
{% tab title="Field Type" %}
Fields can be a set to `text`, `select`, `textarea`, `date`, `time`, `label`, `address` or `checkboxes`.

#### 1. Text:

These fields are generic text boxes.

#### 2. Select:

The select field allows you to customize a dropdown box.

![The 'SELECT' field option](<../../.gitbook/assets/image (18) (1) (1) (1) (1) (1) (1).png>)

![A 'SELECT' field shown in the record editor](<../../.gitbook/assets/image (16) (2) (2) (2) (2) (1) (1).png>)

#### 3. TextArea:

The select field allows you to create a large text area.

![The 'TEXTAREA' field option](<../../.gitbook/assets/image (4).png>)

![A 'TEXTAREA' field shown in the record editor](<../../.gitbook/assets/image (5).png>)

#### 4. Checkboxes

The checkboxes type allows you to create multiple checkboxes, similar to the premade flags section.

![The 'CHECKBOXES' field option](<../../.gitbook/assets/image (26).png>)

![A 'CHECKBOXES' field shown in the record editor.](<../../.gitbook/assets/image (27).png>)

#### 5. Date

The date field allows you to specify a date field. You can also specify the formatting in the mask column.

When `readOnly` is selected, this field will auto-fill the current date for new records.

![The 'DATE' field option](<../../.gitbook/assets/image (28).png>)

![The 'DATE' field shown in the record editor](<../../.gitbook/assets/image (29).png>)

#### 6. Time

The time field allows you to specify a time field.

![The 'TIME' field option](<../../.gitbook/assets/image (30).png>)

![The 'TIME' field shown in the record editor](<../../.gitbook/assets/image (31).png>)

#### 7. Image

The image field allows you to specify an image to be displayed.

![The 'IMAGE' field option.](<../../.gitbook/assets/image (32).png>)

![The 'IMAGE' field shown in the record editor](<../../.gitbook/assets/image (33).png>)

#### 8. Linked Records

The linked records field allows you to link and cross-reference other records and reports to this record.

![Sonoran CAD - Linked Records](<../../.gitbook/assets/image (85).png>)

#### 9. Flags

Custom flag options can be added to every record template. When checked, these flags will show up as alerts on any lookup. Similar to a checkboxes section, you will need to expand the section and add options.

![Sonoran CAD - Custom Flags](<../../.gitbook/assets/image (86).png>)

#### 10. Label

Labels can display static text, along with color attributes.

![Sonoran CAD - Custom Record Label](<../../.gitbook/assets/image (168).png>)

#### 11. Address

The address dropdown will auto-filter [street address names that have been imported via CSV](addresses-and-street-names.md).

![Sonoran CAD - Custom Record Address Field](../../.gitbook/assets/90433cf83d1d487c05d18ea392289815.gif)

#### 12. Unit Information

The `UNIT_NUMBER`, `UNIT_NAME`, `UNIT_RANK`, `UNIT_AGENCY`, `UNIT_DEPARTMENT`, `UNIT_SUBDIVISION`, `UNIT_AGENCY_LOCATION`, `UNIT_AGENCY_ZIP`, and `UNIT_LOCATION` field types will all automatically insert the unit's information when they create a new record.

![Sonoran CAD - Custom Record Unit Information Fields](<../../.gitbook/assets/image (304) (1) (1).png>)
{% endtab %}

{% tab title="Field Options" %}
#### 1. Preview:

This will show the field label and value in the lookup table preview.

![Input field with PREVIEW toggled](<../../.gitbook/assets/image (6).png>)

![Previewed field shown in a lookup table](<../../.gitbook/assets/image (5) (1).png>)

#### 2. Supervisor

This will disable the field for all non-supervisor unit identifiers.\
Your unit's supervisor status can be set in the unit identifier editor.\


![Input field with SUPERVISOR toggled](<../../.gitbook/assets/image (7).png>)

![Supervisor field highlighted red](<../../.gitbook/assets/image (8).png>)

#### 3. Required

Required fields will require the unit to enter something into the field before the record can be submitted.

![Input field with REQUIRED toggled](<../../.gitbook/assets/image (9).png>)

![Required field shown in the record editor](<../../.gitbook/assets/image (10).png>)

#### 4. Unique

Unique fields enforce that no duplicate values for this field are stored in the database. These values are enforced for the specific record template only.

Unique fields can only be on non-DB Sync records and in custom sections.

![Sonoran CAD - Unique Field](<../../.gitbook/assets/image (170).png>)

![Sonoran CAD - Unique Field Error](<../../.gitbook/assets/image (171).png>)

#### 5. Read Only

Read only fields prevent the user from entering new or modified text. This is used for auto-filled fields like unit information when a new record is created.

Note: The `date` field will auto-fill with the current date if `readOnly` is toggled.

![Custom Records - Read Only Toggle](<../../.gitbook/assets/image (305) (1) (1).png>)

![Custom Records - Read Only Fields](<../../.gitbook/assets/image (302) (1) (1).png>)
{% endtab %}

{% tab title="Field Mask" %}
The field mask allows you to specify a required format for the field.

| Token | Description  |
| ----- | ------------ |
| #     | Numeric      |
| S     | Letter A-Z   |
| X     | Alphanumeric |

#### Example: Numbers

Specifying `###` allows the user to only enter 3 numbers in the field.

![](<../../.gitbook/assets/image (34).png>)

#### Example: Phone Number

Specifying `(###) ### - ####` formats the user's input into a phone number.

![](<../../.gitbook/assets/image (35).png>)
{% endtab %}

{% tab title="Field Size" %}
The field size slider allows you to select a field size value between 1 and 12.

Every row of a record has a space divisible by 12.

![Record fields with sizes 3, 3, and 8](<../../.gitbook/assets/image (11).png>)

![Record editor with custom field sizes](<../../.gitbook/assets/image (12).png>)
{% endtab %}
{% endtabs %}

### 4. Save the Record

Be sure to set the record name, and press SAVE

![Saving your new custom record](<../../.gitbook/assets/image (13).png>)

## Using your new Record Type

In the police, dispatch, fire, or EMS page you can now [add ](../records-management/adding-a-criminal-record.md)or [search ](../records-management/searching-for-records.md)for the new record type.

## Using your New Report

### 1. Accessing the Reports Center

In the police, dispatch, fire, or EMS page, select "REPORTS" in the top action menu bar\
From here, you can create a new report, search existing reports, and view reports requiring supervisor actions.\


![Sonoran CAD Reports Center](<../../.gitbook/assets/image (14).png>)

### 2. Creating a New Report

Select "New Report" and the desired custom report type from the dropdown button\
From there, you can fill out the fields and add the record.

{% hint style="info" %}
If the "NEW REPORT" button, or actions on the report viewer are disabled, you are missing the [permissions ](../getting-started/permissions.md)to do so.
{% endhint %}

![](<../../.gitbook/assets/image (15).png>)

### 3. Supervisor Panel

The supervisor panel shows all reports that have a blank field that requires supervisor permissions.\
If you do not have the supervisor panel enabled, you will need to have the [supervisor permission granted on your account](../getting-started/permissions.md).

###
