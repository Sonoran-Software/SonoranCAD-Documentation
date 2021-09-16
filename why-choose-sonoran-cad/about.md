---
description: >-
  Sonoran CAD is the most advanced, in-depth, and customizable CAD/MDT software
  available to gaming communities. Check out some of our latest features below!
---

# 🏆 Why Choose Sonoran CAD?

![](../.gitbook/assets/layout_3_11.gif)

### 📱 Downloadable Apps

In addition to our web version, you can download Sonoran CAD on the [iOS App Store](https://apps.apple.com/us/app/sonoran-cad/id1496539456), the [Google Play Store](https://play.google.com/store/apps/details?id=sonorancadmdt.app&hl=en_US), or for [Windows Desktop](https://github.com/Sonoran-Software/SonoranCAD_Windows/releases/latest/download/Sonoran-CAD.exe).  
  
It's never been more easy to access your community's CAD system, regardless of what platform you're on!

### 💾 Database Sync

Tired of having to manually register civilians? With Sonoran CAD's [Database Sync](../integration-plugins/database-sync-and-merge/), all of your in-game characters, licenses, and vehicle registrations are automatically in your CAD!

### 🎮 In-Game Integration Plugins

Sonoran CAD's integration framework includes **over a dozen drag-and-drop plugins** for your game server!

* [Automated Plate Reader Lookup \(Results Sent Back to CAD\)](../integration-plugins/integration-plugins/available-plugins/wraithv2.md)
* [Automated Traffic Stop Dispatching](../integration-plugins/integration-plugins/available-plugins/traffic-stop.md)
* [Live Unit Locations](../integration-plugins/integration-plugins/available-plugins/locations.md)
* [/911, /511, /311 and /Panic](../integration-plugins/integration-plugins/available-plugins/call-commands.md)
* [Custom Integrated Live Map](../integration-plugins/integration-plugins/available-plugins/live-map/)
* [TeamSpeak 3 Integration](../integration-plugins/integration-plugins/available-plugins/teamspeak-3.md)
* [Automated GPS Routing for Dispatch Calls and Live Pursuit GPS Tracking](../integration-plugins/integration-plugins/available-plugins/dispatch-notify.md)
* And much more!

**View a** [**showcase video on our WraithV2 plugin here**](https://www.youtube.com/watch?v=5oL7Mg6LQgg)**!**

![Sonoran CAD&apos;s custom plugin framework and installation system!](../.gitbook/assets/image%20%2849%29.png)

### 💬 Discord Permission Integration <a id="discord-permission-integration"></a>

Our official [Discord bot](https://app.gitbook.com/@sonoran/s/sonoran-software/~/drafts/-Maqgxy_VS4uxPXm0a98/integration-plugins/discord-bot) automatically **syncs Discord roles with CAD account permissions**. This allows you to easily grant and remove permissions from a user's CAD account all through Discord!‌

​[Discord webhooks](https://app.gitbook.com/@sonoran/s/sonoran-software/~/drafts/-Maqgxy_VS4uxPXm0a98/integration-plugins/discord-webhooks) instantly notify your community when changes are made, calls are placed, units toggle their panic status, and more! You can even [react to webhooks](../integration-plugins/discord-bot/features/webhook-actions.md) like dispatch events to attach your unit, or react to record webhooks to view the full record in the CAD.

### 🌎 Full Translation and Locality Support

Only Sonoran CAD supports full [i18n localization](../sonoran-cad/translation-support.md). Regardless of your community's native language, Sonoran CAD supports it!  
  
Sonoran CAD is currently fully translated in Chinese, Russian, Spanish, Polish, Italian, German, Arabic, and more! Anyone is allowed to [contribute to our GitHub translation files](../sonoran-cad/translation-support.md).

Sonoran CAD also offers vast [geographical location](../tutorials/customization/geographical-settings.md) support for non-American communities.

### 📍 Hosted and Integrated Live Map

Sonoran CAD's custom[ live map plugin](../integration-plugins/integration-plugins/available-plugins/live-map/) even shows your unit identifier information in real time and displays 911 call blips! We even take care of hosting the live map for you!

![Sonoran CAD&apos;s custom live map!](../.gitbook/assets/live_map.png)

### [🛑](https://emojipedia.org/stop-sign/) Smart Signs Integration

![Sonoran CAD x London Studios](../.gitbook/assets/image%20%28217%29.png)

We've partnered up with London Studios to integrate their Smart Signs plugin directly with Sonoran CAD! You can customize in-game roadway signs right from Sonoran CAD!

[Learn more about this free script included with Sonoran CAD Pro!](../integration-plugins/integration-plugins/available-plugins/smart-signs.md)

[View our showcase video on Smart Signs!](https://www.youtube.com/watch?v=ihfVSiB8oB8)

### [💻](https://emojipedia.org/laptop/) In-Game Mini CAD

Easily view and attach to calls, talk to other officers, and more all from the [in-game mini CAD](../integration-plugins/integration-plugins/available-plugins/tablet.md)!

![](../.gitbook/assets/image%20%28269%29.png)

### 📺 Twitch Bot and Overlay

![](../.gitbook/assets/live-banner.png)

![Sonoran CAD - Livestream Overlay](../.gitbook/assets/overlay%20%282%29.gif)

Sonoran CAD also offers a [customizable stream overlay and Twitch bot](../integration-plugins/twitch-overlay-and-bot.md) to display your unit and attached call information in real time!

### 💻 Multitasking Window and Tab System

Only Sonoran CAD lets you easily multitask and open multiple search windows, records, penal codes references, ten code lists, and more! Our workflow allows you to handle even the most complicated and demanding patrols.

[Every panel and window can be locked into position and customized.](../tutorials/customization/customizing-your-layout.md)

Drag-and-drop allows you to easily view calls, attach units, and more!

![Sonoran CAD - Custom Layouts](../.gitbook/assets/3_10_features%20%281%29.gif)

### 🎤 [TeamSpeak 3 Integration](../integration-plugins/integration-plugins/available-plugins/teamspeak-3.md)

Enforce security in your TeamSpeak 3 channels by requiring them to be signed into the CAD. Additionally, kick users from secured TS channels when they log off.

### 🔢 [Stream Deck Integration](../integration-plugins/stream-deck-integration.md)

Check out our official [Stream Deck profiles](../integration-plugins/stream-deck-integration.md) to change your unit status, panic, open a lookup, and more from a physical button. Along with the [Sonoran CAD desktop application](../downloads/), these actions can be done even while the app is minimized.

![Sonoran CAD - Stream Deck Profile](../.gitbook/assets/image%20%28176%29%20%281%29.png)

### 📖 API Integration

In addition to over a dozen drag-and-drop integration [plugins](../integration-plugins/integration-plugins/), you can write your own integration plugins using our [API documentation](../sonoran-cad/api-integration/).

We've complied extensive documentation for over two-dozen API endpoints and server [push events](../sonoran-cad/api-integration/push-events/)!

```javascript
{
    "id": "YOUR_COMMUNITY_ID",
    "key": "YOUR_API_KEY",
    "type": "ATTACH_UNIT",
    "data": [
        {
            "serverId": 1, // Default 1 - See guide on setting up multiple servers
            "callId": 100, // Can be retrieved from the GET_CALLS API endpoint
            "units": ["STEAN:1234"] // Array of API IDs
                                // Typically, this is their STEAM Hex
        },
    ]
}
```

### 📝 Custom Records and Reports

Create your very own [custom report and record formats](../tutorials/customization/creating-custom-record-and-report-types.md) for your community to use!

Whether it's your own firearms registration system, an in-depth vehicle accident report format, or a custom incident record, Sonoran CAD allows you to customize it all.

You can even index specific record fields for [custom search types](../tutorials/customization/custom-search-types.md). Allowing you to run a lookup on your record's custom ID numbers, phone numbers, and more!

![Create custom record and report formats!](../.gitbook/assets/image%20%2844%29.png)

### 📧 Custom Branding

Sonoran CAD enables you to place your community's name and [branding](../tutorials/customization/community-branding-and-info.md) in the CAD, [customize user account emails](../tutorials/customization/custom-emails.md), host a [custom login page](../tutorials/customization/custom-login-page.md) on **your own domain**, and more!

![Sonoran CAD&apos;s custom email branding!](../.gitbook/assets/image%20%2847%29.png)

### 🧍 Self-Dispatch

Don't have a dedicated dispatcher for your community?  
Sonoran CAD allows your units to easily [self-dispatch](../tutorials/dispatching/self-dispatch.md), attach to calls, preview other open calls, and more!

### 🖨️ PDF Records

Looking to store official criminal records or prior call logs in a PDF format? Sonoran CAD allows you to easily view and [print records to PDF](../tutorials/records-management/pdf-records.md).

![Sonoran CAD&apos;s print to PDF system!](../.gitbook/assets/image%20%2845%29.png)

### 🏠 Auto Suggested Street Names and Addresses

Sonoran CAD allows you to upload a [custom spreadsheet with your game's street names and addresses](../tutorials/customization/addresses-and-street-names.md). Dispatchers in the call editor can quickly and easily search and filter these names automatically.

![](../.gitbook/assets/addresses.gif)

### ⌨️ Global Hotkeys

Only Sonoran CAD allows you to configure customizable [hotkeys](../tutorials/other-features/configurable-hotkeys.md) for quick actions in the CAD. With our [Desktop application](../downloads/), hotkeys are even registered globally and do not require the application to be visible or in-focus to trigger commands.

![Sonoran CAD&apos;s global hotkey configuration!](../.gitbook/assets/image%20%2846%29.png)

### 📦 Easy Migration

Sonoran CAD allows you to easily migrate your [10-codes ](../tutorials/customization/10-codes.md#import-10-codes-from-a-spreadsheet-csv)and [penal codes](../tutorials/customization/penal-codes.md#import-from-spreadsheet-csv) by importing directly from a spreadsheet \(CSV\) or JSON file. Fully [customizable record formats/templates](../tutorials/customization/sharing-custom-records.md) can also be exported and shared between communities.

### 🎤 Voice Commands

Common tasks are made even easier with our [voice commands](../tutorials/other-features/voice-commands.md). Sonoran CAD allows you to easily lookup a civilian's name, a vehicle license plate, or trigger a panic tone completely hands free!

### 📋 Frequent Updates

As shown in our [changelog](../roadmap/changelog.md), new features, fixes, and suggestions are added all the time!

