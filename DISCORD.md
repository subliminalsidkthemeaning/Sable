# HEX Discord Rich Presence

HEX 0.2.0 preserves lightweight local named-pipe RPC with the ordinary Discord desktop client. Presence is optional and off by default; existing privacy preferences are retained. No bot, token, OAuth, client secret, Local API or additional server/process is required. This release does not change your Discord activity privacy settings.

Application ID: **1570159402856751135** (unchanged). Track title, artist, public album art when supported and clock-based timeline use real playback metadata. The fallback and small brand asset key are **hex**. Artwork and song information do not contain clickable song URLs. The only button is **Download HEX**.

Updates follow playback events and are coalesced to at most one activity update per five seconds. Discord advances its own timeline. Pausing removes the running timeline and follows the saved clear-on-pause/timeout preference. Stopping, disabling presence and exiting clear the activity. A missing client never blocks playback. Reconnection uses bounded backoff; there is no per-second activity polling.

## Developer Portal: required manual branding changes

1. Open https://discord.com/developers/applications/1570159402856751135 .
2. In General Information, rename the existing application to **HEX** and save. Keep its Application ID.
3. Upload the supplied official logo as the application icon.
4. Under Rich Presence → Art Assets (or the current equivalent), upload **HEX_Branding_Kit/discord/hex.png**, also supplied as the release asset **hex.png**. It is 1024 × 1024, approximately 147 KiB. Set its asset key to **hex**.
5. Allow for Discord caching and reconnect presence from HEX Settings if needed.

The application name displayed by Discord is controlled in the Developer Portal. Changing local code cannot rename the server-managed application. Until the asset is uploaded, Discord may omit the fallback logo/badge. Existing album artwork remains supported.

## Download HEX

Stable target: https://github.com/subliminalsidkthemeaning/HEX/releases/latest/download/HEX-Setup-x64.exe

A repository alone is not a verified installer. HEX initially marks this URL unverified. Enabling Discord or choosing **Save and verify** performs an anonymous HTTPS check for a Windows executable signature and caches success. Invalid, missing, local, non-HTTPS and failed links cannot become buttons. Changing the URL invalidates previous verification. A viewer opens the URL in their browser under normal download/security controls; nothing silently runs.

After a matching successful SET_ACTIVITY acknowledgment, HEX records the exact accepted outgoing activity containing Download HEX once per connection. This verifies payload inclusion, not a click by another person. Discord commonly hides activity buttons from their owner; use another viewer to inspect/click it when available.

Official references: https://docs.discord.com/developers/topics/rpc and https://docs.discord.com/developers/discord-social-sdk/development-guides/setting-rich-presence .
