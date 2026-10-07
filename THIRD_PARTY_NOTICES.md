# Third-party notices

CalcioTotale includes original project material and uses or references third-party software, assets, names, trademarks and data. The proprietary terms in `LICENSE` apply only to material owned by Gerardo Perilli / Eleòra and do not replace any third-party license or right.

This notice reflects the current version 1.0.5 repository and was last reviewed on 29 September 2026. It is a practical inventory, not a substitute for the complete license texts or for legal review of a particular executable build. `BUILD_COMPONENTS.txt` records the exact principal versions used for each generated package.

---

## Original CalcioTotale material

- Material: original source code, Italian, English and Spanish localisations, documentation and original project assets
- Copyright: Copyright (c) 2026 Gerardo Perilli / Eleòra
- License: proprietary; all rights reserved
- Terms: `LICENSE`

Any bundled item that is not owned by Gerardo Perilli / Eleòra is excluded from this proprietary grant and remains subject to its own rights.

---

## Python

- Material: Python interpreter and standard library embedded in official executable builds
- Source requirement: Python 3.10 or newer
- Automated release environment: Python 3.12
- License: Python Software Foundation License Version 2 and the additional licenses for software incorporated into the corresponding Python distribution
- Included text: `licenses/PYTHON-3.12-LICENSE.txt`
- Official project: https://www.python.org/

Python is not relicensed by CalcioTotale. The included file is the complete license shipped for the Python 3.12 line used by the automated release workflow. A package built locally with another supported Python line must include the license material supplied with that exact interpreter.

---

## PySide6 / Qt for Python

- Material: Python bindings and Qt libraries used by the graphical interface
- Repository location: declared in `requirements.txt`; installed as an external dependency
- Current requirement: `PySide6>=6.7,<7`
- Current automated-build channel: PySide6 Community wheels installed from PyPI
- Licensing: LGPLv3/GPLv3 for the Community distribution; separate Qt commercial licensing is available only under its own terms
- Included general texts: `licenses/LGPL-3.0.txt` and `licenses/GPL-3.0.txt`
- Official information: https://doc.qt.io/qtforpython-6/

PySide6, Shiboken6 and Qt are not relicensed by CalcioTotale. The automated pipeline's use of Community wheels means that a public build must satisfy the applicable LGPLv3/GPLv3 requirements, including the notices, license texts, relinking or replacement rights, source-code availability obligations and third-party acknowledgements required by the exact Qt modules and wheel versions bundled. A build made under a valid Qt commercial license must instead be produced and documented through the corresponding commercial distribution channel.

---

## PyInstaller

- Material: build system; its bootloader and loader files are embedded in executable packages
- Current build requirement: `PyInstaller==6.21.0`
- License: GPLv2 or later with the PyInstaller bootloader exception; runtime hooks use Apache License 2.0
- Included text: `licenses/PYINSTALLER-COPYING.txt`
- Upstream project: https://github.com/pyinstaller/pyinstaller

The bootloader exception permits PyInstaller's compiled bootloader and related files to be combined with and distributed as part of non-free applications. It does not relicense CalcioTotale or remove the terms that apply to PyInstaller itself.

---

## Pillow

- Material: image-processing dependency used by the packaging environment, including platform-icon handling
- Current build requirement: `Pillow>=10,<13`
- Runtime status: not imported by CalcioTotale and not required for source gameplay
- License: MIT-CMU License
- Included text: `licenses/MIT-CMU-PILLOW.txt`
- Upstream project: https://github.com/python-pillow/Pillow

Pillow is installed in the temporary build environment on Linux, Windows and macOS. It is a build-time tool rather than a declared game-runtime dependency.

---

## Google Material Symbols / Material Design icons

- Material: applicable UI icons derived or adapted from Google Material Symbols or Material Design icons
- Current format and location: applicable raster PNG assets under `assets/icons/` and its category subdirectories
- License: Apache License 2.0
- Included text: `licenses/APACHE-2.0.txt`
- Upstream project: https://github.com/google/material-design-icons

CalcioTotale does not relicense these icons.

---

## Red Hat Display

- Material: Red Hat Display static Regular, Medium, SemiBold, SemiBold Italic and Bold fonts, used for the interface and trailer body text
- Location: `assets/fonts/RedHatDisplay-*.ttf`
- Copyright: Copyright 2021 The Red Hat Project Authors (https://github.com/RedHatOfficial/RedHatFont)
- License: SIL Open Font License 1.1
- Included text: `licenses/OFL-RED-HAT-DISPLAY-1.1.txt`
- Upstream distribution: https://github.com/RedHatOfficial/RedHatFont/tree/6bb1048a6402b0076ea04f42951ec66263cd1437/fonts/Proportional/RedHatDisplay/ttf
- Local modification: vertical line metrics reduced slightly in the five bundled TTFs to tighten multiline text. Glyph outlines and names are unchanged.

CalcioTotale does not relicense Red Hat Display.

---

## Oxanium

- Material: Oxanium static Bold font used for shirt sponsors, and a variable font used for trailer headings
- Location: `assets/fonts/Oxanium-Bold.ttf`, `assets/fonts/Oxanium.ttf`
- Copyright: Copyright 2019 The Oxanium Project Authors (https://github.com/sevmeyer/oxanium)
- License: SIL Open Font License 1.1
- Included text: `licenses/OFL-OXANIUM-1.1.txt`
- Upstream distribution: https://github.com/sevmeyer/oxanium/tree/master/fonts

CalcioTotale does not relicense Oxanium.

---

## flag-icons

- Material: applicable country and territory flags derived from the `flag-icons` SVG collection
- Location: `assets/flags/*.svg`; project-specific category flags whose names begin with `_` are not represented as upstream `flag-icons` files by this notice
- Copyright: Copyright (c) 2013 Panayiotis Lipiridis
- License: MIT License
- Included text: `licenses/MIT-FLAG-ICONS.txt`
- Upstream project: https://github.com/lipis/flag-icons

CalcioTotale does not relicense the `flag-icons` material.

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

For the purposes of the project documentation and licensing structure, the entire `data/` directory is a replaceable football content package distributed separately from the proprietary CalcioTotale application. Its database is outside the scope of the CalcioTotale proprietary license. Fixed, generic competition illustrations are application resources under `assets/competitions/`, selected by neutral identifiers in the database.

Football club, player, federation, league and competition names, other marks and football data contained in that package are not CalcioTotale application material. All corresponding rights remain with their respective owners.

CalcioTotale is an unofficial project and is not affiliated with, endorsed by or sponsored by any football federation, league, competition, club, player or data provider.

---

## Other bundled media

The stylised map in `assets/competitions/regional_organizer.png` is derived from the public-domain Natural Earth 1:110m country boundaries, simplified for small interface sizes. Source: https://github.com/nvkelso/natural-earth-vector/blob/master/geojson/ne_110m_admin_0_countries.geojson. Terms: https://www.naturalearthdata.com/about/terms-of-use/. The surrounding artwork is original project material.

Branding, backgrounds, facility images, the animated wait cursor, feature illustrations, competition icons and other media are covered by `LICENSE` only where they are original CalcioTotale material. The four static Kenney cursors are documented separately above. Any other third-party element remains under its original ownership, license, terms or reserved rights even if it is stored in the repository or transformed for use by the application.
