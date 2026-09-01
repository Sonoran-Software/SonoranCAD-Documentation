---
description: Create a civilian character in CAD from an in-game form, with optional framework autofill and a character portrait.
---

# Civilian Registration (CivReg)

Civilian Registration lets players create a new civilian character on their linked Sonoran CAD account without leaving FiveM. Run `/civreg` to open **Character Registration**, complete your community's character form, and submit it to CAD.

The form loads your community's live character template, including its sections, field labels, choices, required fields, and visibility rules. QBCore or supported ESX identity information can prefill the form, and image fields let players capture their current in-game character's portrait.

<figure><img src="../../../.gitbook/assets/civreg-character-form.jpg" alt="Character Registration showing sample identity details, required fields, a date format, and residency options"><figcaption><p>Character Registration interface with a sample template and fictional character details.</p></figcaption></figure>

{% hint style="info" %}
Screenshots show the actual registration interface rendered in a browser preview with sample data. Your community's fields and layout depend on its CAD template. Portrait capture and CAD record creation run in FiveM.
{% endhint %}

## Activation Guide

### 1. Install or Update Sonoran CAD for FiveM

Follow the [FiveM installation guide](../fivem-installation/) and use a resource version that includes `sonorancad/submodules/civreg`. The submodule is bundled with the Sonoran CAD resource; its supplied configuration has `enabled = true`.

Keep the installation guide's startup configuration in `server.cfg`:

```cfg
exec @sonorancad/sonorancad.cfg
```

Your base resource must be connected to the correct CAD community with a working API configuration. See [installation troubleshooting](../fivem-installation/troubleshooting/) if the resource cannot connect.

### 2. Configure the Submodule

Open `sonorancad/configuration/civreg_config.lua`. If only `civreg_config.dist.lua` exists, copy it to `civreg_config.lua` before editing. Keep `enabled = true` and `templateId = 7` for civilian character registration.

Save your changes and restart the `sonorancad` resource. See [Submodule Configuration](../submodule-configuration/) for general configuration instructions.

### 3. Link Players to CAD

Each player must [link their CAD account in-game](../link-user-in-game.md) before using `/civreg`. The new character belongs to that linked account. Players do not need an online emergency unit to register a civilian.

### 4. Review Your Character Template

In CAD, open **Admin > Customization > Custom Records** and review the civilian character template. The built-in character template ID is `7`. See [Creating Custom Record and Report Types](../../../tutorials/customization/creating-custom-record-and-report-types.md) for editing fields and sections.

The form uses the template from CAD, so you do not need to maintain a separate list of form fields in the submodule configuration. Review required fields, dropdown options, read-only settings, masks, and dependencies before players use it. Add an editable **Image** field if players should attach a portrait, and make that field required if a portrait is mandatory.

Templates are cached for **60 seconds** by default. After saving a template change, allow the cache to expire, then close and reopen `/civreg` to load the updated form. An already-open form does not refresh automatically.

### 5. Configure Optional Autofill and Portrait Uploads

For identity autofill, follow [Framework Autofill](#framework-autofill). For templates with image fields, review [Portrait Uploads](#portrait-uploads) and the image size limit.

## Player Guide

### Register a Character

1. Join the server and complete the [CAD account link](../link-user-in-game.md).
2. Run `/civreg`, or your server's configured registration command.
3. Review any prefilled details and complete the remaining fields. A red `*` marks required player input. Follow the displayed format for dates and other masked fields.
4. Scroll through the form. Additional fields or sections may appear when you change an answer.
5. If the form includes a portrait field, select **Click to take a selfie**. Wait for the preview; click it again to retake the portrait if needed.
6. Select **Register Character** and wait for the result. On success, the form closes and a confirmation notification appears. The new civilian is saved to your linked CAD account.

Each successful submission creates a **new character**. Use CAD to manage existing characters and select the civilian you want to use with other integrations.

### Take a Character Selfie

The selfie control captures your current FiveM character's headshot. It uses the character you are playing when you click the control. Each editable image field has its own capture button, and the preview lets you review or retake that field's image before submitting.

<figure><img src="../../../.gitbook/assets/civreg-selfie-control.jpg" alt="Character Photo section with the Click to take a selfie control above Cancel and Register Character"><figcaption><p>Scroll to an image field and select Click to take a selfie to capture your current in-game character.</p></figcaption></figure>

If capture fails, the form displays an error and lets you try again. Wait for an active capture to finish before registering.

### Correct or Cancel a Form

If a required value is missing or a value does not match its format, the form displays an error. Correct the field and submit again. A failed registration leaves the form open so you can review the message.

Select **Cancel**, the **×** button, or press **Escape** to close the form before submitting. Closing discards the unfinished form; reopening starts a new registration. Closing controls are disabled while a submission is pending.

A registration session expires after **10 minutes**. If it expires, close the form, reopen the command, and enter the details again.

## Template Behavior

| Template setting or field | In-game behavior |
| --- | --- |
| Sections, labels, and field widths | The form follows the template's section order, labels, and field sizes. Narrow displays stack fields vertically. |
| Required fields | Editable required fields receive a red `*` and must be completed when visible. |
| Text and multi-line text | Players enter the value directly. Text values are limited to 8,000 characters; a mask may impose a shorter limit. |
| Dates and masks | The form uses the configured format, such as `MM/DD/YYYY`, and checks the entered value against it. |
| Dropdowns and checkboxes | Choices come from the template. Checkbox fields support multiple selections. |
| Status | Uses the template's choices. If none are supplied, the form offers Pending, Approved, and Rejected. |
| Field and section dependencies | Show or hide content based on another field's selected value. Hidden answers and portraits are excluded from the submission. |
| Read-only fields | Players cannot edit them. The form uses available prefilled or template values. |
| Random fields | Automatically populated from the template value or mask and locked for editing. |
| Supervisor fields | Omitted from the player's registration form. |
| Labels, record IDs, and unit fields | Display-only or disabled. Unit fields are not a substitute for civilian identity autofill. |
| Image fields | Editable images become selfie controls. Read-only images cannot be captured. |

Address fields accept typed text in this form. Specialized CAD editors such as address search, record linking, charges, and diagrams are not provided by the registration interface.

## Framework Autofill

Autofill is optional. Players can complete the registration form without a framework. To prefill supported identity values:

1. Configure and enable [Framework Support (ESX/QBCore)](framework-support-esx-qbcore-and-auto-fines/).
2. Start the supported framework before Sonoran CAD and set `usingQBCore` appropriately in `frameworksupport_config.lua`.
3. Match `autofillFieldIds` in `civreg_config.lua` to your character template's **Field Mapping ID** values.
4. Restart Sonoran CAD and open a new registration form while playing a loaded framework character.

The left-hand keys describe the identity values supplied by the framework. The right-hand strings identify the destination fields in CAD:

```lua
autofillFieldIds = {
    first = "first",
    last = "last",
    dob = "dob",
    sex = "sex",
    height = "height",
    phone = "phone",
    nationality = "nationality"
},
```

For example, if your first-name field has the custom Field Mapping ID `givenName`, change only that entry to `first = "givenName"`. These mappings control autofill; they do not create or rename template fields.

| Identity value | Default destination | Notes |
| --- | --- | --- |
| First name | `first` | Available framework first name. |
| Last name | `last` | Available framework last name. |
| Date of birth | `dob` | Dates supplied as `YYYY-MM-DD` or `YYYY/MM/DD` are converted when the CAD field uses `MM/DD/YYYY`. |
| Sex | `sex` | Values `0`, `m`, or `male` become `M`; `1`, `f`, or `female` become `F`. Match your template's choices to those values. |
| Height | `height` | Copied as supplied; the submodule does not convert height units. |
| Phone number | `phone` | Filled when the framework supplies a supported phone value. |
| Nationality | `nationality` | Filled when available from the framework. |

Only values supplied by the framework and mapped to an existing template field are prefilled. Missing values leave the template's default or an empty field for the player to complete. Prefilled fields remain editable unless marked read-only in CAD. Framework support is used to read identity details; registration does not update the framework character.

## Portrait Uploads

Captured portraits are uploaded directly with the character registration as **base64 image data**, including the PNG or JPEG data prefix. New submissions do not require a public image URL, reverse proxy, or a saved image file on the game server.

The server validates each portrait before sending the registration to CAD. `maxSelfieBytes` limits the decoded image size to **1 MiB** by default. If an image is invalid or too large, the form displays an error so the player can retake it and try again.

### Updating from URL-Based Portraits

The old `selfieBaseUrl` setting is ignored and can be removed from `civreg_config.lua`. Previously created records keep their original image URLs. Preserve `sonorancad/filestore/civreg` and its existing public route while those records use it; updating the submodule does not convert existing portraits. The resource continues to serve those older files.

## Configuration Reference

Edit `sonorancad/configuration/civreg_config.lua` and restart the resource after changes.

| Option | Default | Description |
| --- | --- | --- |
| `enabled` | `true` | Enables civilian registration. |
| `commandName` | `"civreg"` | Chat command without the leading `/`. Changing it changes the command players use. |
| `templateId` | `7` | CAD character template ID. Keep `7` for civilian registration; selecting a different record type changes what is submitted to CAD. |
| `templateCacheSeconds` | `60` | Shared template cache duration in seconds. `0` disables caching; frequent requests can hit the CAD template endpoint's rate limit. |
| `maxSelfieBytes` | `1024 * 1024` | Maximum decoded size of each base64 portrait upload: 1 MiB by default. |
| `autofillFieldIds` | Mapping shown above | Maps supported framework identity values to CAD Field Mapping IDs. |
| `notificationOverride` | `"none"` | Uses the global notification choice when `none`. Supported overrides listed in the configuration are `ox_lib`, `lation_ui`, `pnotify`, and `chat`. |
| `language` | English strings below | Customizes command help, form labels, and the success notification. |

Leave `pluginName = "civreg"`, `pluginAuthor = "SonoranCAD"`, and `configVersion = "1.0"` as supplied. These identify the submodule and its configuration version.

### Language Settings

| Key in `language` | Default text |
| --- | --- |
| `helpMsg` | `Register a new civilian character in CAD` |
| `title` | `Character Registration` |
| `subtitle` | `Complete the live CAD character form below.` |
| `selfieAction` | `Click to take a selfie` |
| `selfieHint` | `Your current character portrait will be attached to this CAD record.` |
| `submit` | `Register Character` |
| `cancel` | `Cancel` |
| `loading` | `Loading the live CAD template...` |
| `success` | `Character registered successfully in CAD.` |

`loading` is included in the supplied configuration but is not currently displayed by the form. Some validation messages and the `Submitting...` text are built into the interface and are not changed by this language table.

## Troubleshooting

| Problem | What to check |
| --- | --- |
| The command is unavailable | Confirm `civreg` is installed, the active configuration is named `civreg_config.lua`, `enabled` is `true`, and you are using the configured `commandName`. Restart the resource after configuration changes. |
| The player is asked to link CAD | Complete [Link User In-Game](../link-user-in-game.md) with the intended CAD account, then retry. |
| Repeated commands do nothing | A form already open will not reopen. Requests also have a three-second cooldown; close the current form and wait before retrying. |
| Template changes are missing | Save the template in CAD, wait for `templateCacheSeconds` to pass, then reopen the form. |
| Autofill is missing or incorrect | Check that Framework Support is enabled, the framework character is loaded, and each destination Field Mapping ID exists. Review date formats, sex choices, and height units. |
| A field or section is missing | Review its dependency rules and whether the field is supervisor-only. |
| A field cannot be edited | Check read-only settings and whether the field is an automatically managed field such as a random value or ID. |
| Selfie capture fails | Retry with the intended character fully loaded. If it persists, check client errors and that the Sonoran CAD UI files are up to date. |
| A portrait is rejected as invalid or too large | Retake it and review the displayed error. Check `maxSelfieBytes` for the decoded size limit. |
| A portrait is missing from an older URL-based CAD record | Open its saved URL externally. Check the original public route and that the file still exists in `filestore/civreg`. See [Updating from URL-Based Portraits](#updating-from-url-based-portraits). |

### Registration Error Codes

| Code | Meaning | Resolution |
| --- | --- | --- |
| [ERR-CR-101](../fivem-installation/troubleshooting/error-codes.md#err-cr-101) | The live CAD character template could not be loaded. | Check the CAD connection and template ID, then retry. If requests are rate limited, keep template caching enabled and wait before retrying. |
| [ERR-CR-102](../fivem-installation/troubleshooting/error-codes.md#err-cr-102) | The form expired or contains invalid fields or portrait data. | Correct the displayed validation error. Retake an invalid portrait and check `maxSelfieBytes`. If the form expired, close and reopen the registration command; sessions last 10 minutes. |
| [ERR-CR-105](../fivem-installation/troubleshooting/error-codes.md#err-cr-105) | CAD could not create the character. | Review the accompanying API failure in the server console, confirm the linked account and template, and correct the reported issue before retrying. |

`ERR-CR-103` and `ERR-CR-104` apply to older versions that hosted portrait files. Current base64 uploads do not use those paths; see the [error-code reference](../fivem-installation/troubleshooting/error-codes.md#civilian-registration-errors) when troubleshooting an older installation.

## Related Submodules

* [Civilian Integration](civilian-integration.md) retrieves civilian information and provides the in-game ID commands.
* [Vehicle Register (VehReg)](vehreg.md) registers the vehicle a player is sitting in to their selected CAD character.
* [Framework Support (ESX/QBCore)](framework-support-esx-qbcore-and-auto-fines/) supplies optional identity information for autofill.
