---
description: >-
  Display your identifier information, attached call information, and more on
  your gaming stream!
---

# 📺 Twitch Overlay and Bot

![](../.gitbook/assets/live-banner.png)

![Sonoran CAD - Live Stream Overlay](../.gitbook/assets/overlay%20%282%29.gif)

![Stream Overlay - Bodycam](../.gitbook/assets/image%20%28255%29.png)

## What is Sonoran CAD's Livestream Overlay?

Sonoran CAD has a built-in livestream overlay, allowing you to display your live unit information, call information, and more!

Our Twitch bot can also be configured to send out chat messages when data is modified.

## Bodycam Overlay

![Sonoran CAD - Stream Overlay Bodycam](../.gitbook/assets/overlay.png)

{% hint style="warning" %}
The free version of the overlay does not include the customizable bodycam asset.  
However, you can still create [custom overlay text](twitch-overlay-and-bot.md#custom-overlay-text) with the free version!

Learn more about the [full version of Sonoran CAD's stream overlay](twitch-overlay-and-bot.md#purchasing-the-overlay)!

The bodycam creates local text files and hosts a local webserver.  
**This requires the** [**desktop** ](../downloads/)**application to run.**
{% endhint %}

The stream overlay also includes a customizable version of the popular [XION Chase Cam asset](https://github.com/zhivotnoya/XION-ChaseCam).

This allows you to customize a bodycam overlay on your stream, with your real-time unit and call information.

### 1. Set a File Directory

**First, ensure you are using the** [**desktop** ](../downloads/)**version of Sonoran CAD.** The application has to generate physical files, and host a local webserver to work. This can not be done in a browser.

In the stream overlay, open the txt file directory viewer and select a folder for the text files and bodycam webpage to be generated:

![Stream Overlay - Text file Location](../.gitbook/assets/8d764649f961657fc6245ce3cce2a62d.gif)

### 2. Configuring the Bodycam Contents

In the livestream overlay config section, expand the `Bodycam` section.

Here, you can enable and customize the data placement and keys just as before with the [customizable text files](twitch-overlay-and-bot.md#3-toggle-and-configure-keys).

* Expand the `Unit Updates` or `Call Updates` Section
* Toggle `ON` the txt file
* `COPY` the field key
* `PASTE` the field key into the bodycam section
* `SAVE` the configuration once complete

You can also optionally specify a different port for the bodycam webpage to run on \(`9990` is the default\).

![](../.gitbook/assets/image%20%28256%29.png)

### 3. Add the Bodycam to OBS

In OBS, add a new "Browser" source and paste the URL listed in the bodycam section.  
By default, this will be `http://localhost:9990`

![OBS - New Browser Source](../.gitbook/assets/image%20%28257%29.png)

Paste the URL into the browser source and hit OK.

![](../.gitbook/assets/image%20%28254%29.png)

### 4. Customize the Size and Placement

You can now customize the size and placement of this browser window in OBS as you normally would.

## Smart Lighting

{% hint style="danger" %}
**This feature has not yet been released.**
{% endhint %}

Sonoran CAD allows you to configure in-game events to smart lighting in your own home!

When you toggle your police lights in-game, your room can flash with custom lighting patterns to further immerse and simulate real world lighting.

### Supported Smart Bulbs

At this time, Sonoran CAD currently supports the following smart bulb types:

#### [Wyze Color](https://wyze.com/wyze-bulb-color.html)

Many of our development team members personally use and recommend these bulbs. Due to the design, these tend to provide the fastest response type with more complex lighting patterns. A 4 pack typically costs ~$40 \($10/bulb\).

#### [Philips Hue](https://www.philips-hue.com/en-us/products/smart-light-bulbs)

Philips Hue is significantly more expensive, but is typically the most widely known option. This option will also require the purchase of a Hue bridge/hub. Due to the design, these tend to have a ~10ms+ delay when setting the color of multiple bulbs at a time.

We recommend keeping the `delay` for custom sequences &gt; 500ms.

### 1. Searching for Bulbs

The smart lighting section has multiple `Scenes`

* `Restore`: Set when you are no longer flashing emergency lights, turn signals, etc.
* `Emergency Lights`: While you are in an emergency vehicle with the lights on
* `Panic`: While your panic status is toggled
* `Left Turn Signal`: While your left hand turn signal is on
* `Right Turn Signal`: While your right hand turn signal is on
* `Hazard Lights`: While your hazard lights are on

Expand the `Scene` &gt; `Add Bulb` &gt; `Search for Bulbs` &gt; Select `Wyze` or `Philips Hue`

Note: The Wyze Color bulbs require your Wyze login credentials. This makes a simulated request to your homepage for all lights on your account. The Wyze credentials are not saved on both the local Desktop app, or Sonoran CAD's servers. However, you may wish to update/reset your password, or even create a new Wyze account that shares these bulbs.

![Sonoran CAD - Scan for Smart Bulbs](../.gitbook/assets/image%20%28271%29.png)

### 2. Creating Sequences

You can add the desired bulb to your `Scene`. Each `scene` is made up of multiple `frames`.



### 3. Testing and Using In-Game

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

## Custom Overlay Text

The overlay is immensely customizable, allowing you to customize every piece of data displayed.

### 1. Accessing the Overlay Window

The overlay configuration modal can be opened by navigating to `Start Menu` &gt; `System` &gt; `Stream Overlay`. Or, by searching in the start menu.

### 2. Configuring Text File Location

While the Twitch bot can run in a browser instance of Sonoran CAD, the [desktop application](../downloads/) **is required**, to generate unit/call data txt files.

In the stream overlay, open the txt file directory viewer and select a folder for the text files to be generated:

![Stream Overlay - Text file Location](../.gitbook/assets/8d764649f961657fc6245ce3cce2a62d.gif)

### 3. Toggle and Configure Keys

{% hint style="warning" %}
The **free version** of the overlay is limited to three \(3\) data keys.  
Learn more about the [full version of Sonoran CAD's stream overlay](twitch-overlay-and-bot.md#purchasing-the-overlay)!
{% endhint %}

In the `Configuration` tab, toggle on the desired data fields for your unit and dispatch call information.

For every field toggled, a text file will be generated to be viewed in OBS.  
However, we **recommend creating custom text files** to combine multiple data fields in a single text file.

![Stream Overlay - Custom Text Files](../.gitbook/assets/image%20%28251%29.png)

#### Data Field Keys:

These can be easily copied from the UI, by pressing the `Copy` button next to the toggled field and pasting into the custom file's key textbox.

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

### 4. Save your Configuration

Don't forget to save your configuration!

### 5. Configure Data in OBS

In OBS, add a new text source:

![OBS - New Text Source](../.gitbook/assets/image%20%28245%29.png)

In the text source properties, select `Read from File` and select one of your generated data key files from the [location specified earlier](twitch-overlay-and-bot.md#2-configuring-text-file-location).

![Stream Overlay - Text Files](../.gitbook/assets/image%20%28241%29.png)

![Stream Overlay - Text file Viewer](../.gitbook/assets/image%20%28246%29.png)

You can now place the text field anywhere in your OBS stream layout.

You can also customize the fonts, change the background and more!

## Purchasing the Overlay

The free version of the livestream overlay allows anyone to test out the basic functionality. The free version does not allow use of the [Twitch bot](twitch-overlay-and-bot.md#configuring-the-twitch-bot), [bodycam](twitch-overlay-and-bot.md#bodycam-overlay), and is locked to a maximum of three custom "data keys".

The full version of Sonoran CAD's livestream overlay and Twitch bot is available for $7.99/mo.

Users can purchase a license to the full version in their billing center:

{% page-ref page="../pricing/faq/create-and-manage-a-subscription.md" %}

### 

