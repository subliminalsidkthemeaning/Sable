# HEX 0.2.0 verification

The existing JOLT 0.1.2 code and profiles were backed up before changes, with another profile backup before the installed upgrade. The native Rust/Slint playback engine and single-process design are retained. Public artifacts exclude private source, logs, profiles, sessions, credentials and backups.

## Build and regression checks

- Formatting and strict workspace Clippy with all targets were run; the final logs are retained privately.
- The full CI-profile unit/integration run covered 1,552 cases: 1,551 passed and one expected-text fixture still named the previous product. The corrected fixture then passed in a 235-case targeted run, with all 235 passing. The full run skipped 86 configuration-gated/ignored cases; those are not claimed as passes.
- The additional manual-lyrics regression passed, confirming that scrolling holds position across lyric advancement and the visible return control restores centering. Its five-case run also passed centered forward/backward seeks and all three installer identity checks. This adds one unique regression case to the 1,552-case full run.
- Workspace documentation tests passed (all 11 crates contain zero runnable doctests).
- The audited Windows x64 release compilation passed with no perf-harness or development-cookie feature. Executable product name and version are HEX 0.2.0.

Coverage includes legacy profile locations and settings migration, favorites and library refresh, authenticated-library behavior, queue timeline/replay, playlist source classifications, bottom-player/mini-player navigation, hover/focus behavior, conservative progress interpolation, seeks/pause/resume, real enhanced-LRC parsing and word highlighting, line/plain/unavailable lyric fallbacks, hidden lyric work, centered scrolling, Discord lifecycle/identity/link validation and update-channel trust boundaries. Real word timing is tested with explicitly labeled fixtures, never represented as a live provider result.

## Installer and saved data

The isolated installer and uninstaller both returned exit 0. They replaced the old executable and preserved the test library byte for byte, including on uninstall. The QA identity and shortcuts were separate from the normal application. The production installer retains the previous AppId, AUMID, data folders and credential service. It recognizes the exact official 0.1.2 binary if uninstall registration is missing, cleans exact obsolete shortcuts/executable names and migrates an owned startup command.

The actual installed JOLT 0.1.2 was upgraded successfully in place. The entire library and settings were byte-for-byte identical before and after. The saved queue, current index, radio, shuffle and repeat were unchanged; normal playback position was saved on close. An additional isolated silent-install test confirmed preservation of an existing desktop-shortcut choice and removal of only the QA shortcut on uninstall. Windows registered HEX 0.2.0 and the Start-menu shortcut became HEX. The old executable and old desktop/Start shortcut were removed.

## Artwork and DPI

All supplied kit hashes match. Thirteen PNG sizes and all seven ICO entries were checked. Full alpha scans of the master and icon variants confirm an opaque inner body; transparent corners and the original antialiased edge treatment are preserved. No logo was generated or redesigned. App screenshots were rendered and inspected at 100%, 125% and 150% scale, including centered lyrics. Small official icons are retained at their supplied dimensions.

Inno Setup 7.1.1 compiled the transparent 147 × 147 small wizard art and 480 × 918 large art. Official current image areas are square 58/77/97 px for the small image at 100/125/150%, and 202 × 386 / 269 × 515 / 336 × 643 for the large image. Live interactive installer visual review at all three Windows display scales remains a manual check; native UI automation was unavailable. Application offscreen renders and successful silent installation do not substitute for that visual check.

## Live playback and Discord

Real streaming playback passed the measured scenarios in PERFORMANCE-0.2.0.md. Live synchronized lyrics were confirmed by an exact LRCLIB match in both performance modes. Four skips and four past-entry replays reached actual audio-start events. All sampled player process counts were one.

Discord's existing local IPC architecture and Application ID 1570159402856751135 are retained. Download HEX is disabled until its public installer URL verifies. Public download and accepted activity-payload checks occur after release publication and are reported in the repository's current verification document. No second-viewer button click is claimed.

Manual Developer Portal work remains: rename the application to HEX and upload the supplied 1024 × 1024 hex.png under asset key hex. The name is server-managed; keeping the existing Application ID preserves the integration. Song/art click-through URLs remain omitted. Ordinary activity privacy preferences are not changed.

The installer is unsigned. Windows security and reputation protections are not bypassed. Automatic application installation remains gated on HEX-controlled signing keys; application updates currently use the official release page manually.

## Publication verification, 11 November 2026

HEX 0.2.0 was published at https://github.com/subliminalsidkthemeaning/HEX/releases/tag/v0.2.0 . An anonymous full download of https://github.com/subliminalsidkthemeaning/HEX/releases/latest/download/HEX-Setup-x64.exe returned HTTP 200 and matched the packaged SHA-256 **563ab1a23d9faea20c371c34ad53da1eb5edfb5c9ae61d80afef30185bac3642**. The app's live public-URL verification test passed separately (1/1).

The public, uninstrumented executable received Discord's successful SET_ACTIVITY acknowledgment with matching nonce **2**. Its accepted outgoing payload includes exactly one button, **Download HEX**, pointing to that verified installer URL. Artwork, real title/artist, Listening type and timeline remain. No details_url, state_url, large_url or small_url song click-through fields are present. This verifies payload acceptance; a second-viewer click has not been performed. A separate live optimized-QA run also paused, resumed, skipped, exited through the real app callback, and received an acknowledged presence clear. The QA process exited on its own; its development instrumentation is absent from the public executable.

Across the full run and corrected/added regression runs, 1,554 unique automated cases passed, including the new manual-lyrics case and live public-URL case. The full-run/targeted-run breakdown above is retained for transparency; the remaining 85 configuration-gated/ignored cases were not claimed as passes. Installer CLI checks and real streaming/Discord checks are additional evidence.

Manual work remains the Developer Portal name/art update, a second-viewer button click, and live interactive installer artwork review at all three Windows display scales. Release binaries remain unchanged after publication; this repository document contains the post-publication checks.