---
description: Bidirectionally synchronize locally stored CAD notepad entries with an iframe parent.
---

# Notepad Sync

The notepad iframe API keeps an in-game notepad synchronized with the notepad inside an embedded Sonoran CAD frontend. Notes remain in the CAD frontend's local browser storage and are not sent to the Sonoran CAD backend.

Each note has the following shape:

```json
{
  "id": "734c8df5-af36-4607-bb01-65e4d8ee64b0",
  "title": "Traffic Stop",
  "notes": "Blue Sultan, plate 4QXR128",
  "metadata": {
    "lookups": [
      {
        "start": 19,
        "end": 26,
        "text": "4QXR128",
        "type": "PLATE",
        "search": { "first": "", "last": "", "mi": "", "plate": "4QXR128" },
        "result": {
          "version": 2,
          "title": "State Return",
          "header": null,
          "sections": []
        }
      }
    ]
  }
}
```

`id` is a stable identifier. `metadata` is an optional JSON object reserved for integration-specific data such as future text annotations or links. CAD automatically adds an ID and empty metadata object to older notes that do not have them.

When a CAD user highlights text and runs a name or plate lookup, CAD stores the linked text range, search object, and latest NCIC state-return snapshot in `metadata.lookups`. Preserve `metadata` when syncing notes from the iframe so users can preview the results or click the linked text to repeat the lookup. `result` is added after the lookup completes and uses the same state-return structure displayed in CAD call notes.

## Get Notes

Request the full note list after the iframe loads:

```javascript
cadFrame.contentWindow.postMessage({
  type: 'scad:notepad:get',
  requestId: 'initial-sync',
}, cadOrigin);
```

CAD responds with:

```json
{
  "type": "scad:notepad:state",
  "requestId": "initial-sync",
  "notes": []
}
```

## Set Notes

Send the complete note list whenever the in-game notepad adds, edits, or deletes a note:

```javascript
cadFrame.contentWindow.postMessage({
  type: 'scad:notepad:set',
  requestId: 'save-notes',
  notes: [
    {
      id: '734c8df5-af36-4607-bb01-65e4d8ee64b0',
      title: 'Traffic Stop',
      notes: 'Blue Sultan, plate 4QXR128',
      metadata: {},
    },
  ],
}, cadOrigin);
```

CAD stores the list locally, updates an open CAD notepad, and responds with the canonical list in `scad:notepad:changed`. If a note does not include `id` or `metadata`, CAD adds them in the response.

## Listen for CAD Changes

CAD emits the full note list whenever notes are changed in CAD and after applying `scad:notepad:set`:

```json
{
  "type": "scad:notepad:changed",
  "requestId": "save-notes",
  "notes": [
    {
      "id": "734c8df5-af36-4607-bb01-65e4d8ee64b0",
      "title": "Traffic Stop",
      "notes": "Blue Sultan, plate 4QXR128",
      "metadata": {}
    }
  ]
}
```

Changes made directly in CAD do not include `requestId`. Replace the in-game note list with the received `notes` array to keep both sides synchronized.

If `scad:notepad:set` does not contain a `notes` array, CAD responds with `scad:notepad:error` and `error: "invalid_notes"`.
