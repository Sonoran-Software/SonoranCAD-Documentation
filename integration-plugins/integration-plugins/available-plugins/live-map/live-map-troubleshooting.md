---
description: This guide covers the basic troubleshooting of the live map plugin.
---

# Live Map Troubleshooting

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../../vps-hosting-1/vps-hosting.md)!  
Sonoran Servers customers receive **free plugin installation** and **30% off** their monthly CAD subscription!
{% endhint %}

![Sonoran Servers - Discount and Free Plugin Installation](../../../../.gitbook/assets/banner_3.png)

## When are Player Blips Displayed?

Players will only show on the map when **ALL** of the following conditions are met:

1. The player has their [API ID set in the CAD](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).
2. The player actively is logged into the police, fire, or EMS page.
3. The player has the [correct server selected in the CAD](../../../../tutorials/customization/configuring-multiple-servers.md), on the top right of the page.
4. The player is actively logged into the server.
5. The player has Steam, Discord, or other identifier type program running:
   * If the server API IDs are based on the Steam HEX, **the player must have Steam running**.
   * If the server API IDs are based on Discord IDs, **the player must have Discord running**.

## ERROR: Couldn't start resource sonoran\_livemap

![Error message without starting webpack](../../../../.gitbook/assets/image%20%2850%29.png)

Particularly with **Linux**, some users have an additional installation step,[ per the installation guide](./).

First, run `start webpack` in your server console _before_ running `start sonoran_livemap` in order to build it for the first time. You can `stop webpack` after it has been built.‌

You will have to do this step whenever the `sonoran_livemap` resource is updated.

## 1. Check your Subscription Version

Your community's subscription may have expired and failed to renew. Do a quick check on your [community limits](../../../../tutorials/getting-started/view-your-limits.md) to make sure your community version is on the **Plus** version or higher.

## 2. Search the Resource Manifest

Navigate to `mapIp:gamePort/info.json` in your web browser:

_Your game port is typically `30120` by default, but could be different for others._

![View your resource manifest for active plugins](../../../../.gitbook/assets/screen-shot-2020-06-20-at-12.22.58-pm.png)

You can search \(control/command + f\) for the keyword "map".

1. Ensure the `sonoran_livemap` resource listed and running. If not, follow the [installation guide](./) and check your server console for errors on startup once `ensure sonoran_livemap` is in your `server.cfg` file.
2. Ensure you do **NOT** have `live_map` listed. This is the default/original live map resource from Havoc and will cause resource conflicting issues.
3. If `live_map` is listed and running, stop it, remove it, and restart the server.

## 3. Check Ports

The live map requires one additional port that are not used by any other service or resource.

If you are using/forwarding ports other than the default `30121` \(map port\) and `30120` \(listener/game server port\) you will need to update the convars and admin panel per the [installation tutorial](./).

### 3A. Check IP and Ports for Common Mistakes

Ensure the IP and ports are listed correctly without spaces, common mistypes, possible incorrect port numbers, etc.

![Ensure your map IP, map port, and game port are set correctly](../../../../.gitbook/assets/livemap_config.png)

### 3B. Ensure the Map Port is Open

Navigate to `mapIp:mapPort/blips.json` in a web browser:  
You should see brackets **with or without additional blip data**.

![View your blips.json file](../../../../.gitbook/assets/screen-shot-2020-06-20-at-12.10.28-pm.png)

If you do **not** see the brackets \(with or without additional data\), the issue may be caused by one of the following:

1. The `sonoran_livemap` [resource ](./#4-configuration)is not running on your server.
2. The live map port `30121` \(by default\) is used by another service.
3. Your live map port is not open.
   * If you are unsure how to open the live map port, you will need to **contact your hosting provider**.
   * You can use a [port checker](https://www.yougetsignal.com/tools/open-ports/) to ensure you have properly opened this port.
4. You are using a [different port than the default](./#using-different-ports) and did not configure that in your `server.cfg`. 

### 3C. Ensure the Listener Port is Open

Navigate to `mapIp:gamePort/sonorancad/event` in your web browser, you should see the following page. This means that you have properly configured your push events listener page:

![Event Listener: Web Browser View](../../../../.gitbook/assets/image%20%28161%29.png)

If the page is not displayed, the issue may be caused by one of the following:

1. The port number is not correct.
2. You do not have the port open.
   * If you are unsure how to open the live map port, you will need to **contact your hosting provider**.
   * You can use a [port checker](https://www.yougetsignal.com/tools/open-ports/) to ensure you have properly opened this port.
3. You are using a [different port than the default](./#using-different-ports) and did not configure that in your `server.cfg`.

## 4. Ensure Your API ID is Set

Once the map is properly connected, only online players both in-game and in the CAD \(police, fire, or EMS page\) with their [API ID set](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) will show on the map.

Ensure that your users have their API ID set in the CAD. This is generally their steam hex value. The [API ID plugin](../api-id-checker.md) will help them get the correct ID.

## 5. Enable Debug Mode

### 5A. Toggle Debug Mode ON

The plugin framework includes a powerful debug mode. Enable this by entering `sonoran debugmode` into your server console.

Debug mode will print out additional error information and JSON data for all API calls or push events.

**Check for any error messages printed out in the console.**

### 5B. Check for Push Events:

The image below shows a push event being sent from Sonoran CAD to your server. This data is shown in your server console when `sonoran debugmode` mode is toggled ON.

Push events are sent to your server when a unit signs into the CAD \(on the police, fire, or EMS page\), or when your unit status is updated. This data tells the live map to add or remove a unit, and change the blip information.

You should see push events being received with the types `EVENT_UNIT_LOGIN`, `EVENT_UNIT_LOGOUT`, and `EVENT_UNIT_STATUS` when those actions are performed in the CAD.

| Event | Description |
| :--- | :--- |
| EVENT\_UNIT\_LOGIN | When you login to the police, fire, or EMS page. |
| EVENT\_UNIT\_LOGOUT | When you exit the police, fire, or EMS page. |
| EVENT\_UNIT\_STATUS | When your unit status is updated. |

Ensure the `APIID` listed in the push event data matches the [API ID set in your CAD's user account](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).

If the `APIID` listed is different, [update your API ID set in your CAD's user account](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) to the one displayed in debug mode. **These IDs must match up exactly**.

![](../../../../.gitbook/assets/image%20%2827%29.png)

If you do not see the  `EVENT_UNIT_LOGIN`, `EVENT_UNIT_LOGOUT`, or`EVENT_UNIT_STATUS` push events displayed in debug mode when you perform these actions in the CAD, **double check that your push events listener is correctly setup in step 3C**.

## 6. Clear Local Browser or Desktop Cache

When re-deploying the live map with new configurations, your local web browser may be caching an older version of the config.

In Chrome, you can hold `shift` and click `refresh` at the same time on the live map page to [clear your browser's cache](../../../../downloads/web-browser-clear-cache.md).

For more information on clearing your Desktop application's cache, click [here](../../../../downloads/desktop-app-clear-cache.md).

