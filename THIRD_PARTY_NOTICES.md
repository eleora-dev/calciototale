# Third-party notices

CalcioTotale includes original project material and uses or references third-party software, assets, names, trademarks and data. The proprietary terms in `LICENSE` apply only to material owned by Gerardo Perilli / Eleòra and do not replace any third-party licence or right.

This notice reflects the current version 1.0 beta repository and was last reviewed on 22 August 2026. It is a practical inventory, not a substitute for the complete licence texts or for legal review of a particular executable build. `BUILD_COMPONENTS.txt` records the exact principal versions used for each generated package.

---

## Original CalcioTotale material

- Material: original source code, documentation, localisation and original project assets
- Copyright: Copyright (c) 2026 Gerardo Perilli / Eleòra
- Licence: proprietary; all rights reserved
- Terms: `LICENSE`

Any bundled item that is not owned by Gerardo Perilli / Eleòra is excluded from this proprietary grant and remains subject to its own rights.

---

## Python

- Material: Python interpreter and standard library embedded in official executable builds
- Source requirement: Python 3.10 or newer
- Automated release environment: Python 3.12
- Licence: Python Software Foundation License Version 2 and the additional licences for software incorporated into the corresponding Python distribution
- Included text: `licenses/PYTHON-3.12-LICENSE.txt`
- Official project: https://www.python.org/

Python is not relicensed by CalcioTotale. The included file is the complete licence shipped for the Python 3.12 line used by the automated release workflow. A package built locally with another supported Python line must include the licence material supplied with that exact interpreter.

---

## PySide6 / Qt for Python

- Material: Python bindings and Qt libraries used by the graphical interface
- Repository location: declared in `requirements.txt`; installed as an external dependency
- Current requirement: `PySide6>=6.7,<7`
- Current automated-build channel: PySide6 Community wheels installed from PyPI
- Licensing: LGPLv3/GPLv3 for the Community distribution; separate Qt commercial licensing is available only under its own terms
- Included general texts: `licenses/LGPL-3.0.txt` and `licenses/GPL-3.0.txt`
- Official information: https://doc.qt.io/qtforpython-6/

PySide6, Shiboken6 and Qt are not relicensed by CalcioTotale. The automated pipeline's use of Community wheels means that a public build must satisfy the applicable LGPLv3/GPLv3 requirements, including the notices, licence texts, relinking or replacement rights, source-code availability obligations and third-party acknowledgements required by the exact Qt modules and wheel versions bundled. A build made under a valid Qt commercial licence must instead be produced and documented through the corresponding commercial distribution channel.

---

## PyInstaller

- Material: build system; its bootloader and loader files are embedded in executable packages
- Current build requirement: `PyInstaller==6.21.0`
- Licence: GPLv2 or later with the PyInstaller bootloader exception; runtime hooks use Apache License 2.0
- Included text: `licenses/PYINSTALLER-COPYING.txt`
- Upstream project: https://github.com/pyinstaller/pyinstaller

The bootloader exception permits PyInstaller's compiled bootloader and related files to be combined with and distributed as part of non-free applications. It does not relicense CalcioTotale or remove the terms that apply to PyInstaller itself.

---

## Pillow

- Material: image-processing dependency used by the packaging environment, including platform-icon handling
- Current build requirement: `Pillow>=10,<13`
- Runtime status: not imported by CalcioTotale and not required for source gameplay
- Licence: MIT-CMU License
- Included text: `licenses/MIT-CMU-PILLOW.txt`
- Upstream project: https://github.com/python-pillow/Pillow

Pillow is installed in the temporary build environment on Linux, Windows and macOS. It is a build-time tool rather than a declared game-runtime dependency.

---

## Google Material Symbols / Material Design icons

- Material: applicable UI icons derived or adapted from Google Material Symbols or Material Design icons
- Current format and location: applicable raster PNG assets under `assets/icons/` and its category subdirectories
- Licence: Apache License 2.0
- Included text: `licenses/APACHE-2.0.txt`
- Upstream project: https://github.com/google/material-design-icons

CalcioTotale does not relicense these icons.

---

## Exo 2

- Material: Exo 2 static Regular font
- Location: `assets/fonts/Exo2-Regular.ttf`
- Copyright: Copyright 2013 The Exo 2 Project Authors (https://github.com/googlefonts/Exo-2.0)
- Licence: SIL Open Font License 1.1
- Included text: `licenses/OFL-1.1.txt`

CalcioTotale does not relicense Exo 2.

---

## flag-icons

- Material: applicable country and territory flags derived from the `flag-icons` SVG collection
- Location: `assets/flags/*.svg`; project-specific category flags whose names begin with `_` are not represented as upstream `flag-icons` files by this notice
- Copyright: Copyright (c) 2013 Panayiotis Lipiridis
- Licence: MIT License
- Included text: `licenses/MIT-FLAG-ICONS.txt`
- Upstream project: https://github.com/lipis/flag-icons

CalcioTotale does not relicense the `flag-icons` material.

---

## Development-tool dependencies

The following direct dependencies are used only by the importer and maintenance utilities under `tools/` and are excluded from executable game builds:

- **Requests** (`requests>=2.31.0`) — Apache License 2.0; included text: `licenses/APACHE-2.0.txt`; upstream project: https://github.com/psf/requests
- **Beautiful Soup** (`beautifulsoup4>=4.12.0`) — MIT License; included text: `licenses/MIT-BEAUTIFULSOUP.txt`; upstream project: https://www.crummy.com/software/BeautifulSoup/bs4/

Their own dependencies, when installed in a development environment, remain subject to the notices and licence terms distributed by their respective packages.

---

## Football names, crests, competition marks and data

Football club, player, federation, league and competition names; crests, logos and other marks; and football data are not covered by the CalcioTotale proprietary licence unless explicitly owned or licensed by Gerardo Perilli / Eleòra. All corresponding rights remain with their respective owners.

The maintenance tools described in `tools/README.md` can consult SoccerWiki, EA SPORTS FC resources and FIFACM. Those services and names are not runtime dependencies, sponsors or partners of CalcioTotale. References to them do not imply affiliation, endorsement or permission beyond the terms granted by their respective owners.

CalcioTotale is an unofficial project and is not affiliated with, endorsed by or sponsored by any football federation, league, competition, club, player or data provider.

---

## Other bundled media

Branding, backgrounds, facility images, cursors, feature illustrations, competition icons and other media are covered by `LICENSE` only where they are original CalcioTotale material. Any third-party element remains under its original ownership, licence, terms or reserved rights even if it is stored in the repository or transformed for use by the application.
