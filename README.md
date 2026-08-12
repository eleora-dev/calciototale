# CalcioTotale

CalcioTotale is a local, single-player football management game centred on Italian club football. It is built with Python and PySide6 and is currently at version **1.0**, with a **2025-26** base database.

![Fedora](https://img.shields.io/badge/reference-Fedora-blue)
![License](https://img.shields.io/badge/license-proprietary-red)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![PySide6](https://img.shields.io/badge/UI-PySide6-41cd52)
![Game](https://img.shields.io/badge/game-football%20manager-f6a91a)

---

![CalcioTotale](assets/branding/screenshot.png)

---

## Current game

- **Two career modes** — *Solo la Maglia* keeps the player at one club, while *Sentieri di Gloria* follows a director's career from lower divisions through offers, evaluations and possible dismissals.
- **Five playable leagues** — Serie A, Serie B and all three Serie C groups, with 100 selectable Italian clubs plus 121 non-selectable European and world-pool clubs in the base database.
- **Domestic football** — league seasons, Coppa Italia, Coppa Italia Serie C, Supercoppa Italiana, Serie B play-offs/play-outs and Serie C post-season.
- **International competitions** — UEFA Champions League, Europa League, Conference League, UEFA Super Cup, Intercontinental Cup and Club World Cup, with qualification and season-to-season progression.
- **Squad and match management** — formations, line-ups, tactics, shirt numbers, player roles, match preparation, weekly training, injuries, suspensions and match reports.
- **Club management** — board objectives and reports, finances, contracts, prizes, credit, recapitalisation, staff, stadium and training-centre development.
- **Transfers and scouting** — purchases, sales, loans, negotiations, pre-contracts, outgoing lists, observed players and youth scouting.
- **Commercial management** — ticketing and season tickets, sponsors, TV rights, press and official communication, social channels and merchandising.
- **Youth and development** — academy prospects, promotion paths, technical growth, personalities and individual treatment.
- **Statistics and news** — tables, calendars, competition filters, player and team reports, awards, records and contextual news.
- **Local saves** — nine career slots stored in the local `saves/` directory; portable executable builds keep it beside the executable, while system packages use the user's data directory.
- **Italian interface** — generic player-facing prose is maintained in `locales/locale_it.py`; competition names and organisers are data-driven.

## Runtime and privacy

CalcioTotale is an offline desktop game:

- it does not require an account or a remote server;
- it does not use telemetry, analytics or advertising services;
- normal gameplay does not make network requests;
- career data remains on the user's device unless the user copies or shares it.

The links in the About dialog open the user's default browser only when selected; any resulting connection is made by that browser to the linked website, not by the game runtime.

Each occupied slot uses a gzip-compressed JSON payload named `saves/slotN.json.gz` and may use a small plain-JSON summary named `saves/slotN.meta.json`. In a portable executable build, `saves/` is resolved beside the executable instead of from the process working directory. The Fedora RPM stores it in `${XDG_DATA_HOME:-$HOME/.local/share}/calciototale/saves/`. The application may also generate replaceable raster caches in the operating system's temporary directory. During startup it creates a short-lived `calciototale-display-*.json` probe there with the primary display geometry and scaling factor, then removes it; this file contains no career or profile data.

The importer and maintenance utilities in `tools/` are separate development tools. Some of them access third-party websites, but they are never invoked by the game at runtime.

See [privacy.html](privacy.html) for the complete bilingual privacy policy.

## Technical overview

- `data/data.json.gz` contains the version 1.0, 2025-26 base database as gzip-compressed UTF-8 JSON, including competition names, short names, organisers and icon paths.
- `data/competitions/` contains every competition image referenced by that database; `data/teams/` contains club badges.
- `catalogs/` contains database I/O, static-record schemas and access to the replaceable game catalogues.
- `models/` defines clubs, players, staff, matches, standings, facilities, economic data and the season-objective policy.
- `engine/` contains world construction, match simulation, calendars, competitions, transfers, contracts, finance, news, training and season progression.
- `ui/` contains the PySide6 interface, dialogs, styling and presentation logic.
- `locales/locale_it.py` is the single catalogue for the Italian interface.
- `assets/` contains local branding, backgrounds, interface icons, flags, fonts and other non-competition visual resources.
- `saves/` is created at runtime for local save slots and their summaries.

The reference environment is Fedora Linux with KDE Plasma. The source also contains display handling for Windows, but only official builds explicitly published for a platform should be considered supported.

## Requirements for the source version

- Python 3.10 or newer
- PySide6 6.7 or newer, below version 7
- a working graphical desktop environment
- a display of at least 1280 × 720 for the fixed 1600 × 900 game surface and its automatic cross-platform scaling

For an authorised development copy:

```bash
python3 -B -m venv .venv
source .venv/bin/activate
python3 -B -m pip install -r requirements.txt
python3 -B calciototale.py
```

## Distribution

The source repository is private. Public distribution, when available, is limited to official executable builds published through an Eleòra channel.

Official executable builds may be downloaded, installed and used only for personal, non-commercial purposes under [LICENSE](LICENSE). Source access, redistribution, modification, publication and commercial use require prior written authorisation. Do not redistribute builds or rely on unofficial mirrors.

The Windows x64 portable-build procedure is documented in [packaging/windows/README.md](packaging/windows/README.md). Linux x86_64 portable and Fedora RPM builds are documented in [packaging/linux/README.md](packaging/linux/README.md). Both create an autonomous payload containing Python, PySide6/Qt and all runtime resources; the end user does not install Python packages.

## Project structure

```text
assets/                   Branding, backgrounds, icons, flags, fonts and UI media
catalogs/                 Static database I/O, schemas, configuration and catalogue access
data/                     Replaceable base database and competition/team images
engine/                   World construction, simulation and game-state logic
licenses/                 Included third-party licence texts
locales/                  Italian localisation catalogue
models/                   Domain models, identifiers, policies and constants
packaging/windows/        PyInstaller recipe and PowerShell build script
packaging/linux/          Shared Linux payload, portable archive and Fedora RPM
tools/                    Tests, database importer and maintenance utilities
ui/                       PySide6 interface, palette and styling
calciototale.py           Application entry point
LICENSE                   CalcioTotale proprietary licence
THIRD_PARTY_NOTICES.md    Third-party components, assets and rights
privacy.html              English and Italian privacy policy
saves/                    Runtime save directory, created when needed
```

## Internal development

These instructions apply only to authorised collaborators with access to the private source:

```bash
# Syntax check without bytecode files
python3 -B - <<'PY'
import ast
from pathlib import Path

for path in Path('.').rglob('*.py'):
    if '__pycache__' not in path.parts:
        ast.parse(path.read_text(encoding='utf-8'), filename=str(path))
PY

# Complete technical test suite
PYTHONPATH=. python3 -B -m unittest discover -s tools -p 'test_*.py'
```

`tools/` has its own [README](tools/README.md) and dependency list. Every distributed build must include `LICENSE`, `THIRD_PARTY_NOTICES.md` and the applicable files from `licenses/`; a build that bundles Qt/PySide must also comply with the specific Qt licensing option used for that build.

## Licence and third-party rights

Original CalcioTotale code, documentation and original project assets are proprietary and all rights are reserved. See [LICENSE](LICENSE).

Third-party components and materials remain under their own licences, terms and rights. The current repository specifically documents:

- **PySide6 / Qt for Python** — LGPLv3/GPLv3 or Qt commercial licensing, depending on the distribution option used;
- **Google Material Symbols / Material Design icons** — Apache License 2.0 for applicable derived icons;
- **Exo 2** — SIL Open Font License 1.1;
- **flag-icons** — MIT License for applicable country and territory SVG flags;
- **football names, badges, logos, trademarks and data** — rights remain with their respective owners.

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and the [`licenses/`](licenses/) directory. CalcioTotale is unofficial and is not affiliated with, endorsed by or sponsored by any football federation, league, competition, club, player or data provider.

## Author

Gerardo Perilli · [Eleòra](https://github.com/eleora-dev)
