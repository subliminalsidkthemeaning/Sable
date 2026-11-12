# HEX 0.2.0 measured performance

Measured 11 November 2026 on this Windows x64 machine with 12 logical processors. Each row uses 30 process samples over approximately 32.5 seconds, after playback starts and a further 15-second warmup. CPU is process CPU time divided by elapsed time and all 12 logical processors. Memory units are MiB (1,048,576 bytes). Process counts cover the player and its descendants; the ordinary Discord client and other existing applications are separate.

The old and new executables stream the same Get Lucky recording, muted, with matching quality and isolated copies of the same starting profile. Compilers and tests were finished during measurement. Two minimized samples that were opened during observation were discarded and repeated. No temporary browser or server was added for these measurements. First-run helper preparation is outside the steady-state sampling window.

## Public, uninstrumented executables

| Scenario | Working set MiB | Private bytes MiB | CPU, whole machine | Processes | Sample s |
|---|---:|---:|---:|---:|---:|
| JOLT 0.1.2, minimized, Performance ON, Discord OFF | 59.67 | 23.22 | 0.097% | 1–1 | 32.31 |
| HEX, minimized, Performance ON, Discord OFF | 59.32 | 22.59 | 0.128% | 1–1 | 32.47 |
| HEX, minimized, Performance OFF, Discord OFF | 58.24 | 19.74 | 0.133% | 1–1 | 32.33 |
| HEX, minimized, Performance ON, Discord ON | 58.89 | 20.26 | 0.116% | 1–1 | 32.45 |
| HEX, normal player visible, Performance ON | 67.18 | 27.78 | 0.128% | 1–1 | 32.60 |
| HEX, normal player visible, Performance OFF; smooth progress | 70.24 | 30.44 | 0.136% | 1–1 | 32.53 |

The comparable minimized Performance ON samples are 59.67 MiB working set / 23.22 MiB private bytes for JOLT and 59.32 / 22.59 MiB for HEX. Observed CPU was 0.097% and 0.128%, respectively. These are single observational samples on a live desktop, with network and cache variability; they do not establish a statistically significant optimization. The earlier Task Manager figure of about 39.7 MB was a separate observation and is not substituted for these measurements.

## Optimized QA build with development instrumentation

| Scenario | Working set MiB | Private bytes MiB | CPU, whole machine | Processes | Sample s |
|---|---:|---:|---:|---:|---:|
| HEX QA, real synchronized lyrics visible, Performance ON | 76.30 | 36.80 | 0.136% | 1–1 | 32.47 |
| HEX QA, real synchronized lyrics visible, Performance OFF | 77.12 | 37.34 | 0.717% | 1–1 | 32.50 |
| HEX QA, repeated skips/history replay, Performance OFF, Discord ON | 76.54 | 36.71 | 1.059% | 1–1 | 32.45 |

The QA-only perf-harness feature invokes the real app callbacks and records events/frames/allocations. It is absent from the public executable. These rows therefore describe an instrumented optimized build, not exact shipped-binary costs. Lyrics used a live catalog album recording and LRCLIB reported an exact synchronized match in both modes. The data was line-timed; no live word-timed result is claimed. Separate live runs also exercised the genuine plain-lyrics fallback. The queue run completed four next-track operations and four historical-entry replays, confirmed by actual audio-start events, without a permanent child process.

The public executable SHA-256 is **b6b27d5ab2edd99555f033d3c8ff77e13af2ca24e8babc80dcdba2279edc0e2a**. The QA executable SHA-256 is **7389cd289feaa4057bd1ff7e33612b6c4fb4a0b9a04feb940aa22d7b88314708**. These checks preserve the native Rust/Slint architecture; they are not a long-duration leak test or a measurement on every Windows machine.
