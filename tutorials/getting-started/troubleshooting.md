# Troubleshooting

## Cannot Load Sonoran CAD

### Tablet Not Loading

If you are using the in-game Tablet, please ensure that you are using the `Login with Sonoran` option and/or have cleared your `nui-storage` folder as shown [here](https://info.sonorancad.com/integration-plugins/integration-plugins/available-plugins/tablet#known-issues).&#x20;

### CAD Not Loading After Recent Update

If you cannot load Sonoran CAD due to a recent update, then please do `Ctrl` + `Shift` + `Refresh` to hard refresh the page and load it from scratch.

### CAD Not Loading (ESET Antivirus)

In certain cases, antivirus programs such as ESET are also known to block connections to the CAD. To add CAD to ESET's allow list, please follow the following instructions:

1. Open ESET program on your computer
2. Press the `F5` key to open Advanced setup.
3. Click `Web access protection`. Expand `URL list management` and click `Edit` next to `Address list`
4. Select `List of allowed addresses` and click `Edit`
5. Click **`Add`** in the `Edit list` window. Paste `*.sonorancad.com*` in the respective field, click `OK` → `OK` to save your changes, and exit the Advanced setup window.
   * If using CMS, also add `*sonorancms.com*`

For more information, see [here](https://support.eset.com/en/kb2960-exclude-a-safe-website-from-being-blocked-by-web-access-protection).
