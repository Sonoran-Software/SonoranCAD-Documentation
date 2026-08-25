---
description: Monitor alarm controllers, surface active and fault states, toggle alarms, and play a sound when the active count increases.
---

# Fire Alarm

Monitor alarm controllers, surface active and fault states, toggle alarms, and play a sound when the active count increases.

![Fire Alarm custom integration panel](<../../../../.gitbook/assets/integration-panels/fire-alarm.png>)

## Flow

1. Create the panel with the definition below.
2. Replace the instance state whenever the in-game system changes.
3. Poll actions, apply them in the third-party system, then acknowledge each result.

## Actions

| Action ID | Purpose |
| --- | --- |
| `alarm.set-active` | Toggle one alarm on or off. |

## Definition JSON

[Open the raw definition](json/fire-alarm-definition.json)

<details>
<summary>Copy the complete definition</summary>

```json
{
  "schemaVersion": 1,
  "key": "example.fire-alarms",
  "name": "Fire Alarm",
  "icon": "fas fa-bell",
  "surfaces": ["dispatch", "fire", "ems", "police"],
  "sounds": [
    {
      "id": "alarm-active",
      "url": "https://s3.sonorancad.com/default/examples/demos/fire-alarm-demo.mp3",
      "volume": 0.7,
      "maxDurationMs": 8000,
      "trigger": {
        "event": "state",
        "path": "summary.active",
        "operator": "increased"
      }
    }
  ],
  "body": [
    {
      "type": "row",
      "gap": "sm",
      "children": [
        { "type": "badge", "label": "Active: {{state.summary.active}}", "appearance": "primary" },
        { "type": "badge", "label": "Normal: {{state.summary.normal}}", "appearance": "positive" },
        { "type": "badge", "label": "Fault: {{state.summary.fault}}", "appearance": "warning" }
      ]
    },
    {
      "type": "repeat",
      "source": "$state.alarms",
      "emptyText": "No alarms reported",
      "layout": "grid",
      "minItemWidth": 260,
      "gap": "sm",
      "search": {
        "placeholder": "Search alarms",
        "fields": ["name", "location", "status"]
      },
      "sort": {
        "label": "Order",
        "default": "active",
        "options": [
          {
            "label": "Active first",
            "value": "active",
            "rules": [
              { "path": "active", "direction": "desc" },
              { "path": "name", "direction": "asc" }
            ]
          },
          {
            "label": "Name A-Z",
            "value": "name",
            "rules": [{ "path": "name", "direction": "asc" }]
          },
          {
            "label": "Status",
            "value": "status",
            "rules": [
              { "path": "status", "order": ["ACTIVE", "FAULT", "NORMAL"] },
              { "path": "name", "direction": "asc" }
            ]
          }
        ]
      },
      "children": [
        {
          "type": "section",
          "animation": "$item.animation",
          "style": {
            "borderColor": "$item.color",
            "borderStyle": "solid",
            "borderWidth": "1px",
            "borderRadius": "6px",
            "minHeight": "132px"
          },
          "children": [
            {
              "type": "row",
              "align": "center",
              "children": [
                { "type": "icon", "icon": "fas fa-fire", "color": "$item.color" },
                { "type": "text", "text": "$item.name", "variant": "title", "grow": true },
                { "type": "badge", "label": "$item.status", "appearance": "$item.appearance" }
              ]
            },
            { "type": "text", "text": "$item.location", "appearance": "muted" },
            {
              "type": "toggle",
              "id": "alarm-active",
              "label": "Alarm active",
              "value": "$item.active",
              "color": "$item.color",
              "action": {
                "id": "alarm.set-active",
                "values": { "alarmId": "$item.id", "active": "$value" }
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

[Open the raw state](json/fire-alarm-state.json)

<details>
<summary>Copy the example state</summary>

```json
{
  "summary": { "active": 1, "normal": 1, "fault": 1 },
  "alarms": [
    {
      "id": "mrpd-lobby",
      "name": "MRPD Lobby",
      "location": "Mission Row",
      "status": "ACTIVE",
      "appearance": "primary",
      "color": "primary",
      "animation": "pulse-negative",
      "active": true
    },
    {
      "id": "sandy-24",
      "name": "Station 24",
      "location": "Sandy Shores",
      "status": "NORMAL",
      "appearance": "positive",
      "color": "positive",
      "active": false
    },
    {
      "id": "pillbox",
      "name": "Pillbox Medical",
      "location": "Los Santos",
      "status": "FAULT",
      "appearance": "warning",
      "color": "amber",
      "active": false
    }
  ]
}
```
</details>

