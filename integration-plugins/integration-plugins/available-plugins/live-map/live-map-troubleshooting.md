---
description: This guide covers the basic troubleshooting of the live map plugin.
---

# Live Map Troubleshooting

## 1. Search the Resource Manifest

Navigate to mapIp:30120/info.json in your web browser:

![View your resource manifest for active plugins](../../../../.gitbook/assets/screen-shot-2020-06-20-at-12.22.58-pm.png)

You can search \(control/command + f\) for the keyword "map".

1. Ensure the "sonoran\_livemap" resource listed and running.
2. Ensure you do **NOT** have "live\_map" listed. This is the default/original live map resource from Havoc and will conflict.
3. If "live\_map" is listed and running, stop it, remove it, and restart the server.

## 2. Check Ports

The live map requires two, separate, open ports that are not used by any other service or resource.

If you are using/forwarding ports other than the default `30121` \(map port\) and `3232` \(listener port\) you will need to update the convars and admin panel per the [installation tutorial](./).

### 2A. Check IP and Ports for Common Mistakes

Ensure the IP and ports are listed correctly without spaces, common mistypes, possible incorrect port numbers, etc.

![Ensure your map IP, map port, and listener port are set correctly](../../../../.gitbook/assets/livemap_config.png)

### 2B. Ensure the Map Port is Open

Navigate to mapIp:mapPort/blips.json in a web browser:  
You should see brackets with our without blip data.

![View your blips.json file](../../../../.gitbook/assets/screen-shot-2020-06-20-at-12.10.28-pm.png)

If you do not see the brackets, the issue may be caused by one of the following:

1. The live map resource is not running on your server.
2. The live map port `30121` \(by default\) is used by another service.
3. Your live map port is now open.
   * If you are unsure how to open the live map port, you will need to contact your hosting provider. 

### 2C. Ensure the Listener Port is Open

Navigate to mapIp:listenerPort in your web browser, you should see the following page.

![Access your event listener](../../../../.gitbook/assets/screen-shot-2020-06-20-at-12.16.12-pm%20%281%29.png)

If the page is not displayed, the issue may be caused by one of the following:

1.  You do not have the live map resource running.
2. The port numbers are not set correctly.
3. You do not have the ports open.
   * If you are unsure how to open the live map port, you will need to contact your hosting provider.

## 3. Ensure Your API ID is Set

Once the map is properly connected, only online players both in-game and in the CAD \(police, fire, or EMS page\) with their [API ID set](../../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) will show on the map.

Ensure that your users have their API ID set in the CAD. This is generally their steam hex value. The [API ID plugin](../api-id-checker.md) will help them get the correct ID.

