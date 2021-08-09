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

<table>
  <thead>
    <tr>
      <th style="text-align:left">Command</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">/maprole &lt;role&gt; &lt;type&gt; &lt;value&gt;</td>
      <td style="text-align:left">
        <p>Maps a role to a particular permission key or mask, depending on the &quot;type&quot;
          selected:</p>
        <p></p>
        <p>Permission Key - A permission key for your community</p>
        <p>Permission Code - A permission mask</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">/unmaprole &lt;role&gt;</td>
      <td style="text-align:left">Removes the permissions sync with the specified role.</td>
    </tr>
    <tr>
      <td style="text-align:left">/syncroles</td>
      <td style="text-align:left">Forces a server-wide recalculation of all permissions. This can take some
        time depending on the size of your server.</td>
    </tr>
    <tr>
      <td style="text-align:left">/myid</td>
      <td style="text-align:left">Gets your Discord ID.</td>
    </tr>
    <tr>
      <td style="text-align:left">/syncme</td>
      <td style="text-align:left">Forces the bot to sync your permissions. You should only need to use this
        after initially setting your API ID in SonoranCAD.</td>
    </tr>
    <tr>
      <td style="text-align:left">/linkme &lt;secret ID&gt;</td>
      <td style="text-align:left">Using the Secret ID, link your current discord account to SonoranCAD. <b>Primary Server Only</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">/changesecret &lt;new secret&gt;</td>
      <td style="text-align:left">Update the Secret Key mapping your Discord to SonoranCAD. <b>Primary Server Only</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">/caduser</td>
      <td style="text-align:left">Checks if you have correctly linked your Discord account to SonoranCAD.</td>
    </tr>
  </tbody>
</table>

### User Setup

1. Every user in the Discord will get their[ Secret ID from their Settings page](../../../sonoran-cad/api-integration/getting-started/account-secret-id.md).
2. Every user in the Discord will then use `/linkme <secretid>` to link their SonoranCAD account to their current Discord account. This will automatically populate their API ID.
3. Community members can use the `/syncme` command in Discord to force a permissions sync.
4. Communities should **no longer use public permission keys in the CAD**, as the bot will automatically remove CAD permissions from users if they don't have a Discord role for it.

Now, whenever a role is added or removed, the bot will automatically update the user's permissions to match! If the user ever leaves the server, the bot will immediately remove all permissions from their account, although they will still be in the community.

### Changing your Account Secret ID

Sometimes, you may wish to change your secret ID. If you do so from the [Settings page](../../../sonoran-cad/api-integration/getting-started/account-secret-id.md), you must use the `/changesecret <new key>` command or the bot will remove all your permissions on SonoranCAD \(if the optional security setting below is enabled\).

### Optional Security Setting

By default, the bot will not remove permissions from users who do not have a matching secret key to their Discord ID. This can be enabled by setting `stripUnmappedUsers` to true with the `s!setting` command.

### Best Practices and FAQ

* It is advised to not sync potentially dangerous permissions \(such as Admin Access permissions\) with Discord roles **unless** you trust staff with that role, or it's just you.
* The community owner is completely ignored during the synchronization process.
* "Principle of Least Privilege" should be exercised during this setup. Don't give out permissions you don't think users performing the role would need.
* Discontinue use of permission keys ASAP. The bot "takes over" synchronization and will remove permissions granted by permission keys if they don't have a role that grants it.
  * Same goes for manual permission grants, **unless there is no role granting that permission**.



