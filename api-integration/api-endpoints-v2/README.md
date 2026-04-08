---
description: View Sonoran CAD's v2 API endpoints and authentication flow.
---

# v2 API Endpoints

The Sonoran CAD v2 API is a new versioned API surface designed for cleaner integrations and future expansion.

## What's Different in v2?

* Resource-style routes under `/v2/...`
* Standard HTTP methods instead of routing everything through `POST`
* `Authorization: Bearer <apiKey>` authentication
* Structured `application/problem+json` error responses
* No v1-style plan gating or API blacklist behavior on these routes

{% hint style="info" %}
The current v2 rollout is intentionally small. More v1-equivalent endpoints will be added over time.
{% endhint %}

## Available v2 Docs

### Authentication

Start here for bearer authentication, common headers, and error handling.

{% content-ref url="authentication.md" %}
[authentication](authentication.md)
{% endcontent-ref %}

### Emergency

These are the first v2 endpoints currently available.

{% content-ref url="emergency/" %}
[emergency](emergency/)
{% endcontent-ref %}
