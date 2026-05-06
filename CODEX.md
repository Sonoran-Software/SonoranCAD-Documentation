# Codex Rules

## Sonoran CAD v2 OpenAPI

When editing any documented v2 API endpoint under `api-integration/api-endpoints-v2/`, keep the root master OpenAPI import on `api-integration/api-endpoints-v2/README.md` in sync.

After any v2 endpoint OpenAPI change:

1. Run `python tools/generate_v2_openapi_master.py`
2. Verify the generated `Full OpenAPI Collection` block on `api-integration/api-endpoints-v2/README.md`
3. Do not ship a v2 endpoint doc change without the regenerated master collection if the combined spec changed
