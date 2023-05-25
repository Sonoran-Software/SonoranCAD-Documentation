---
description: >-
  The TeamSpeak 3 integration plugin requires that users must be logged into the
  CAD police, fire, EMS, or Dispatch page in order to access specific voice
  channels.
---

# TeamSpeak 3

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **plus** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../../other-products/server-hosting.md)!
{% endhint %}

## Installation Guide

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and all Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran\_ts3integration/releases/tag/latest)to download the TS3 integration plugin .zip file.

### 3. Install the Plugin and all Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation/) for the TeamSpeak3 plugin.

### 4. Configure your TeamSpeak Connection

In the `config_ts3integration.json` file, enter in the following:

|                     |                                                                                                                                                                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ts3server\_host     | TS3 Public Server IP                                                                                                                                                                                                                                |
| ts3server\_port     | <p>Public connection port</p><p>Default is <code>9987</code></p>                                                                                                                                                                                    |
| ts3server\_qport    | <p>Sever Query Port</p><p>Default is <code>10011</code></p>                                                                                                                                                                                         |
| ts3server\_user     | <p>Typically, this will be your server admin username.</p><p>If you do not have one, you <a href="https://www.teamspeak3.com/support/teamspeak-3-add-server-query-user.php">can create a new one</a>.</p>                                           |
| ts3server\_pass     | <p>Typically, this will be your server admin password.</p><p>If you do not have one, you <a href="https://www.teamspeak3.com/support/teamspeak-3-add-server-query-user.php">can create a new one</a>.</p>                                           |
| onduty\_servergroup | <p>Name of the server group that the plugin will grant users when they're on duty.</p><p>You will need to configure this server group with permissions to join specific channels, etc.</p>                                                          |
| enforced\_channels  | A list of channels that units will be kicked from if they log out of the CAD                                                                                                                                                                        |
| logoutGraceTime     | <p>The amount of time between the user logging out of the CAD and being kicked from the TS3 <code>enforced_channels</code>.</p><p>This prevents brief internet disconnections from the CAD from continually kicking users out of their channel.</p> |

![TS3 - Integration Config](<../../../.gitbook/assets/image (353).png>)

### 5. Retrieve Your Individual TS3 ID

Every member from your community will need to retrieve their unique TS3 ID.\
This is found in TS under Tools > Identities > Default > Unique ID

![TS3 - Retrieve your unique ID](<../../../.gitbook/assets/image (310).png>)

### 6. Add your TS3 ID as an API ID

Paste in this TS3 unique ID as a [new API ID in the CAD](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md).

{% hint style="warning" %}
Every member of your community will need to add their unique ID to their CAD account in your community.
{% endhint %}

![API ID - Paste New ID](<../../../.gitbook/assets/image (372).png>)

### 7. Utilize the TS3 Integration

Once configured, when the user joins the TS3 server they will be granted the `onduty_servergroup` once they sign into the police, fire, EMS, or dispatch page.

Signing out of or exiting the CAD will result in the user being kicked from any of the `enforced_channels` from the config.

![TS3 - Server Group Granted](<../../../.gitbook/assets/image (341).png>)

![TS3 - Channel Kicked](<../../../.gitbook/assets/image (164) (2).png>)
