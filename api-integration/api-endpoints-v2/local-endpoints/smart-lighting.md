---
description: >-
  Local API endpoints are pushed directly to the local desktop application,
  typically from in-game or other network devices.
---

# Smart Lighting

{% swagger baseUrl="http://localhost" path=":9990/lighting" method="post" summary="Set Smart Light State" %}
{% swagger-description %}
This method sets the current smart lighting state.
{% endswagger-description %}

{% swagger-parameter in="body" name="state" type="string" %}
some_state_here
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
some_state_here
```
{% endswagger-response %}
{% endswagger %}

```javascript
{
    "state": "lights"
}
```

### Lighting States

| State         | Description                                                    |
| ------------- | -------------------------------------------------------------- |
| `restore`     | Toggle 'Restore' lights when there is no active event          |
| `lights`      | Toggle 'Emergency' lights when emergency vehicle lights are on |
| `panic`       | Toggle 'Panic' lights                                          |
| `available`   | Toggle lights when unit status is changed                      |
| `unavailable` | Toggle lights when unit status is changed                      |
| `enroute`     | Toggle lights when unit status is changed                      |
| `onscene`     | Toggle lights when unit status is changed                      |
| `busy`        | Toggle lights when unit status is changed                      |
| `left`        | Toggle the left turn signal lights                             |
| `right`       | Toggle the right turn signal lights                            |
| `hazard`      | Toggle the hazard lights                                       |

### Local Port

The local port (`9990` by default) can be modified in the bodycam configuration section.

![Sonoran CAD - Bodycam Port](<../../../../.gitbook/assets/image (200).png>)
