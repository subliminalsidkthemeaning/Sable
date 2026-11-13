# Discord Listening presence

Sable uses optional local Discord IPC with application ID **1570159402856751135**. No bot token, client secret, OAuth login, server or Local API is required. Users control presence in Settings and Discord's own activity privacy settings.

The activity supplies its supported name field as **Sable**, type Listening, real song title and artist, album artwork where supported, and playback timestamps. Artwork and song information have no clickable song URLs. Updates follow playback events with coalescing and bounded reconnect backoff. Stopping, disabling integration or exiting clears presence; a missing Discord client does not interrupt playback.

The sole button is **Get Sable**, using:
https://github.com/subliminalsidkthemeaning/Sable/releases/latest/download/Sable-Setup-x64.exe

The target remains inactive until an anonymous HTTPS check confirms an actual executable response. A matched SET_ACTIVITY acknowledgment verifies inclusion in the accepted outgoing payload. Discord commonly hides buttons from the activity owner; visibility and browser behavior require a separate viewer account and must not be inferred from the owner's profile.

## Developer Portal setup

1. Open https://discord.com/developers/applications and select application **1570159402856751135**.
2. Set its public name to **Sable**, retaining the existing application ID.
3. Upload the supplied **assets/discord/sable.png** as Rich Presence artwork with asset key **sable**. This is the exact official 1024×1024 PNG.
4. In Sable Settings → Discord, choose **Save and verify** for the configured installer URL. This confirms the new download address after an upgrade without changing activity privacy settings.
5. Allow Discord metadata/artwork caches to refresh. Test Listening activity from SableMusic.exe, then inspect the profile using another real viewer.

The process filename SableMusic.exe avoids the previous generic HEX.exe game-detection collision. Discord client caches, application metadata and second-viewer rendering are external to the application's acknowledged IPC payload.

Official documentation: https://docs.discord.com/developers/topics/rpc and https://docs.discord.com/developers/discord-social-sdk/development-guides/setting-rich-presence

The published 0.3.0 installer passed anonymous full-file checksum verification and the application’s own bounded HTTPS/MZ verifier. A new live Discord acknowledgment and second-viewer button check were unavailable because no Discord client was running during this release verification.

Official Developer Portal artwork: [sable.png](https://raw.githubusercontent.com/subliminalsidkthemeaning/Sable/main/assets/discord/sable.png).
