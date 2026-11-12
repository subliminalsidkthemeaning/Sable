# Sable 0.3.0 performance

Measured on Windows x64 with 12 logical processors, using the same actual Get Lucky recording (4D7u5KF7SP8), muted streaming, isolated guest profiles and matching saved metadata. Each result is 30 samples over approximately 31 seconds after audio-clock advancement and an eight-second warm-up. Builds, tests and other test players were stopped. Default client geometry was 1280×800; software rendering was retained.

Memory figures are MiB (1,048,576 bytes). CPU is process CPU time normalized across all 12 logical processors, comparable to total machine CPU percentage. Working set is OS residency; private bytes are committed private memory. These are individual observations, not statistical guarantees or proof of an optimization.

| Workload | HEX 0.2 WS | Sable WS | HEX private | Sable private | HEX CPU % | Sable CPU % |
|---|---:|---:|---:|---:|---:|---:|
| Tray hidden · Performance ON | 70.0 | 69.2 | 22.1 | 22.4 | 0.111 | 0.116 |
| Tray hidden · Performance OFF | 59.8 | 60.2 | 21.6 | 22.8 | 0.137 | 0.133 |
| Home visible · Performance ON | 69.3 | 67.2 | 29.7 | 27.7 | 0.100 | 0.120 |
| Home visible / smooth progress · Performance OFF | 68.1 | 68.5 | 27.8 | 29.6 | 0.099 | 0.579 |
| Synchronized lyrics · Performance ON | 75.4 | 75.9 | 36.2 | 36.5 | 0.218 | 0.137 |
| Synchronized lyrics / smooth progress · Performance OFF | 80.4 | 80.9 | 41.0 | 40.8 | 0.472 | 0.999 |
| Tray hidden / Discord enabled (client absent) | 60.6 | 60.2 | 22.3 | 22.3 | 0.108 | 0.120 |
| Repeated skipping and history replay · Performance OFF | 73.6 | 72.1 | 33.7 | 32.2 | 0.748 | 1.018 |
| Now Playing / breathing · Performance OFF | 70.6 | 69.7 | 30.7 | 29.9 | 0.319 | 0.897 |
| Now Playing / static · Performance ON | 69.4 | 70.8 | 29.4 | 31.8 | 0.095 | 0.108 |
| Windows minimized · Performance ON | 63.7 | 63.1 | 24.0 | 23.5 | 0.108 | 0.116 |
| Windows minimized · Performance OFF | 65.6 | 64.1 | 25.5 | 23.5 | 0.108 | 0.091 |

| Additional Sable workload | Working set MiB | Private MiB | CPU % |
|---|---:|---:|---:|
| Now Playing paused · Performance OFF | 71.0 | 30.6 | 0.000 |
| Now Playing minimized · Performance OFF | 64.9 | 25.1 | 0.116 |
| Explore paused / idle · Performance ON | 69.5 | 31.2 | 0.000 |
| Explore playing · Performance OFF | 67.8 | 28.5 | 0.228 |
| Explore minimized · Performance OFF | 64.8 | 24.6 | 0.103 |

Every sampling window observed one application process. Counts were sampled once per second and do not rule out short-lived existing resolver fallbacks between samples. No permanent browser, bot or server was added.

Visible smooth progress and breathing have a measurable CPU cost: Home increased by approximately 0.48 percentage points and full Now Playing by 0.58 points in these runs. Minimized playback remained near 0.1% total CPU. Paused cases recorded no CPU-counter increase at the available counter resolution; this does not guarantee zero CPU usage. Background working set with Performance Mode OFF was 59.8 MiB for the public 0.2 release and 60.2 MiB for Sable under these matched conditions.

The min-on/min-off and rpc-on cases start hidden in the tray through the existing --minimized option. Separate window-min cases use actual Windows minimization. Basic Home/tray/RPC comparisons use the unmodified public executables. Lyrics, queue, Now Playing and native minimized comparisons use retained instrumented reference builds, not the unmodified public executables. The Discord client was absent: enabled/disconnected overhead was measured, while connected-client performance and a real button acknowledgment remain unverified.

Initial lyrics samples with an unsupported baseline QA command were excluded and rerun without seeking on both builds. Two Explore setup samples were also excluded and rerun. All 29 final samples passed audio-clock and applicable QA-step validation. Genuine source-provided line synchronization was present in the lyrics workloads; no synthetic word timing was used.

Executable SHA256 identities:

- 0.2.0 public: B6B27D5AB2EDD99555F033D3C8FF77E13AF2CA24E8BABC80DCDBA2279EDC0E2A
- 0.2.0 instrumented reference: 7389CD289FEAA4057BD1FF7E33612B6C4FB4A0B9A04FEB940AA22D7B88314708
- 0.3.0 public: F2D77961F594A69311D90A64EA6B4A978A4A9F1FCE0CA002D7793D009401C032
- 0.3.0 instrumented reference: EFBCEC70B2B4DBDCB78F39C662F94708CA8D7B96169A1BDA899C669F8BC28DA9

Reproduction: scripts/Benchmark-SableMatrix.ps1. Raw profiles and logs remain private and are not distributed.
