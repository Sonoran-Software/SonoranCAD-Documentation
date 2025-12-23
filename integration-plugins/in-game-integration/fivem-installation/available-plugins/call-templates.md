---
description: >-
  Allows law enforcement to automatically add a new call and attach the unit in
  the CAD.
---

# Call Templates

{% hint style="warning" %}
This submodule utilizes API endpoints that require the **plus** version of SonoranCAD or higher. For more information, view our [pricing ](../../../../pricing/faq/)page.
{% endhint %}

## Activation Guide

### 1. Download and Install the Core

If you haven't already, be sure to install and configure the [SonoranCAD Core](../) first.

### 2. Activate the Submodule and all Dependencies

Follow the [submodule activation guide](../submodule-configuration/#activating-a-submodule) for the required submodules.

### 3. Configuration

| Option                     | Description                                                                           | Default                              |
| -------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------ |
| `callTypeDirectory`        | Location of the call type JSON file                                                   | `submodules/calltemplates/calltypes` |
| `defaultOrigin`            | Call origin used if the template does not specify one                                 | `2`                                  |
| `defaultStatus`            | Call status used if the template does not specify one                                 | `1`                                  |
| `defaultPriority`          | Call priority used if the template does not specify one                               | `1`                                  |
| `reloadTemplatesOnEachUse` | When true, templates are re-read every command execution (useful while editing files) | `false`                              |

### 3b. Call Type Configuration

In the `calltemplates_config.lua` file you will find a section named `commands` . In here, you can configure each custom command that will be used to create a call. Below you will find the options you can use during configuration.

| Option               | Type    | Description                                                                                                      |
| -------------------- | ------- | ---------------------------------------------------------------------------------------------------------------- |
| `command`            | String  | The name of the command                                                                                          |
| `callTypeFile`       | String  | The name of the associated JSON file for the call type                                                           |
| `descriptionPrefix`  | String  | The prefix of the call description                                                                               |
| `suggestionText`     | String  | The command suggestion text                                                                                      |
| `includeWraithPlate` | Boolean | Attach locked plate from wraithv2 if available                                                                   |
| `includePlayerUnit`  | Boolean | Attach the player's unit to the call                                                                             |
| `useAcePermissions`  | Boolean | Require an ace permission to utilize the command. The ace permission is `command.commandName` \| Ex. `comand.ts` |

### 3c. Call Type JSON Files

Each call type requires a JSON file to be added to the directory `submodules/calltemplates/calltypes` . You can either configure this file yourself or you can download it from SonoranCAD. This [guide](../../../../tutorials/dispatching/creating-a-call.md#import-export-saved-call-types) will explain how to create and export call types

### 4. Set Your API ID

Don't forget to set your account [API ID](../../../../api-integration/getting-started/setting-your-api-id.md) to properly link your in-game user to the CAD.

&#x20;    &#x20;
