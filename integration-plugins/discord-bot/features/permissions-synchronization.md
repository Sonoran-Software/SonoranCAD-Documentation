---
description: Sync your Discord roles with SonoranCAD permissions!
---

# Permissions Synchronization

{% hint style="warning" %}
This feature requires the **Plus** version of SonoranCAD to function. 

For more information, see our [pricing](../../../pricing/faq/) or view how to check your community [limits](../../../tutorials/getting-started/view-your-limits.md).
{% endhint %}

## Getting Started

{% hint style="warning" %}
You must be an **Administrator** on the Discord server in order to set up this process.
{% endhint %}

The bot provides a few "slash" commands to set up the roles sync process.

To assist you, use this [Permission Mask Calculator](https://sonoran-software.github.io/sonoranbot-perms/) to calculate the proper code to send with the `/maprole` command below.

| Command | Description |
| :--- | :--- |
| /maprole &lt;role&gt; &lt;permission mask&gt; | Maps a role to a particular permission mask. |
| /unmaprole &lt;role&gt; | Removes the permissions sync with the specified role. |
| /syncroles | Forces a server-wide recalculation of all permissions. This can take some time depending on the size of your server. |

### User Setup

In order for permissions to synchronize properly, **every** player will need to [add their Discord ID as an API ID](../../../sonoran-cad/api-integration/getting-started/setting-your-api-id.md) on their account. Users can use the command `/myid` to get their Discord ID. They can then use `/syncme` to force a permissions sync.

Now, whenever a role is added or removed, the bot will automatically update the user's permissions to match! If the user ever leaves the server, the bot will immediately remove all permissions from their account, although they will still be in the community.

### Best Practices and FAQ

* It is advised to not sync potentially dangerous permissions \(such as Admin Access permissions\) with Discord roles **unless** you trust staff with that role, or it's just you.
* The community owner is completely ignored during the synchronization process.
* "Principle of Least Privilege" should be exercised during this setup. Don't give out permissions you don't think users performing the role won't need.
* Discontinue use of permission keys ASAP. The bot "takes over" synchronization and will remove permissions granted by permission keys if they don't have a role that grants it.
  * Same goes for manual permission grants, **unless there is no role granting that permission**.



