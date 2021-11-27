---
description: Learn more about our Roblox integration with ER:LC!
---

# Roblox ER:LC

![Sonoran CAD x ER:LC](<../.gitbook/assets/image (292).png>)

{% hint style="danger" %}
This integration has **not yet been released by ER:LC** and is expected to be released on **10/28/2021**.
{% endhint %}

## What is ER:LC?

Emergency Response Liberty County is the largest Roblox RP game mode. Play as a Civilian, criminal, transportation worker, police officer, sheriff deputy, or firefighter!

We're excited to support the following in-game integration options with ER:LC

* Live unit locations
* Traffic stop command
* In-game plate search
* In-game name search
* Panic command
* Automated emergency calls for fires and robberies
* In-game 911 calls sent to Sonoran CAD
* and more!

## Getting Started

### For Server Owners

{% hint style="warning" %}
ER:LC's Sonoran CAD integration can only be setup by the **server owner** on a **private server**.
{% endhint %}

#### 1. Retrieve your Community ID and API Key

In Sonoran CAD, navigate to the admin menu > `Advanced` > `In-Game Integration` > `Web API`

Copy your community ID and API key, you'll need to enter these in Roblox.

![Sonoran CAD: In-Game Integration](<../.gitbook/assets/image (303).png>)

![Sonoran CAD: Community ID and API Key](<../.gitbook/assets/image (301).png>)

#### 2. Access the Server Owner Menu

Once you've joined your private server as the owner, click the menu on the top right of your screen.

![ER:LC Server Owner Menu](<../.gitbook/assets/image (294).png>)

#### 3. Edit the Server Settings

Select `Edit Server Settings` in the menu.

![ER:LC Edit Server Settings](<../.gitbook/assets/image (291).png>)

#### 4. Enter your Community ID and API Key

Select `Edit` and paste in your Sonoran CAD community ID and API key.

![](<../.gitbook/assets/image (296).png>)

![](<../.gitbook/assets/image (295).png>)

### For Community Members

#### 1. Access the Local Settings Menu

At the top right of your screen, select the gear icon to open your local settings menu.

![ER:LC - Local Settings Button](<../.gitbook/assets/image (300).png>)

#### 2. Copy your API ID

Then, select `View Your API ID` and copy your in-game API ID.

![ER:LC - View your API ID](<../.gitbook/assets/image (298).png>)

![ER:LC - Copy your API ID](<../.gitbook/assets/image (299).png>)

#### 3. Add Your API ID to Sonoran CAD

From the community menu select the `Settings` modal.

Select `New` under API ID and paste in your Roblox API ID.

![Sonoran CAD Settings](<../.gitbook/assets/image (290).png>)

![Sonoran CAD: New API ID](<../.gitbook/assets/image (293).png>)

## In-Game Commands and Features

### Unit Locations

Once you have [added your Roblox API ID](roblox-er-lc.md#for-community-members) to the CAD, your unit location in-game will be updated as you move around the map.

![Sonoran CAD - Unit Locations](<../.gitbook/assets/Screen Shot 2021-11-27 at 10.17.54 AM.png>)

### Plate Search

| Command                | Description        |
| ---------------------- | ------------------ |
| `/ps <plate>`          | Run a plate search |
| `/platesearch <plate>` | Run a plate search |

Ex: `/ps abc1234`

Once you have [added your Roblox API ID](roblox-er-lc.md#for-community-members) to the CAD, running a pate search in-game will automatically pop up the results on your CAD screen.

![Sonoran CAD: Plate Search](<../.gitbook/assets/Screen Shot 2021-11-27 at 10.24.49 AM.png>)

### Name Search

| Command              |                   |
| -------------------- | ----------------- |
| `/ns <name>`         | Run a name lookup |
| `/namesearch <name>` | Run a name lookup |

Ex: `/ns Brian Sauce`

Once you have [added your Roblox API ID](roblox-er-lc.md#for-community-members) to the CAD,  running a name search in-game will automatically pop up the results on your CAD screen.

![Sonoran CAD: Name Search](<../.gitbook/assets/Screen Shot 2021-11-27 at 10.25.04 AM.png>)

### Traffic Stop

| Command               | Description                                          |
| --------------------- | ---------------------------------------------------- |
| `/ts <info>`          | Creates and attaches you to a traffic stop dispatch  |
| `/trafficstop <info>` | Creates and attaches you to a traffic stop dispatch  |

Ex: `/ts Red Tahoe, ABC123`

Once you have [added your Roblox API ID](roblox-er-lc.md#for-community-members) to the CAD, running the traffic stop command will automatically create and attach you to a new dispatch call with your information.

Note: Don't include your location in the traffic stop info, the command will automatically add this to the call.

![Sonoran CAD: Traffic Stop Dispatch](<../.gitbook/assets/Screen Shot 2021-11-27 at 10.36.11 AM.png>)

### 911 Calls

| Command           | Description                                 |
| ----------------- | ------------------------------------------- |
| `/setname <name>` | Sets a roleplay name used when calling 911. |

#### From the Cell Phone

Using your cell phone in-game, you can call emergency services. This 911 call will be sent directly to Sonoran CAD.

#### Automated Alarms

Automated alarms from fire alarms or bank robberies will also be automatically sent to the CAD's emergency call section.

### Panic

| Command  | Description                      |
| -------- | -------------------------------- |
| `/panic` | Toggles your unit's panic status |

Additionally, you can also use the desktop application's [panic hotkey](../tutorials/other-features/configurable-hotkeys.md).
