---
description: >-
  Fix Sonoran CAD FiveM issues caused by read-only files or missing write
  permissions on Windows and Linux hosts.
---

# Read and Write Permissions

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## Sonoran CAD FiveM - Fix file permission issues

If the `sonorancad` resource cannot create, rename, or update files, you may see startup issues like:

* `Failed to create target file`
* `Failed to rename ..._config.dist.lua to ..._config.lua`
* `Unable to open config backup file`
* Changes not saving after updates or restarts

These usually mean your host has marked the resource files as read-only, or the server process does not have permission to write to them.

## Host Restrictions

Some game panel hosts (Ex: ZAP Hosting) do not allow FiveM resources to programmatically modify other files. This blocks the Sonoran CAD resource from updating itself. In this case, you must disable automatic updates and manually install updated versions of the resource as they release.

To disable automatic updates navigate to your config file:

`[sonorancad]/sonorancad/configuration/config.json` and change `allowAutoUpdate` from `true` to `false`.

Looking for a server host? Learn more about our [one-click installation here](https://docs.sonoransoftware.com/promotions/fivem-hosting).

## Step 1: Open your game panel

Log into the panel where your FiveM server is hosted, such as `txAdmin`, `Pterodactyl`, `ZAP-Hosting`, `Gamepanel`, or your VPS file manager.

## Step 2: Locate the Sonoran CAD resource

Check the main Sonoran CAD resource folder and configuration folder:

```
resources/[sonorancad]/sonorancad/
resources/[sonorancad]/sonorancad/configuration/
```

Pay special attention to:

```
resources/[sonorancad]/sonorancad/configuration/config.json
resources/[sonorancad]/sonorancad/configuration/*_config.lua
```

## Windows hosts

### 1. Open the file or folder properties

Start with the `configuration` folder. If needed, also check the full `sonorancad` folder.

```
resources\[sonorancad]\sonorancad\configuration\
```

1. Right-click the folder or affected file
2. Click **Properties**

### 2. Allow read and write access

Under the **General** tab:

1. Uncheck **Read-only**
2. Click **Apply**
3. Choose to apply changes to this folder, subfolders, and files if prompted
4. Click **OK**

If you only changed a single file and the issue comes back, repeat the process on the entire `sonorancad` folder.

## Linux hosts

### 1. Locate the resource files

Open your host panel or file manager and navigate to:

```
resources/[sonorancad]/sonorancad/configuration/
```

### 2. Fix file permissions

Make sure the server can write to the configuration files and backup directory.

Recommended file permissions:

* `766`
* If that fails, try `666`

If your panel supports permission changes:

1. Right-click the `configuration` folder or affected file
2. Select **Permissions**
3. Apply the updated permissions

If your host does not allow permission changes, contact the hosting provider and ask them to make the Sonoran CAD resource writable.

## Quick permission reference

Each permission digit is the sum of:

* `4` = read
* `2` = write
* `1` = execute

Common values:

* `4` = read only
* `6` = read + write
* `7` = read + write + execute

## Final step: restart the resource

After updating permissions, restart the Sonoran CAD resource or your full server:

```
restart sonorancad
```

If the issue continues, verify the files are named correctly and were not saved with extra extensions such as `config.json.json`.
