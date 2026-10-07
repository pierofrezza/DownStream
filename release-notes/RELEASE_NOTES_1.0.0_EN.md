# DownStream 1.0.0

**7 October 2026 · build 87 · macOS 15 Sequoia or later · Apple Silicon and Intel**

DownStream 1.0.0 is the first public release of the macOS interface that evolved from the previous StreamDownloader workflow.

The goal of 1.0 is to bring HLS analysis, track selection, subtitles, profiles, queue management, retries, and final muxing into a single application while preserving manual control where useful and automating repetitive work.

## Analysis and track selection

DownStream can analyze URLs and HLS/M3U8 playlists and present the available variants in a readable interface.

A job can be configured with:

- a video variant;
- one or more audio tracks where supported by the source;
- HLS subtitles;
- a final container and compatible mux options.

## HLS subtitles

Subtitle handling distinguishes separate renditions even when they share the same language.

When the relevant metadata is present, DownStream can present separately:

- normal subtitles;
- forced subtitles;
- SDH subtitles;
- tracks without an explicit classification.

SRT downloads use distinct filenames to avoid collisions between tracks in the same language.

## MP4, MKV, and TS

DownStream supports several export paths:

- **MP4**;
- **MKV**;
- **TS**, when the original source exposes it and the selected workflow is compatible.

For older TS-based sources, DownStream can perform remux/normalization without re-encoding when needed to improve final-file compatibility.

## External audio and muxing

Workflows are available for adding or replacing external audio while retaining control over the final set of tracks.

Depending on the container and configuration, DownStream can use FFmpeg, MP4Box, mkvmerge, or Subler to complete the output file.

## Profiles

Configurations can be saved and reused as profiles.

Temporary profiles are also supported, allowing a configuration to be applied without replacing the current permanent profile.

## Queue, simultaneous downloads, and activity control

Version 1.0 includes a job queue with:

- multiple ready/configurable jobs;
- configurable simultaneous downloads;
- pause and resume;
- stop and skip controls;
- automatic retries;
- job history;
- optional detailed logs.

Progress remains monotonic during recovery operations so reprocessed HLS fragments do not make the visible progress appear to move backwards.

## HLS recovery

The 1.0 engine includes a dedicated verification and recovery path for problematic HLS fragments.

When required, it can perform targeted retries and rebuild the result without needlessly restarting the whole download, while keeping the activity summary readable in the interface/log.

## Compatibility and distribution

DownStream 1.0.0 requires:

- **macOS 15 Sequoia or later**;
- an **Apple Silicon** or **Intel** Mac.

Three builds are distributed:

- Apple Silicon;
- Intel;
- Universal.

The Universal build contains both architectures and is recommended when the Mac architecture is unknown.

## Release verification

Build 87 is the final functional baseline for version 1.0.0.

Final QA covered the main single/multiple-download flows, queue operation, simultaneous downloads, pause/resume, retries, profiles, subtitles, MP4Box, Subler, MKV, and TS, together with the three distributed architecture configurations.

The applications are signed with Apple Developer ID, use Hardened Runtime, and are notarized by Apple. All three DMGs are also signed, notarized, stapled, and accepted by Gatekeeper.

Final SHA-256 checksums:

```text
e3c469027782488f8254526cf87db0f9b6bf9d820245248a26bcb3c08fd35bec  DownStream-1.0.0-Apple-Silicon.dmg
c6ed57242244ca5d37a69318f51568ee03f9fe29fa0482ec8fe233f6cfba32e0  DownStream-1.0.0-Intel.dmg
1e741ffacf178bac679429174bf85ff240bc0f8cc010dd5917553a27c68a2b1a  DownStream-1.0.0-Universal.dmg
```

## Third-party components

DownStream redistributes separate open-source tools including yt-dlp, FFmpeg, MKVToolNix/mkvmerge, GPAC/MP4Box, and Subler.

Those components remain governed by their respective licenses. See `THIRD_PARTY_NOTICES.md` and the source-compliance materials published with the release.

## Responsible use

Use DownStream only with content that you are authorized to download, copy, or process. It is not designed to circumvent DRM or other technical protection measures.
