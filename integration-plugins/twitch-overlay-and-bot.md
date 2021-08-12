---
description: >-
  Display your identifier information, attached call information, and more on
  your gaming stream!
---

# 📺 Twitch Overlay and Bot

![Sonoran CAD - Live Stream Overlay](../.gitbook/assets/live-banner.png)

![Sonoran CAD - Stream Overlay](../.gitbook/assets/overlay.gif)

## What is Sonoran CAD's Livestream Overlay?

Sonoran CAD has a built-in livestream overlay, allowing you to display your live unit information, call information, and more!

Our Twitch bot can also be configured to send out chat messages when data is modified.

## Configuring the Overlay

The overlay is immensely customizable, allowing you to customize every piece of data displayed.

### 1. Accessing the Overlay Window

The overlay configuration modal can be opened by navigating to `Start Menu` &gt; `System` &gt; `Stream Overlay`. Or, by searching in the start menu.

### 2. Configuring Text File Location

While the Twitch bot can run in a browser instance of Sonoran CAD, the [desktop application](../downloads/) **is required**, to generate unit/call data txt files.

In the stream overlay, open the txt file directory viewer and select a folder for the text files to be generated:

![Stream Overlay - Text file Location](../.gitbook/assets/8d764649f961657fc6245ce3cce2a62d.gif)

### 3. Toggle Desired Keys

In the `Configuration` tab, toggle on the desired data fields for your unit and dispatch call information.

For every field toggled, a text file will be generated to be viewed in OBS.

{% hint style="warning" %}
The free version of the overlay is limited to three \(3\) data keys.  
Learn more about the [full version of Sonoran CAD's stream overlay](twitch-overlay-and-bot.md#purchasing-the-overlay)!
{% endhint %}

![Stream Overlay - Data Field Toggles](../.gitbook/assets/image%20%28247%29.png)

### 4. Save your Configuration

Don't forget to save your configuration!

### 5. Configure Data in OBS

In OBS, add a new text source:

![OBS - New Text Source](../.gitbook/assets/image%20%28245%29.png)

In the text source properties, select `Read from File` and select one of your generated data key files from the [location specified earlier](twitch-overlay-and-bot.md#2-configuring-text-file-location).

_Note: These files are generated and updated when your unit or call data changes. Re-opening the police, fire, or EMS pages will fully regenerate all files._

![Stream Overlay - Text Files](../.gitbook/assets/image%20%28241%29.png)

![Stream Overlay - Text file Viewer](../.gitbook/assets/image%20%28246%29.png)

You can now place the text field anywhere in your OBS stream layout.

You can also customize the fonts, change the background and more!

## Custom Text Files

While the stream overlay generates a unique text file for every toggled data field, you can also configure custom text files with multiple data fields. This makes formatting on your overlay easier with less individual fields.

### 1. Add a New Custom File

In the overlay configuration section, expand the `Custom Text Files` section and select `Add`.

![Stream Overlay - Custom Text Files](../.gitbook/assets/image%20%28249%29.png)

### 2. Set the File Name and Data Keys

Set the custom text file's name and data keys using the text boxes. The data keys are formatted as `{someKey}` and will have their values replaced automatically with the live unit or dispatch call data.

{% hint style="warning" %}
In order for the data key to be replaced/updated in the custom text file, the **field MUST be toggled/enabled** in the Unit Updates or Call Updates section above.
{% endhint %}

| Key | Description |
| :--- | :--- |
| {unit\_status} | Unit Status |
| {unit\_location} | Unit Location |
| {unit\_aop} | Unit AOP |
| {unit\_number} | Unit Number |
| {unit\_name} | Unit Name |
| {unit\_agency} | Unit Agency |
| {unit\_department} | Unit Department |
| {unit\_subdivision} | Unit Subdivision |
| {unit\_rank} | Unit Rank |
| {unit\_group} | Unit Group |
| {unit\_panic} | Unit Panic Status |
| {call\_id} | Dispatch Call ID |
| {call\_origin} | Dispatch Call Origin |
| {call\_status} | Dispatch Call Status |
| {call\_priority} | Dispatch Call Priority |
| {call\_block} | Dispatch Call Block |
| {call\_address} | Dispatch Call Address |
| {call\_postal} | Dispatch Call Postal |
| {call\_title} | Dispatch Call Title |
| {call\_code} | Dispatch Call 10-Code |
| {call\_description} | Dispatch Call Description |

### 3. Add the Text File to OBS

**Be sure to save your new configuration!**

\*\*\*\*[As with the regular text files](twitch-overlay-and-bot.md#5-configure-data-in-obs), these custom formatted ones can be imported and live-updated through OBS.

## Configuring the Twitch Bot

Sonoran CAD's stream overlay also comes with a configurable Twitch bot. This bot will send out chat updates when unit or call data is updated.

{% hint style="warning" %}
The Twitch bot is **not included with the free version** of the Stream Overlay.  
  
[Learn more about the full version of Sonoran CAD's stream overlay.](twitch-overlay-and-bot.md#purchasing-the-overlay)
{% endhint %}

### 1. Create a Twitch OAuth Token

Create a new Twitch OAuth token by going to [https://twitchapps.com/tmi/](https://twitchapps.com/tmi/)

### 2. Configure your Twitch Bot Token and Username

Using the overlay in OBS, select the `Twitch Bot` button in the taskbar.  
Paste in your Twitch channel name and OAuth key.

![Overlay - Twitch Bot Credentials](../.gitbook/assets/image%20%28248%29.png)

Once set, you can press `Test` to display a test message in your Twitch chat.

### 3. Configure the Bot's Event Data

Every piece of unit and call data can be toggled on or off individually.

**It is highly recommended to only toggle on data updates that will not be frequently spammed.** Toggling too many data fields and updating data too quickly may result in **Twitch rate limiting your bot.**

![Overlay - Twitch Data Fields](../.gitbook/assets/image%20%28242%29.png)

### 4. Save and Run

Once you have configured your Twitch Bot's credentials and data fields, press `Save`.

Now, whenever one of those data fields is updated, your Twitch bot will send a chat message.

![Sonoran CAD - Stream Overlay](../.gitbook/assets/overlay.gif)

### Debugging the Twitch Bot

If you're having issues seeing the Twitch bot messages, view the `Twitch Logs` panel in the stream overlay.

This will contain valuable information on the twitch bot's connection, rate limiting, and other errors.

![Overlay - Twitch Logs](../.gitbook/assets/image%20%28244%29.png)

If you have too many data fields toggled, and are sending Twitch updates too quickly you may experience rate limiting.

## Purchasing the Overlay

The free version of the livestream overlay allows anyone to test out the basic functionality. The free version does not allow use of the Twitch bot, and is locked to a single unit/call data window with a maximum of three "data keys".

The full version of Sonoran CAD's livestream overlay and Twitch bot is available for $7.99/mo.

Users can purchase a license to the full version in their billing center:

{% page-ref page="../pricing/faq/create-and-manage-a-subscription.md" %}

### 

