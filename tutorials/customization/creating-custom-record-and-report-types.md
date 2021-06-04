---
description: Learn how to create custom record and report types for your community!
---

# Creating Custom Record and Report Types

{% hint style="danger" %}
Custom record and reports are limited based upon your subscription version.  
For more information, please view our [pricing page](../../pricing/faq/).
{% endhint %}

## What are custom records and reports?

Sonoran CAD allows your community to create custom records and incident reports for police, fire, and EMS services. This tutorial will cover the basics of creating a new custom report or record and general usage of the system.

## Video Tutorial

View our [video tutorial](https://youtu.be/UclCEnm5FHM) on creating custom reports and records.

## Creating a new Report or Record:

### 1. Navigate to the Record Editor

Navigate to Admin &gt; Customization &gt; Custom Records

### 2. Select the new Record Type

From the "New Record Type" dropdown, select the desired record type.  
  
Records follow the standard record editing and lookup system, and require a civilian or vehicle field to be searched.  
  
Reports can be searched in the unit's report center via number or identifier.

![Sonoran CAD&apos;s Custom Record Types](../../.gitbook/assets/image%20%282%29.png)

### 3. Add Custom and Pre-made Sections

## 

Add your desired custom and premade sections, edit fields, and more!

![Select custom or premade sections from the dropdown buttons](../../.gitbook/assets/image%20%288%29.png)

If your section is a custom character or vehicle field, you can toggle on the search button:

![Sonoran CAD: Custom Section Search Toggle](../../.gitbook/assets/image%20%2869%29.png)

This allows the section to be filled via search when creating a new one.

{% tabs %}
{% tab title="Field Type" %}
Fields can be a set to `text`, `select`, `textarea`, `date`, `time`, `label`, `address` or `checkboxes`.

#### 1. Text:

These fields are generic text boxes.

#### 2. Select:

The select field allows you to customize a dropdown box.

![The &apos;SELECT&apos; field option](../../.gitbook/assets/image%20%2818%29%20%281%29%20%281%29.png)

![A &apos;SELECT&apos; field shown in the record editor](../../.gitbook/assets/image%20%2816%29%20%282%29%20%282%29.png)

#### 3. TextArea:

The select field allows you to create a large text area.

![The &apos;TEXTAREA&apos; field option](../../.gitbook/assets/image%20%2821%29.png)

![A &apos;TEXTAREA&apos; field shown in the record editor](../../.gitbook/assets/image%20%281%29.png)

#### 4. Checkboxes

The checkboxes type allows you to create multiple checkboxes, similar to the premade flags section.

![The &apos;CHECKBOXES&apos; field option](../../.gitbook/assets/image%20%2829%29.png)

![A &apos;CHECKBOXES&apos; field shown in the record editor.](../../.gitbook/assets/image%20%2834%29.png)

#### 5. Date

The date field allows you to specify a date field. You can also specify the formatting in the mask column.

![The &apos;DATE&apos; field option](../../.gitbook/assets/image%20%2836%29.png)

![The &apos;DATE&apos; field shown in the record editor](../../.gitbook/assets/image%20%2839%29.png)

#### 6. Time

The time field allows you to specify a time field.

![The &apos;TIME&apos; field option](../../.gitbook/assets/image%20%2831%29.png)

![The &apos;TIME&apos; field shown in the record editor](../../.gitbook/assets/image%20%2838%29.png)

#### 7. Image

The image field allows you to specify an image to be displayed.

![The &apos;IMAGE&apos; field option.](../../.gitbook/assets/image%20%2840%29.png)

![The &apos;IMAGE&apos; field shown in the record editor](../../.gitbook/assets/image%20%2832%29.png)

#### 8. Linked Records

The linked records field allows you to link and cross-reference other records and reports to this record.

![Sonoran CAD - Linked Records](../../.gitbook/assets/image%20%2894%29.png)

#### 9. Flags

Custom flag options can be added to every record template. When checked, these flags will show up as alerts on any lookup. Similar to a checkboxes section, you will need to expand the section and add options.

![Sonoran CAD - Custom Flags](../../.gitbook/assets/image%20%2895%29.png)

#### 10. Label

Labels can display static text, along with color attributes.

![Sonoran CAD - Custom Record Label](../../.gitbook/assets/image%20%2813%29.png)

#### 11. Address

The address dropdown will auto-filter [street address names that have been imported via CSV](addresses-and-street-names.md).

![Sonoran CAD - Custom Record Address Field](../../.gitbook/assets/90433cf83d1d487c05d18ea392289815.gif)
{% endtab %}

{% tab title="Field Options" %}
#### 1. Preview:

This will show the field label and value in the lookup table preview.

![Input field with PREVIEW toggled](../../.gitbook/assets/image%20%2814%29.png)

![Previewed field shown in a lookup table](../../.gitbook/assets/image%20%285%29%20%281%29.png)

#### 2. Supervisor

This will disable the field for all non-supervisor unit identifiers.  
Your unit's supervisor status can be set in the unit identifier editor.  


![Input field with SUPERVISOR toggled](../../.gitbook/assets/image%20%2812%29.png)

![Supervisor field highlighted red](../../.gitbook/assets/image%20%2819%29.png)

#### 3. Required

Required fields will require the unit to enter something into the field before the record can be submitted.

![Input field with REQUIRED toggled](../../.gitbook/assets/image%20%2822%29.png)

![Required field shown in the record editor](../../.gitbook/assets/image%20%286%29.png)
{% endtab %}

{% tab title="Field Mask" %}
The field mask allows you to specify a required format for the field.

| Token | Description |
| :--- | :--- |
| \# | Numeric |
| S | Letter A-Z |
| X | Alphanumeric |

#### Example: Numbers

Specifying `###` allows the user to only enter 3 numbers in the field.

![](../../.gitbook/assets/image%20%2835%29.png)

#### Example: Phone Number

Specifying `(###) ### - ####` formats the user's input into a phone number.

![](../../.gitbook/assets/image%20%2837%29.png)
{% endtab %}

{% tab title="Field Size" %}
The field size slider allows you to select a field size value between 1 and 12.

Every row of a record has a space divisible by 12.

![Record fields with sizes 3, 3, and 8](../../.gitbook/assets/image%20%287%29.png)

![Record editor with custom field sizes](../../.gitbook/assets/image%20%284%29.png)
{% endtab %}
{% endtabs %}

### 4. Save the Record

Be sure to set the record name, and press SAVE

![Saving your new custom record](../../.gitbook/assets/image%20%2817%29.png)

## Using your new Record Type

In the police, dispatch, fire, or EMS page you can now [add ](../records-management/adding-a-criminal-record.md)or [search ](../records-management/searching-for-records.md)for the new record type.

## Using your New Report

### 1. Accessing the Reports Center

In the police, dispatch, fire, or EMS page, select "REPORTS" in the top action menu bar  
From here, you can create a new report, search existing reports, and view reports requiring supervisor actions.  


![Sonoran CAD Reports Center](../../.gitbook/assets/image%20%289%29.png)

### 2. Creating a New Report

Select "New Report" and the desired custom report type from the dropdown button  
From there, you can fill out the fields and add the record.

{% hint style="info" %}
If the "NEW REPORT" button, or actions on the report viewer are disabled, you are missing the [permissions ](../getting-started/permissions.md)to do so.
{% endhint %}

![](../../.gitbook/assets/image%20%2815%29.png)

### 3. Supervisor Panel

The supervisor panel shows all reports that have a blank field that requires supervisor permissions.  
If you do not have the supervisor panel enabled, you will need to have the [supervisor permission granted on your account](../getting-started/permissions.md).

### 

