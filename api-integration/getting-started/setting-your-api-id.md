---
description: >-
  Learn how to map in-game players to Sonoran CAD users with communityUserId,
  Roblox account linking, or an account secret key.
---

# Map In-Game Users to CAD Users

{% hint style="info" %}
API IDs are no longer the recommended account-mapping method for new integrations.
{% endhint %}

Your integration must be able to tell Sonoran CAD which account an in-game player belongs to. There are three main ways to do that.

## Option 1: `communityUserId`

Use `communityUserId` when your game server controls its own player identifier, such as FiveM.

This is the default approach used by our [FiveM integration resource](../../integration-plugins/in-game-integration/fivem-installation/). Players link their CAD account in-game with [`/link`](../../integration-plugins/in-game-integration/link-user-in-game.md), and Sonoran CAD stores the player's game identifier in the account's `communityUserId` field.

By default, the FiveM resource uses the `primaryIdentifier` config value, which is set to `license` unless you change it.

If you are building your own link flow, use these endpoints:

- [Create Community Link](../api-endpoints-v2/general/accounts/create-community-link.md)
- [Check Community Link](../api-endpoints-v2/general/accounts/check-community-link.md)

Once linked, pass `communityUserId` to supported v2 endpoints to target that player's Sonoran CAD account.

## Option 2: Roblox account linking

Use Roblox account linking when the player's Roblox identity is already the source of truth for your integration.

Players can link their Roblox account directly to their Sonoran account. Our [ER:LC getting started guide](../../integration-plugins/erlc/getting-started.md#linking-your-roblox-account) walks through that flow.

After the account is linked, use the `roblox` parameter on supported v2 endpoints instead of `communityUserId`.

This is the preferred approach for Roblox-based integrations because it targets the linked Roblox account directly.

## Option 3: account secret key to `accountUuid`

Use an account secret key when you already have a trusted Sonoran account secret and need to resolve it to the user's Sonoran account UUID.

Start by retrieving the user's [Account Secret ID](account-secret-id.md), then verify it with [Verify Secret](../api-endpoints-v2/general/accounts/verify-secret.md). That endpoint returns the matched `accountUuid`.

You can then use `accountUuid` on supported v2 endpoints.

Support for `accountUuid` is more limited than `communityUserId` or `roblox`, so this should usually be treated as a fallback rather than your primary mapping strategy.

## Next Steps

1. Retrieve your [community ID and API key](retrieving-your-credentials.md).
2. Choose whether your integration should use `communityUserId`, `roblox`, or `accountUuid`.
3. Build against the [v2 libraries](../api-endpoints-v2/libraries.md) or the full [v2 API docs](../api-endpoints-v2/).

If an endpoint supports both account selectors, use the one that matches your integration source of truth.
