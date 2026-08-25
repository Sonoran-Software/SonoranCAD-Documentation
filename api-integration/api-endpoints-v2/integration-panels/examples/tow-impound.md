---
description: Display pending and assigned tow requests with vehicle details, then accept or complete each request from the CAD.
---

# Tow and Impound

Display pending and assigned tow requests with vehicle details, then accept or complete each request from the CAD.

![Tow and Impound custom integration panel](<../../../../.gitbook/assets/integration-panels/tow-impound.png>)

## Flow

1. Create the panel with the definition below.
2. Replace the instance state whenever the in-game system changes.
3. Poll actions, apply them in the third-party system, then acknowledge each result.

## Actions

| Action ID | Purpose |
| --- | --- |
| `tow.accept` | Assign the selected request. |
| `tow.complete` | Mark an assigned request complete. |

## Definition JSON

[Open the raw definition](json/tow-impound-definition.json)

<details>
<summary>Copy the complete definition</summary>

```json
{
  "schemaVersion": 1,
  "key": "example.tow-requests",
  "name": "Tow & Impound",
  "icon": "fas fa-truck-pickup",
  "surfaces": ["dispatch", "police"],
  "body": [
    {
      "type": "row",
      "gap": "sm",
      "children": [
        { "type": "badge", "label": "Pending: {{state.summary.pending}}", "appearance": "primary" },
        { "type": "badge", "label": "Assigned: {{state.summary.assigned}}", "appearance": "info" },
        { "type": "badge", "label": "Completed today: {{state.summary.completed}}", "appearance": "positive" }
      ]
    },
    {
      "type": "repeat",
      "source": "$state.requests",
      "emptyText": "No tow requests",
      "layout": "grid",
      "minItemWidth": 300,
      "gap": "sm",
      "search": {
        "placeholder": "Search plate, vehicle, or location",
        "fields": ["plate", "vehicle", "location", "requester", "status"]
      },
      "sort": {
        "label": "Order",
        "default": "priority",
        "options": [
          {
            "label": "Pending first",
            "value": "priority",
            "rules": [
              { "path": "status", "order": ["PENDING", "ASSIGNED", "COMPLETED"] },
              { "path": "createdAt", "direction": "asc" }
            ]
          },
          {
            "label": "Newest first",
            "value": "newest",
            "rules": [{ "path": "createdAt", "direction": "desc" }]
          },
          {
            "label": "Plate A-Z",
            "value": "plate",
            "rules": [{ "path": "plate", "direction": "asc" }]
          }
        ]
      },
      "children": [
        {
          "type": "section",
          "style": {
            "borderColor": "$item.color",
            "borderStyle": "solid",
            "borderWidth": "1px",
            "borderRadius": "6px",
            "minHeight": "166px"
          },
          "children": [
            {
              "type": "row",
              "align": "center",
              "children": [
                { "type": "icon", "icon": "fas fa-truck-pickup", "color": "$item.color" },
                { "type": "text", "text": "$item.plate", "variant": "title", "grow": true },
                { "type": "badge", "label": "$item.status", "appearance": "$item.appearance" }
              ]
            },
            { "type": "text", "text": "$item.vehicle" },
            { "type": "text", "text": "$item.location", "appearance": "muted" },
            { "type": "text", "text": "Requested by {{item.requester}}", "variant": "caption", "appearance": "muted" },
            {
              "type": "button",
              "label": "Accept request",
              "icon": "fas fa-check",
              "appearance": "primary",
              "visibleWhen": { "path": "$item.pending", "equals": true },
              "action": {
                "id": "tow.accept",
                "values": { "requestId": "$item.id" }
              }
            },
            {
              "type": "button",
              "label": "Mark complete",
              "icon": "fas fa-flag-checkered",
              "appearance": "positive",
              "visibleWhen": { "path": "$item.assigned", "equals": true },
              "action": {
                "id": "tow.complete",
                "values": { "requestId": "$item.id" }
              }
            }
          ]
        }
      ]
    }
  ]
}
```
</details>

## Example State

[Open the raw state](json/tow-impound-state.json)

<details>
<summary>Copy the example state</summary>

```json
{
  "summary": { "pending": 2, "assigned": 1, "completed": 8 },
  "requests": [
    { "id": "tow-1042", "plate": "46EJX219", "vehicle": "Vapid Stanier · Black", "location": "Alta St / Vespucci Blvd", "requester": "1A-12", "status": "PENDING", "createdAt": "2026-08-25T18:12:00Z", "pending": true, "assigned": false, "color": "primary", "appearance": "primary" },
    { "id": "tow-1043", "plate": "83KLM550", "vehicle": "Bravado Bison · White", "location": "Route 68 / Joshua Rd", "requester": "2L-04", "status": "PENDING", "createdAt": "2026-08-25T18:16:00Z", "pending": true, "assigned": false, "color": "primary", "appearance": "primary" },
    { "id": "tow-1039", "plate": "29QRS118", "vehicle": "Karin Sultan · Blue", "location": "Mission Row Impound", "requester": "1B-31 · Tow 7", "status": "ASSIGNED", "createdAt": "2026-08-25T17:54:00Z", "pending": false, "assigned": true, "color": "blue", "appearance": "info" }
  ]
}
```
</details>

