# Third-party notices

Calcio Totale includes original project material and uses or references third-party software, assets, names, trademarks and data. The proprietary terms in `LICENSE` apply only to material owned by Gerardo Perilli / Eleòra and do not replace any third-party license or right.

This notice reflects the current version 1.0.8 repository and was last reviewed on 17 October 2026. It is a practical inventory, not a substitute for the complete license texts or for legal review of a particular executable build. `BUILD_COMPONENTS.json` records the edition, Qt version and SHA-256 hashes of the files in each generated package.

---

## Original Calcio Totale material

- Material: original C++17 application and game-engine source code, Italian, English and Spanish localisations, documentation and original project assets
- Copyright: Copyright (c) 2026 Gerardo Perilli / Eleòra
- License: proprietary; all rights reserved
- Terms: `LICENSE`

Any bundled item that is not owned by Gerardo Perilli / Eleòra is excluded from this proprietary grant and remains subject to its own rights.

The numerical and domain library under `src/engine/` is original Calcio Totale code, except for the bundled miniz sources and the attributed MT19937/CPython-compatible random adaptations documented below. The Qt application links it directly into the native executable. Development tools and tests exercise its domain interfaces directly. CMake and the C++ compiler are development and packaging tools, not requirements for players.

---

## miniz

- Material: statically linked DEFLATE compression/decompression and CRC for compatible gzip career saves
- Version: 3.1.1, commit `d10b03cc73475af673df40f06e5cefd1d5f940d9`
- Project: https://github.com/richgel999/miniz
- License: MIT; copyright notices are retained in the vendored sources and complete license
- License text included in executable packages: `licenses/miniz-MIT.txt`
- Sources and provenance: `src/engine/third_party/miniz/`, including `SOURCE.json` with SHA-256 hashes
- ZIP archive APIs are disabled; no external zlib or runtime installation is required.

---

## MT19937 and CPython algorithm adaptations

- Material: algorithms adapted into the C++ implementation
- MT19937 initialization/state transitions: Makoto Matsumoto and Takuji Nishimura; BSD terms in `licenses/MT19937-BSD.txt`
- CPython-derived sampling and compatible numerical adaptations: Python Software Foundation; retained PSF and incorporated notices in `licenses/PYTHON-3.12-LICENSE.txt`
- Native implementations: `src/engine/domain/core/random.*` and the compensated summation in `src/engine/domain/core/owned_player.hpp`
- Upstream references: CPython `Modules/_randommodule.c`, `Lib/random.py` and `Modules/mathmodule.c`

The career generator owns its state, seed expansion, draw order, sampling and saved-state format. The adapted algorithms retain the BSD and PSF notices listed above.

---

## Unicode character data

- Material: derived Unicode 16.0.0 normalization, case mapping and decimal digit data in `src/engine/domain/core/model_catalog.inc`
- Generation source: Unicode 16.0.0 character data, stored as fixed tables
- Copyright: © 1991-2026 Unicode, Inc.
- License: Unicode License V3, reproduced in `licenses/UNICODE-LICENSE-V3.txt`
- Source and terms: https://www.unicode.org/ and https://www.unicode.org/license.txt

The compiled catalog supplies Unicode rules to the model factories. The Unicode data retains its own license. Model schemas, game defaults, translations and C++ normalization logic are original Calcio Totale material.

## Qt native libraries and image codecs

- Material: dynamically linked Qt Core, Gui, Widgets and Svg, plus the deployment-selected Network and Image Formats libraries/plugins
- Copyright: The Qt Company Ltd. and the respective Qt contributors
- Native automated build version: Qt 6.11.2; the application requires a compatible Qt 6 SDK with Widgets, Svg and WebP support
- Licensing: Qt Community LGPLv3/GPLv3, as applicable to each module; separate commercial terms apply only to a build produced under a corresponding Qt commercial license
- General texts: `licenses/LGPL-3.0.txt` and `licenses/GPL-3.0.txt`
- Upstream module license texts, third-party attributions and provenance: `licenses/qt/6.11.2/`
- Official information: https://doc.qt.io/qt-6.11/licensing.html
- Official source modules: https://github.com/qt/qtbase/tree/v6.11.2, https://github.com/qt/qtsvg/tree/v6.11.2 and https://github.com/qt/qtimageformats/tree/v6.11.2

Qt and its codecs retain their upstream terms. The Image Formats module supplies WebP support for the original backgrounds and other WebP images; its libwebp notices are included in the Qt collection. That collection also preserves the upstream attributions for optional components: the exact set shipped depends on platform and Qt configuration. The package manifest identifies the actual library/plugin files. Builds using another Qt version must refresh the corresponding upstream collection.

Qt Community builds retain the applicable replacement/relinking rights, source availability obligations and third-party acknowledgements for the bundled Qt modules. The original Calcio Totale code remains proprietary.

Linux packages deploying the Qt OpenSSL TLS backend also bundle the unmodified OpenSSL 3 `libssl` and `libcrypto` libraries for HTTPS diagnostic submissions. Copyright (c) 1998-2026 The OpenSSL Project Authors; Copyright (c) 1995-1998 Eric A. Young, Tim J. Hudson. OpenSSL uses the Apache License 2.0, included in `licenses/APACHE-2.0.txt`. Upstream: https://openssl-library.org/.

---

## Microsoft Visual C++ runtime (Windows only)

- Material: Microsoft C++ redistributable x64 DLLs shipped alongside the native executable, and the Microsoft-supplied `vc_redist.x64.exe` where included
- Source: the Visual Studio build tools' redistributable directory; the portable test package uses runtime 14.44.35211.0 from its included Microsoft installer
- Copyright and license: Microsoft Corporation; Microsoft Software License Terms, retained in the included installer and `licenses/MICROSOFT-VISUAL-C-RUNTIME.rtf`
- Official redistribution information: https://learn.microsoft.com/cpp/windows/redistributing-visual-cpp-files

These are Microsoft runtime components, not original Calcio Totale code. Their inclusion provides the C++ runtime required by the application and Qt on Windows. Linux and macOS packages do not require or ship the Windows runtime DLLs.

---

## Google Material Symbols / Material Design icons

- Material: applicable UI icons derived or adapted from Google Material Symbols or Material Design icons
- Current format and location: applicable raster PNG assets under `assets/icons/` and its category subdirectories
- License: Apache License 2.0
- Included text: `licenses/APACHE-2.0.txt`
- Upstream project: https://github.com/google/material-design-icons

Calcio Totale does not relicense these icons.

---

## Red Hat Display

- Material: Red Hat Display static Regular, Medium, SemiBold, SemiBold Italic and Bold fonts, used for the interface and trailer body text
- Location: `assets/fonts/RedHatDisplay-*.ttf`
- Copyright: Copyright 2021 The Red Hat Project Authors (https://github.com/RedHatOfficial/RedHatFont)
- License: SIL Open Font License 1.1
- Included text: `licenses/OFL-RED-HAT-DISPLAY-1.1.txt`
- Upstream distribution: https://github.com/RedHatOfficial/RedHatFont/tree/6bb1048a6402b0076ea04f42951ec66263cd1437/fonts/Proportional/RedHatDisplay/ttf
- Local modification: vertical line metrics reduced slightly in the five bundled TTFs to tighten multiline text. Glyph outlines and names are unchanged.

Calcio Totale does not relicense Red Hat Display.

---

## Oxanium

- Material: Oxanium static Bold font used for shirt sponsors, and a variable font used for trailer headings
- Location: `assets/fonts/Oxanium-Bold.ttf`, `assets/fonts/Oxanium.ttf`
- Copyright: Copyright 2019 The Oxanium Project Authors (https://github.com/sevmeyer/oxanium)
- License: SIL Open Font License 1.1
- Included text: `licenses/OFL-OXANIUM-1.1.txt`
- Upstream distribution: https://github.com/sevmeyer/oxanium/tree/master/fonts

Calcio Totale does not relicense Oxanium.

---

## flag-icons

- Material: applicable country and territory flags derived from the `flag-icons` SVG collection
- Location: `assets/flags/*.svg`; project-specific category flags whose names begin with `_` are not represented as upstream `flag-icons` files by this notice
- Copyright: Copyright (c) 2013 Panayiotis Lipiridis
- License: MIT License
- Included text: `licenses/MIT-FLAG-ICONS.txt`
- Upstream project: https://github.com/lipis/flag-icons

Calcio Totale does not relicense the `flag-icons` material.

The language-selector PNG files `assets/icons/menu/language_it.png` and `assets/icons/menu/language_en.png` are project-provided UI assets and are not identified as upstream `flag-icons` material by this notice. They are covered by the proprietary project license only to the extent that they are original material owned by Gerardo Perilli / Eleòra; any third-party element remains subject to its original rights.

---

## Kenney Cursor Pack

- Material: four static UI cursors from the Kenney Cursor Pack
- Upstream files: `pointer_a.png`, `hand_thin_small_point.png`, `cursor_help.png` and `bracket_a_vertical.png` from `PNG/Outline/Default`
- Repository locations: `assets/cursors/arrow.png`, `assets/cursors/hand.png`, `assets/cursors/help.png` and `assets/cursors/ibeam.png`
- License: Creative Commons CC0 1.0 Universal
- Included notice: `licenses/CC0-KENNEY-CURSOR-PACK.txt`
- Official project: https://kenney.nl/assets/cursor-pack

These four files may be used, modified and redistributed without attribution under CC0. The source and mapping are retained in the included notice for provenance.

---

## Separate football content package

For the purposes of the project documentation and licensing structure, the entire `data/` directory is a replaceable football content package distributed separately from the proprietary Calcio Totale application. Its database is outside the scope of the Calcio Totale proprietary license. Fixed, generic competition illustrations are application resources under `assets/competitions/`, selected by neutral identifiers in the database.

Football club, player, federation, league and competition names, other marks and football data contained in that package are not Calcio Totale application material. All corresponding rights remain with their respective owners.

Calcio Totale is an unofficial project and is not affiliated with, endorsed by or sponsored by any football federation, league, competition, club, player or data provider.

---

## Other bundled media

The stylised map in `assets/competitions/regional_organizer.png` is derived from the public-domain Natural Earth 1:110m country boundaries, simplified for small interface sizes. Source: https://github.com/nvkelso/natural-earth-vector/blob/master/geojson/ne_110m_admin_0_countries.geojson. Terms: https://www.naturalearthdata.com/about/terms-of-use/. The surrounding artwork is original project material.

Branding, backgrounds, facility images, the animated wait cursor, feature illustrations, competition icons and other media are covered by `LICENSE` only where they are original Calcio Totale material. The four static Kenney cursors are documented separately above. Any other third-party element remains under its original ownership, license, terms or reserved rights even if it is stored in the repository or transformed for use by the application.

---

## Development tools (not distributed with the game)

Native build orchestration, archives, Qt SDK installation, Qt attribution updates, database tools, importing and automated test logic are implemented in C++. Packaging tools invoke CMake, curl and platform deployment utilities. Qt Network also handles optional, user-requested diagnostic submissions to Sentry. The development-only database tools additionally use libxml2; those tools are not included in game packages. The PSF notice under `licenses/` remains because adapted C++ algorithms use it.

The development-only `ct_publish` tool uses Qt Gui to draw localized trailer
frames and invokes separately installed ImageMagick, CMake and GStreamer tools
for artwork export, ZIP archives and H.264/AAC MP4 encoding. These external
programs and codecs are not bundled with the game. Existing artwork, fonts and
music retain the terms documented in this inventory and the media credits.
