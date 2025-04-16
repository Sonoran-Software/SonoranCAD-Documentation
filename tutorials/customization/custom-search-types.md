---
description: >-
  Sonoran CAD allows you to add custom searchable/indexed fields to your custom
  records.
---

# Custom Search Types

{% hint style="danger" %}
Custom search types are limited based upon your subscription version.\
For more information, please view our [pricing page](../../pricing/faq/).
{% endhint %}

## Video Tutorial

View our [video tutorial and showcase](https://youtu.be/KecmGjMmNiQ) on Sonoran CAD's custom search type feature.

## Written Tutorial

### 1. Configure Search Types

In the admin customization menu, expand the lookup types section.

![Sonoran CAD - Custom Lookup Types](<../../.gitbook/assets/image (111).png>)

There are three sections for each lookup type:

1. Name
   * Label/Name of the lookup type
2. Field Mapping ID
   * Unique ID used to specify searchable columns in the custom record editor
3. Mask
   * Mask for the search bar - This uses the same mask system as the [custom records](creating-custom-record-and-report-types.md).

Once configured, press save.

### 2. Configure Your Custom Records

In the custom records editor, specify the `Field Mapping ID` from step one on the searchable field.\
If this searchable field is in your in-game database, you can also set up [database sync](../../integration-plugins/database-sync-and-merge/) mapping to pull that data from in-game when records are opened.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption><p>Sonoran CAD - Custom Records Field Mapping ID</p></figcaption></figure>

Press save, then move onto the next step.

### 3. Configure Database Sync Column (Optional)

If the search field is provided by your in-game database with [database sync](../../integration-plugins/database-sync-and-merge/), this custom record column will be display in your database sync configuration for any character, license, or vehicle registration.

This will then allow you to search characters, licenses, or vehicle registrations from your in-game database based on this custom column value.

![Sonoran CAD - Database Sync and Custom Searches](<../../.gitbook/assets/image (238).png>)

### 4. Make a NEW Record

With the exception of database sync records, any existing records with this field will **not** be searchable.

You will need to create a new record with the custom searchable field in order to find it via custom lookup.

### 5. Run a Lookup

The lookup window will now display your new custom search types.\
You can now search your records (including database sync/merge) using these custom search boxes.

![Sonoran CAD - Custom Search Fields](<../../.gitbook/assets/image (236).png>)
