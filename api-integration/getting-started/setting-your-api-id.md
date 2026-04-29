---
description: Learn how to map in-game players to Sonoran CAD users with unique identifiers.
---

# Map Players to CAD Users

Your integration must be able to tell Sonoran CAD which account an in-game player belongs to. There are three main ways to do that.

## Option 1: `communityUserId`

Use `communityUserId` when your game server controls its own player identifier, such as FiveM.

This is the default approach used by our [FiveM integration resource](../../integration-plugins/in-game-integration/fivem-installation/). Players link their CAD account in-game with [`/link`](../../integration-plugins/in-game-integration/link-user-in-game.md), and Sonoran CAD stores the player's game identifier in the account's `communityUserId` field.

By default, the FiveM resource uses the `primaryIdentifier` config value, which is set to `license` unless you change it.

#### Create Community Link

Use the following endpoint to create a 4-digit link code and associate it with your game's unique player identifier

* [Create Community Link](../api-endpoints-v2/general/accounts/create-community-link.md)

#### Complete User Link

Users can complete the link verification by logging in and visiting `sonorancad.com/id?code=1234`. This completes the link and automatically joins the user to the community (if not already).

#### Check User Link

Use the following API endpoint and push event to programmatically confirm that a user has completed the link.

* [Check Community Link](../api-endpoints-v2/general/accounts/check-community-link.md)
* Event Community Link

Once linked, pass `communityUserId` to supported v2 endpoints to target that player's Sonoran CAD account.

## Option 2: Roblox account linking

Use Roblox account linking when the player's Roblox identity is already the source of truth for your integration.

Players can link their Roblox account directly to their Sonoran account. Our [ER:LC getting started guide](../../integration-plugins/erlc/getting-started.md#linking-your-roblox-account) walks through that flow.

After the account is linked, use the `roblox` parameter on supported v2 endpoints instead of `communityUserId`.

This is the preferred approach for Roblox-based integrations because it targets the linked Roblox account directly.

## Option 3: account secret key to `accountUuid`

Use an account secret key when you already have a trusted Sonoran account secret and need to resolve it to the user's Sonoran account UUID.

#### User Secret ID

User's can copy their account's secret ID from the settings panel.

<figure><img src="../../.gitbook/assets/Screenshot 2026-04-29 at 12.20.10 AM.png" alt=""><figcaption></figcaption></figure>

#### Verify the Secret

Use the following endpoint to verify the secret ID and get the user's Sonoran account UUID

* [Verify Secret](../api-endpoints-v2/general/accounts/verify-secret.md)

You can then use `accountUuid` on supported v2 endpoints.

Support for `accountUuid` is more limited than `communityUserId` or `roblox`, so this should usually be treated as a fallback rather than your primary mapping strategy. Reach out to our development team if more expansion is required for your application.
