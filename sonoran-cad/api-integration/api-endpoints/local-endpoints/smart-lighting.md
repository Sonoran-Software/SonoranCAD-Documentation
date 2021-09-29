---
description: >-
  Local API endpoints are pushed directly to the local desktop application,
  typically from in-game or other network devices.
---

# Smart Lighting

{% api-method method="post" host="http://localhost" path=":9990/lighting" %}
{% api-method-summary %}
Set Smart Light State
{% endapi-method-summary %}

{% api-method-description %}
This method sets the current smart lighting state.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="state" type="string" required=true %}
some\_state\_here
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
some_state_here
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
{
    "state": "lights"
}
```

### Lighting States

| State | Description |
| :--- | :--- |
| `restore` | Toggle 'Restore' lights when there is no active event |
| `lights` | Toggle 'Emergency' lights when emergency vehicle lights are on |
| `panic` | Toggle 'Panic' lights |
| `left` | Toggle the left turn signal lights |
| `right` | Toggle the right turn signal lights |
| `hazard` | Toggle the hazard lights |

### Local Port

The local port \(`9990` by default\) can be modified in the bodycam configuration section.

![Sonoran CAD - Bodycam Port](../../../../.gitbook/assets/image%20%28273%29.png)

