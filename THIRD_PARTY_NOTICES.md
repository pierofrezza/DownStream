# DownStream — Third-Party Notices

**For DownStream 1.0.0 (build 87)**

DownStream includes and/or redistributes third-party software. Those components are not covered by the DownStream Proprietary Binary License; each remains governed by its own upstream license.

This file is a practical notice and inventory. It does not replace the complete license texts supplied by the upstream projects, and it does not alter any rights granted by those licenses.

## yt-dlp

- Version included: **2026.06.09**
- Project: https://github.com/yt-dlp/yt-dlp
- The yt-dlp project itself is released under the **Unlicense**.
- The official PyInstaller-bundled executables contain code under additional licenses; yt-dlp documents those combined executables as **GPLv3+**.
- Upstream third-party license inventory: `THIRD_PARTY_LICENSES.txt` in the yt-dlp repository/release materials.

DownStream invokes yt-dlp as a separate bundled executable.

## FFmpeg

Project: https://ffmpeg.org/

DownStream distributes two separate FFmpeg executables:

### Apple Silicon

- Version: **FFmpeg 7.1.1**
- Architecture: **arm64**
- Build enables GPL components (`--enable-gpl`).
- Effective FFmpeg license for this build: **GNU GPL v2 or later**.
- `--enable-nonfree` is **not** enabled.

### Intel

- Version: **FFmpeg 7.1.1-tessus**
- Architecture: **x86_64**
- Binary provider: https://evermeet.cx/ffmpeg/
- Build enables GPL components and version-3 licensing (`--enable-gpl`, `--enable-version3`).
- Effective FFmpeg license for this build: **GNU GPL v3 or later**.
- `--enable-nonfree` is **not** enabled.

The Universal edition contains both architecture-specific FFmpeg executables.

FFmpeg is distributed as a separate executable and may include statically linked third-party libraries whose own licenses also apply. Build configuration can be inspected with `ffmpeg -buildconf`.

## MKVToolNix / mkvmerge

- Version included: **MKVToolNix 92.0 (mkvmerge)**
- Project: https://mkvtoolnix.download/
- License: **GNU GPL v2** for MKVToolNix itself.
- Source archives: https://mkvtoolnix.download/sources/

DownStream bundles architecture-specific mkvmerge binaries together with the runtime libraries required by those binaries. Those libraries retain their own upstream licenses and are not relicensed by DownStream.

## GPAC / MP4Box

- Version included: **GPAC 26.03-DEV-rev354-g1198d06cc-HEAD**
- Project: https://gpac.io/
- License: **GNU LGPL v2.1 or later** for the included GPAC/MP4Box build.
- Build type used by DownStream: minimal, isomedia-focused command-line build.

DownStream invokes MP4Box as a separate bundled executable.

## Subler

- Version included: **Subler 1.9.4**
- Upstream tag/commit used for the custom builds: **43a768a18706f4ae91536bb669a3e5aa6e9c4a0a**
- Project: https://github.com/SublerApp/Subler
- License: **GNU GPL v2**.

DownStream includes Subler as a separate application used for specific MP4 workflows. Apple Silicon and Intel packages use architecture-specific builds; the Universal package uses a Universal Subler 1.9.4 build.

### MP42Foundation

Subler includes the **MP42Foundation** framework/submodule.

- Project: https://github.com/SublerApp/MP42Foundation
- Commit used in the custom DownStream Subler builds: **f883d07809a8a264a4f342876543ae9f5b159366**

MP42Foundation and its own bundled dependencies remain subject to their upstream licensing terms as distributed within the Subler project.

### Sparkle

Subler also embeds the **Sparkle** update framework.

- Project: https://github.com/sparkle-project/Sparkle
- Sparkle is distributed under its upstream permissive license and includes additional third-party notices in its own `LICENSE` file.

## Additional runtime libraries

The architecture-specific mkvmerge runtime folders include libraries from projects such as Boost, GLib, ICU, libEBML, libMatroska, libogg, libvorbis, FLAC, fmt, PCRE2, pugixml, zstd, Qt and related dependencies.

Each of those libraries remains governed by its own upstream license. Their presence does not place DownStream's original proprietary code under those licenses.

## No relicensing

DownStream does not claim ownership of third-party software and does not relicense it. Where a third-party license grants rights to inspect, modify, reverse engineer, replace, redistribute, or obtain source code for that component, those rights remain fully applicable to that component regardless of the DownStream Proprietary Binary License.

## Source and license availability

For public redistribution of GPL/LGPL components, the corresponding source code, build information, and complete license texts must be made available in the manner required by the applicable license.

The corresponding source materials and build information are provided in the DownStream-1.0.0-Third-Party-Source.zip asset of the DownStream 1.0.0 GitHub release.
