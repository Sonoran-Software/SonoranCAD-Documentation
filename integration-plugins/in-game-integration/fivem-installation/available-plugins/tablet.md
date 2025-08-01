---
description: >-
  Automatically set user's API IDs in the CAD on a login, and view your CAD
  in-game with our easy to use tablet resource! Use the Mini-CAD to view current
  calls, and easily attach to and view them.
---

# Tablet & Mini-CAD

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](broken-reference)!
{% endhint %}

<figure><img src="../../../../.gitbook/assets/mini_cad.png" alt=""><figcaption><p>Sonoran CAD - Mini-CAD</p></figcaption></figure>

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.\
This resource is included in the base framework.

### 2. Start the Resource

In your `server.cfg` file add the following new line:\
`ensure tablet`

### 3. Set URL Convar (Optional)

If you wish to use a custom login page, you can set a convar in your server.cfg.\
\
The easiest way to show your [custom login page](../../../../tutorials/customization/custom-login-page.md) is to use a query string.

`"https://sonorancad.com/?comid=YOUR_COMMUNITY_ID_HERE"`

Simply replace `YOUR_COMMUNITY_ID_HERE` in the URL with your [community ID](../../../../tutorials/getting-started/finding-your-community-id-and-authentication-code.md).\
EX: `https://app.sonorancad.com/?comid=midwestrp`

Add the following to your server.cfg **before** starting the tablet resource:

```
setr sonorantablet_cadUrl "YOUR_URL_HERE"
```

Fill in with your actual URL above with the comid you want.

### 4. Using the Tablet

* Use the `/showcad` command in-game to toggle your tablet. You can also add a custom keybind to open the tablet by going to `GTA Settings` > `Keybinds` > `FiveM`
* Use the `/cadsize <width> <height>` command to resize the tablet to best fit your screen. This size persists on reload of the client.
* Use the `/cadrefresh` command to refresh the tablet if it's not loading properly.

### 5. Using the Mini-CAD

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **Plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

* Use the `/minicad` command in-game to display your Mini-CAD. You must be logged into the Police or Fire CAD, and need to have your [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) set.
* While open, use `/showcad` to focus the minicad and allow the elements to be clickable, such as the Attach button.
* You can close or move the Mini-CAD by opening the tablet, and interacting with the Mini-CAD window.
* (Experimental) Use the `/minicadsize <width> <height>` command to resize the Mini-CAD to best fit your screen. This size persists on reload of the client.
* Use the `/minicadrefresh` command to refresh the Mini-CAD if it's not loading properly.
* Controls
  * Use the `Left Arrow Key` to display the previous call.
  * Use the `Right Arrow Key` to display the next call.
  * Use the `K` key to attach or detach to/from the displayed call.
  * Use the `L` key to toggle display of the call details.
  * **All these commands can be edited from the Keybinds menu.**

### 6. Auto API ID

When a user signs into the CAD using the in-game tablet, their[ API ID](../../../../api-integration/getting-started/setting-your-api-id.md) can be automatically be set in the CAD.

To enable this, open the submodule [Check API Id's](api-id-checker.md) config and set `forceSetApiId` to `true`.

Additionally, communities using Steam as their framework's `primaryIdentifier` **will need to ensure they have a** [**Steam key set**](../#id-5.-steam-api-key) **for their server**.

## Known Issues

### Tablet SSO Sign In via Discord/Apple

The in-game tablet utilizes an iFrame. Because Apple and Discord have disabled their oauth pages from being viewed inside of an iFrame, users will be unable to use these sign in methods from in-game.

#### 1. Utilize the official Desktop App Overlay system

{% content-ref url="../../../../download/steam-browser-workaround.md" %}
[steam-browser-workaround.md](../../../../download/steam-browser-workaround.md)
{% endcontent-ref %}

#### 2. Link your Discord/Apple created account to a Sonoran login email/password.

Because your account was created using Discord/Apple, your email does not yet have a password set to login via Sonoran.

1. Navigate to the [account website](https://account.sonoransoftware.com) -> Recover Password
2. Enter in the email address of the Discord/Apple account
3. Check your email for a link to setting your new password
4. Sign-in on the Tablet using the Sonoran sign-in method (Discord can still be used elsewhere)

If you are having an issue using the Sonoran sign-ing method please see [below](tablet.md#tablet-showing-grey).

### Timeout SonoranCAD::mini:CallSync

Some users may see `SonoranCAD::mini:CallSync` listed multiple times after recieving a timeout.

When your client recieves a timeout from the server for any reason, it will display a list of the most recent requests. Because Sonoran's Mini-CAD runs frequent sync requests, these will consequenty be displayed.

**This is not an issue with or related to Sonoran CAD**. This is a general timeout between the client and server listing all recent calls as diagnostic information.

![Sonoran CAD Mini - Timeout Debug](<../../../../.gitbook/assets/Screen Shot 2022-01-06 at 9.28.58 PM.png>)

### Tablet Showing Grey

Some users may get a grey, black or blank screen when using the Sonoran Login method before and then opening the tablet and it just being a grey screen.

To resolve this, close FiveM, then to go to your `FiveM Application Data` folder then to `data` and then delete the `nui-storage` folder.

If you still are having issues reach out to our [support team](https://support.sonoransoftware.com).

![Sonoran CAD Tablet - Blank Screen Issue](<../../../../.gitbook/assets/Tablet Blank Error.png>)
