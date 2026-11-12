# HEX 0.2.0

A native Windows x64 music player built with Rust and Slint, adapted from featherplay. No Electron, browser shell, subscription, tracking SDK or personal server.

## Install or run

Use **HEX-Setup-x64.exe** for a per-user installation without administrator privileges, or extract the complete **HEX-Portable-0.2.0-x64** folder and run **HEX.exe**, keeping its Microsoft runtime DLLs beside it. This build is unsigned. Check SHA256SUMS-0.2.0.txt and follow normal Windows security decisions.

Official downloads: https://github.com/subliminalsidkthemeaning/HEX/releases/latest

The installer upgrades JOLT in place using the same installation identity. It gracefully closes the installed player to save state. The executable, shortcuts and displayed product name become HEX. A previous installation may retain its original Programs\JOLT directory for upgrade compatibility.

## Your music and settings

Existing favorites, local playlists, history, queue, account sessions and preferences are retained. **Library → Liked** remains the favorites view. Hearts and local favorite persistence have not been replaced. Signed-in libraries depend on the authenticated service's capabilities and permissions; anonymous listening cannot access a private account library.

For compatibility, the default data locations remain **%APPDATA%\JOLT** and **%LOCALAPPDATA%\JOLT**. Credential Manager continues using the existing jolt service, and the Windows application ID is retained. These internal compatibility names are intentional. HEX_HOME selects an isolated profile; JOLT_HOME remains an alias. Portable builds also use the user profile by default.

The HEX uninstaller removes program integration but preserves music metadata, settings and credentials. Do not use an old JOLT uninstaller to remove saved data during an upgrade. Back up your profile before manually deleting any data.

## Listening

Search songs, albums, artists and playlists. Use song menus for radio, play next, queue and local playlists. The queue is a bounded timeline: past songs stay above the highlighted current song, recommendations below it. Advance playback to follow the current row, or browse/replay earlier entries. Shuffle, autoplay, repeat, media keys and Windows media controls use the existing engine.

Home prioritizes actual recent listening and catalog recommendations. Source-classified editorial and promotional playlist shelves are excluded from default discovery; personal playlists, library and playlist search remain available. Availability depends on the service, region, account and network. No DRM or paid-access restrictions are bypassed.

Click current-song artwork or title to open the existing Now Playing view without resetting playback. The compact player opens that same view. Hover/pressed feedback uses the charcoal/red HEX theme and supplied official logo.

Performance Mode is enabled by default. It retains low-frequency progress and reduced motion. Turning it off enables visible-only smooth progress and lyric transitions. Visual progress interpolates between real audio samples and never extrapolates beyond the latest sample. Hidden/minimized views suspend animation work. Visible covers are additional to the bounded decoded-cover cache budget (8 MB Performance Mode, 24 MB otherwise).

Lyrics can be enabled in Settings. Synchronized lyrics center the current line; browse manually and use **Return to current line** to resume following. Real enhanced-LRC word timestamps receive word highlighting; line-only data remains line-synchronized, and plain lyrics remain unsynchronized. No word timings are fabricated. Optional LRCLIB requests follow the existing permission setting. Lyrics are not fetched continuously while hidden.

## Windows and Discord

Settings retain volume, quality, autoplay, close behavior, optional startup and optional Discord Rich Presence. Startup and Rich Presence are off by default. Local API is unrelated and is not enabled for Discord.

Discord uses lightweight local RPC and public Application ID **1570159402856751135**. No bot, client secret, OAuth or backend is needed. Song title, artist, artwork and timeline remain; song/art click-through URLs are omitted. **Download HEX** is enabled only after the configured public HTTPS installer passes verification. The owner may not see their own button. See docs/DISCORD.md for the required Developer Portal rename and official hex artwork upload.

HEX uses its own release page. Automatic installation is gated on HEX-controlled update signing keys; no upstream product's signing keys are trusted. Until those keys are configured, obtain application updates manually from official releases. First playback may obtain pinned, hash-verified yt-dlp and Deno helpers from official upstream releases. These are compatibility helpers, not UI runtimes or permanent browser processes. Optional account connection may use WebView2 or a browser temporarily.

See docs/RELEASE-0.2.0.md, docs/PERFORMANCE-0.2.0.md and docs/MANUAL-VERIFICATION.md for measured results and verification limits. Third-party licenses and notices are included. HEX is unofficial and is not endorsed by Google, YouTube, Spotify, Apple or Discord.

This public repository contains releases, documentation and notices only. Application source is not published here. Historical JOLT releases remain available at https://github.com/subliminalsidkthemeaning/JOLT/releases .
