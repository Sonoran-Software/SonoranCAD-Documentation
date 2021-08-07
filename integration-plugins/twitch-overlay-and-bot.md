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

### 1. Access the Overlay

{% hint style="info" %}
It is recommended to configure and save your overlay layout in a regular web browser. This layout is saved on the account level and will be persisted to your OBS browser window.
{% endhint %}

While using the OBS browser, In the police, fire, or EMS page select the "Stream Overlay" button in the taskbar.  
This can be found under `System` &gt; `Stream Overlay` or by searching for it in the search bar.

### 2. Customize the Data and Font

The overlay has multiple window types. The `Unit & Call Data` window can display customizable unit and call data. The `Call Notes` window will display the live notes section of your attached call.

To add a window, select `New` &gt; {Window Type}

![Sonoran CAD Stream Overlay - Window Keys](../.gitbook/assets/image%20%28234%29.png)

{% hint style="warning" %}
The free version of the stream overlay is designed for trialing. This is limited to three \(3\) live data keys and one \(1\) Unit & Call Data window type. The Twitch bot is also unavailable with the free version.

[Learn more about the full version of Sonoran CAD's stream overlay.](twitch-overlay-and-bot.md#purchasing-the-overlay)
{% endhint %}

#### Data Keys

In the data window, you can add or remove rows to be displayed. Keys are marked as `{someKey}` and will be replaced with the live information.

| Key | Description |
| :--- | :--- |
| `{location}` | Unit Location |
| `{status}` | Unit Status |
| `{aop}` | Unit AOP |
| `{unitNum}` | Unit Number |
| `{name}` | Unit Name |
| `{district}` | Unit District |
| `{department}` | Unit Department |
| `{rank}` | Unit Rank |
| `{group}` | Unit Group Name |

| Key | Description |
| :--- | :--- |
| `{callId}` | Dispatch Call ID |
| `{origin}` | Dispatch Call Origin |
| `{callStatus}` | Dispatch Call Status |
| `{priority}` | Dispatch Call Priority |
| `{block}` | Dispatch Call Block |
| `{address}` | Dispatch Call Address |
| `{postal}` | Dispatch Call Postal |
| `{title}` | Dispatch Call Title |
| `{code}` | Dispatch Call 10-Code |
| `{description}` | Dispatch Call Description |

#### Font Customization

Select the `A` font icon to customize the row or window's text styling.

Here, you can change the font, color, size, weight, and alignment.

![Stream Overlay - Font Customization](../.gitbook/assets/image%20%28237%29.png)

### 3. Customize the Window

Each window can also have a customizable background. You can set the color with a HEX or RGB code.  
Or, use custom CSS for the `background` property.

Ex: `linear-gradient(0deg, rgba(228,0,54,1) 0%, rgba(149,0,228,1) 35%);`

![Stream Overlay - Custom CSS Background](../.gitbook/assets/image%20%28236%29.png)

### 5. Save your Layout

Make sure you SAVE your layout. This layout configuration is saved on the account level, and will persist to your stream layout loaded in OBS.

### 6. Adding the Overlay to OBS

[OBS Studio](https://obsproject.com/) is recommended for use of this overlay, but other stream casting software may also be used. The browser source type supports native transparency, and can even update in the background while minimized.

In OBS, add a new `Browser` source.

Set the URL to `https://sonorancad.com` and customize the `Width` and `Height` properties to your screen size.

![OBS - New Browser Source](../.gitbook/assets/image%20%28240%29.png)

![OBS - Browser Properties](../.gitbook/assets/image%20%28238%29.png)

### 7. Interact with the Browser Source

In OBS, right click on your new browser source to "interact" with it on the screen. By running the browser source through OBS, native transparency will be supported and processing can run in the background.

Then, login to Sonoran CAD as you normally would. Access the police, fire, or EMS page and enable the stream overlay mode.

![OBS - Browser Interaction](../.gitbook/assets/image%20%28233%29.png)

{% hint style="info" %}
Tip: In the OBS browser, be sure to set the community as your default in the community menu.  
  
Then, overlay will automatically resume when reloaded.
{% endhint %}

### 8. Start the Overlay

You can toggle on `Stream Mode` in the top toolbar. This will hide the toolbar on your stream.

Once a window is locked, the data will be displayed and update in real-time. You can now use Sonoran CAD on your regular web, desktop, or mobile app and watch the OBS browser window update.

To unlock a window, right-click and select `Unlock Window`.

## Configuring the Twitch Bot

Sonoran CAD's stream overlay also comes with a configurable Twitch bot. This bot will send out chat updates when unit or call data is updated.

{% hint style="warning" %}
The Twitch bot is not included with the free version of the Stream Overlay.  
  
[Learn more about the full version of Sonoran CAD's stream overlay.](twitch-overlay-and-bot.md#purchasing-the-overlay)
{% endhint %}

### 1. Create a Twitch OAuth Token

Create a new Twitch OAuth token by going to [https://twitchapps.com/tmi/](https://twitchapps.com/tmi/)

### 2. Configure your Twitch Bot Token and Username

Using the overlay in OBS, select the `Twitch Bot` button in the taskbar.  
Paste in your Twitch channel name and OAuth key.

![Overlay - Twitch Bot Credentials](../.gitbook/assets/image%20%28235%29.png)

### 3. Configure the Bot's Event Data

Every piece of unit and call data can be toggled on or off individually.

**It is highly recommended to only toggle on data updates that will not be frequently spammed.** Toggling too many data fields and updating data too quickly may result in **Twitch rate limiting your bot.**

![Overlay Twitch Bot - Configuration](../.gitbook/assets/image%20%28239%29.png)

### 4. Save and Run

Once you have configured your Twitch Bot's credentials and data fields, press `Save`.

Now, whenever one of those data fields is updated, your Twitch bot will send a chat message.

![Sonoran CAD - Stream Overlay](../.gitbook/assets/overlay.gif)

## Purchasing the Overlay

The free version of the livestream overlay allows anyone to test out the basic functionality. The free version does not allow use of the Twitch bot, and is locked to a single unit/call data window with a maximum of three "data keys".

The full version of Sonoran CAD's livestream overlay and Twitch bot is available for $7.99/mo.

Users can purchase a license to the full version in their billing center:

{% page-ref page="../pricing/faq/create-and-manage-a-subscription.md" %}

