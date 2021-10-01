---
description: >-
  Database Sync is a highly advanced feature allowing you to automatically pull
  all character, license, and vehicle registration data from your own in-game
  database directly to Sonoran CAD.
---

# Database Sync and Merge

{% hint style="warning" %}
Database Sync requires the **plus** version of Sonoran CAD or higher.  
Database Merge requires the **pro** version of Sonoran CAD.

For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../../tutorials/getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../other-products/server-hosting.md)!
{% endhint %}

Database Sync is a highly advanced feature allowing you to automatically pull all character, license, and vehicle registration data from your own in-game database directly to Sonoran CAD.

This feature is specifically designed for frameworks like ESX and QBus/QBCore, but is compatible with any MySQL database.

## Video Configuration Tutorial

View our [video tutorial](https://youtu.be/UfMup7KkpEg) on enabling Database Sync.

## Written Configuration Guide

Configuring Sonoran CAD's Database Sync may seem complicated, but you are simply specifying your table names and column values where your in-game data is stored.

REQUIRED fields in the CAD are shown in red. All other fields are optional and are not required to work properly.

## Connection Credentials

In order for Sonoran CAD to connect to your SQL database, connection credentials must be configured properly.

### 1. Retrieve your SQL Connection Credentials

Sonoran CAD requires an **external** connection to your database.

View our guide on creating a new read-only SQL user for external use.

{% page-ref page="database-sync-credentials.md" %}

### 2. Enable Database Sync and Merge

Expand the `SQL Connection Credentials` section of the configuration, and toggle on Database Sync and the optional Database Merge feature.

#### What is Database Merge?

Database Merge is an additional feature that allows you to save off additional, manually specified data in the CAD.

**Example:**

DB Merge pulls a character record into the CAD, but the `address` field in your custom record is blank \(your DB doesn't have this info\). DB merge allows you to manually edit the record pulled from your database and edit any blank field.

Next time you look up this character, it will pull the same character info from your database and then merge this with the manually specified data saved in Sonoran CAD.

### 3. Enter the required fields below.

![Sonoran CAD - DB Sync SQL Credentials](../../.gitbook/assets/image%20%28176%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Type</td>
      <td style="text-align:left">This is the type of SQL database your server is using (MySQL, PostgreSQL,
        etc.)</td>
    </tr>
    <tr>
      <td style="text-align:left">Host/Address</td>
      <td style="text-align:left">
        <p>This is the <b>external </b>IP address or domain address to your SQL database.
          <br
          />
        </p>
        <p><em>Note:</em> This IP will never be <code>localhost</code> or <code>127.0.0.1</code>.
          This must be the external IP or domain to reach your database. <a href="../../sonoran-cad/api-integration/getting-started/retrieving-your-credentials.md">Learn more about creating an external SQL connection.</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Port</td>
      <td style="text-align:left">This is the port your database is accessible from. Typically, the default
        port for MySQL is 3306.</td>
    </tr>
    <tr>
      <td style="text-align:left">Database</td>
      <td style="text-align:left">This is the database or schema name that contains your community&#x2019;s
        character, license and vehicle registration tables.</td>
    </tr>
    <tr>
      <td style="text-align:left">Username</td>
      <td style="text-align:left">This is the SQL account username.</td>
    </tr>
    <tr>
      <td style="text-align:left">Password</td>
      <td style="text-align:left">This is the password for the SQL account.</td>
    </tr>
  </tbody>
</table>

### 3. Test the Connection

Once the required SQL connection fields have been specified, select the “Test Connection” button.  
This will query your database for the version.  
  
If you see an alert similar to the following, your connection is successful:

![DB Sync - Connection Successful](../../.gitbook/assets/image%20%28155%29.png)

If you see an error message, it's likely you have not [properly setup your new SQL user's credentials](database-sync-credentials.md) or opened the database port for external use.

## Character Mapping

{% hint style="warning" %}
Sonoran CAD requires character mapping to be properly configured for the additional license and vehicle registration mapping.
{% endhint %}

### 1. What is DB Sync Mapping?

The DB sync configuration is designed to show Sonoran CAD the specific tables and columns that data can be pulled from in your database.

### 2. Table Columns and Name

The `table name` field will contain the name of your database table containing character records.

The `column name` field will contain the name of the specific column in the character records table containing data for this row.

The `Character Mapping Column` contains a unique ID for the specific character. This unique identifier will also map records in your license and vehicle registration tables back to the character that owns them. Typically, this is a Steam ID or license ID.

Character records can also pull data from multiple different tables, such as a properties table to add address information. Just be sure that those additional tables have a proper `identifier` column to map back to the other characters table.

**Example:**

In our database, the `characters` table contains our character records. The `identifier` column contains the character's unique ID, the `firstname` column contains the characters first name, the `lastname` character contains the characters last name, etc.

![SQL Table Example](../../.gitbook/assets/image%20%28141%29.png)

![DB Sync Character Mapping Example](../../.gitbook/assets/image%20%28152%29.png)

### 3. Enable, Save and Test

Be sure that you have enabled character mapping via the toggle. Once your character mapping has been completed, hit the save button and then the test button. The test button will attempt to select a single random character with the mapping configuration specified.

If you see "Success!" move onto the next section.

## License and Vehicle Mapping

Licenses and Vehicle registrations can also be automatically pulled via CAD search with Database Sync.

### 1. Table Columns and Names

Similar to the character mapping, specify the table name containing your vehicle registrations or licenses. Unlike character mapping, data for these records can only be pulled from a single table.

The vehicle and license mapping will also need to have the `Character Mapping Column` specified. Again, this is the name of the column in your license/vehicle table containing a unique ID that maps back to the character that owns it.

**Example:**

In our database, the `owned_vehicles` table contains our stored vehicles. The `owner` column contains the character's unique ID that owns the vehicle, and the `plate` column contains the vehicle's license plate.

![SQL Vehicle Table Example](../../.gitbook/assets/image%20%28132%29.png)

![DB Sync - Vehicle Mapping Example](../../.gitbook/assets/image%20%28188%29.png)

### 2. Enable, Save and Test

Be sure that you have enabled the license/vehicle mapping via the toggle. Once your mapping has been completed, hit the save button and then the test button. The test button will attempt to select a single random license or vehicle with the mapping configuration specified.

If you see "Success!" move onto the next section.

## JSON Columns

Many databases store data in a JSON formatted column. Sonoran CAD can also parse these columns for data.

### 1. View the JSON Data

In our database, the `accounts` column stores JSON formatted data. For this example, we want to display the `bank` money in the custom character record.

![SQL - JSON Column Example](../../.gitbook/assets/image%20%28153%29.png)

To more easily view the JSON data, we can copy it from the cell and paste it into a [JSON formatter](http://jsonviewer.stack.hu/).

In the [JSON formatter](http://jsonviewer.stack.hu/), we can paste it and select `Format`.

![](../../.gitbook/assets/image%20%28187%29.png)

We can see that the JSON "key" for the bank account amount is `bank`.

### 2. Nested JSON Values

Nested JSON values are also supported.  
Here, the `eye_color` is a JSON object, with the `item` property of `0`.

![Database - Nested JSON Value](../../.gitbook/assets/image%20%28278%29.png)

In the DB Sync config, we list the JSON key as `eye_color.item`

![](../../.gitbook/assets/image%20%28277%29.png)

Then, we can use [friendly mapping](./#friendly-mapping) to convert the eye color `0` value to an actual color, like "brown".

## External Keys

### Introduction

In some cases, your license or vehicle registration tables may not directly contain a `Character Mapping ID` column \(a column with an ID that directly maps back to the character/civilian record\), but may contain a unique ID that maps back to a specific character in another table.

### Example: DB Layout

In this example, the `vehicle` table contains all of the vehicle information, but does not contain a `CharacterID` column. Instead, the `vehicle` table contains a `VehicleRegistrationID` column.

The `VehicleRegistrationId` column then maps to the `vehicleregistration` table. The `vehicleregistration` table then contains a corresponding `CharacterId` column, which maps back to the `character` table.

![Sonoran CAD - External Key DB Layout](../../.gitbook/assets/image%20%28263%29.png)

### Example: CAD Config

In the CAD, the configuration is simple.

Toggle on the `External Key` checkbox, as the `vehicle` table's `VehicleId` needs to be mapped to an external table to be turned into the proper `characterId`.

Specify the external key's table \(`vehicleregistration`\) and the external key's column `CharacterId`.

![Sonoran CAD - External Key](../../.gitbook/assets/image%20%28265%29.png)

### 2. Set the JSON Column and Key

Back in the mapping panel, we toggle the field as a `JSON Column` and set the column name to `accounts` as this is the column in our character table that contains the JSON data.

We can then set the JSON Key for this data as `bank`.

![DB Sync - JSON Column](../../.gitbook/assets/image%20%28139%29.png)

## Friendly Mapping

Friendly mapping allows you to convert any raw database value to a more user friendly value.  
Ex: `drive_license` in your database is converted to `Driver's License`.

### 1. Find Values to "Friendly Map"

In our SQL table, we can see the character's job columns has text values that can be improved. The `taxi` job value can be automatically converted to `Taxi Driver` in DB Sync records, and the `cardealer` jon can be automatically converted to `Car Dealer`.

![SQL Table - Unfriendly Values](../../.gitbook/assets/image%20%28173%29.png)

### 2. Configure the Friendly Mapping

In our character table mapping, we can select `Modify` on the `job` field's friendly mapping.

![DB Sync - Modify Friendly Mapping](../../.gitbook/assets/image%20%28160%29.png)

In the editor, we can now map the raw database value of `taxi` to a friendly value of `Taxi Driver` and the raw db value of `cardealer` to `Car Dealer`.

Be sure to hit save in the friendly mapping editor, and then save the configuration for your mapping section.

These new friendly mapped values will even work with [custom search types](../../tutorials/customization/custom-search-types.md)!

![Friendly Mapping Editor](../../.gitbook/assets/image%20%28143%29.png)

### Import via CSV

#### 1. Copy the Google Sheet

Navigate to our [official friendly mapping Google Sheet](https://docs.google.com/spreadsheets/u/1/d/1Q83yqdH-YGlAv9zW-hJ1dA5k5hYPQDLfeXby0BXB6-k/copy) and make a copy. Using a copy of our official sheet ensures your friendly mapping is formatted correctly.

**You may ONLY use the Google sheet directly. Editing this via Excel or any other program is NOT supported.**

![Sonoran CAD - Copy Friendly Mapping CSV](../../.gitbook/assets/image%20%28285%29.png)

**2. Add your Friendly Mappings**

Be sure to leave the top header line as it is. Below the header, add in your friendly mapping keys and values.

![Sonoran CAD - Edit Friendly Mapping CSV](../../.gitbook/assets/image%20%28284%29.png)

#### 3. Download the CSV

In Google Sheets, navigate to File &gt; Download &gt; Comma Separated Values \(.csv\) to download the file.

![Sonoran CAD - Download Friendly Mapping CSV](../../.gitbook/assets/image%20%28282%29.png)

#### 4. Import the CSV File

In the friendly mapping editor select `Import` &gt; `CSV` &gt; Select your downloaded Google spreadsheet

Then, save the mapping and save the database sync config.

![](../../.gitbook/assets/image%20%28283%29.png)

### Import from JSON

You can also build and format your friendly mapping from raw JSON and paste them directly into the UI.

#### 1. Format the JSON Structure

The JSON structure is an object array. Be sure to strictly follow the format.

```javascript
[
  {
    "dbValue": "0",
    "friendlyValue": "Brown"
  },
  {
    "dbValue": "1",
    "friendlyValue": "Green"
  },
  {
    "dbValue": "2",
    "friendlyValue": "Blue"
  }
]
```

#### 2. Import the JSON Structure

In the friendly mapping editor select `Import` &gt; `JSON` &gt; Paste your JSON formatted structure

![Friendly Mapping - Import via JSON](../../.gitbook/assets/image%20%28281%29.png)

## Custom Record Fields

Sonoran CAD's records are entirely customizable, this includes database sync records! You can easily enable database sync mapping for any custom field you add to a character, license, or vehicle registration record.

### 1. Edit your Custom Record

Navigate to Admin &gt; Customization &gt; Custom Records

Select your custom character, license, or vehicle registration record to open the editor.

Simply check the box to enable database sync mapping for any new or existing field. For this example, we'll enable it for a new `job` field in our character's table.

Be sure to save your custom record format after enabling this!

![Custom Records - DB Sync Mapping Toggle](../../.gitbook/assets/image%20%28186%29.png)

### 2. Configure the Newly Mapped Field

Back in our database sync editor, we can now see the new `Job` field has been added. We can map this new field to our database as any other field.

![Database Sync - Custom Field Mapping](../../.gitbook/assets/image%20%28133%29.png)

