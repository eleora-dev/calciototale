# CalcioTotale

[Versione italiana](README.md)

CalcioTotale is a local, single-player football management game centred on Italian club football. This repository distributes the **version 1.0.1 demo**, with a database updated for the **2026-27** season.

> **Languages:** the game and its interface are available in Italian and English.

> **This is the demo version of CalcioTotale.** It includes all gameplay features, but each career can continue only through the end of the first season's opening half. The full version will be available on Steam.

![Windows](https://img.shields.io/badge/Windows-x64-0078d4)
![Linux](https://img.shields.io/badge/Linux-x86__64-fcc624)
![Release](https://img.shields.io/badge/release-1.0.1%20Demo-f6a91a)
![License](https://img.shields.io/badge/license-proprietary-red)
![Offline](https://img.shields.io/badge/game-offline-41cd52)

---

![CalcioTotale](assets/branding/screenshot.png)

---

## Demo download

Official packages from [Release v1.0.1](https://github.com/eleora-dev/calciototale/releases/tag/v1.0.1) are available for:

Packages updated on **15 September 2026**.

- [Windows 10/11 x64 — portable ZIP](https://github.com/eleora-dev/calciototale/releases/download/v1.0.1/CalcioTotale-1.0.1-demo-windows-x64.zip)
- [Linux x86_64 — portable archive](https://github.com/eleora-dev/calciototale/releases/download/v1.0.1/CalcioTotale-1.0.1-demo-linux-x86_64.tar.gz)

The demo lets you start a career with all features available and play through the end of the first season's opening half. The packages are self-contained: Python and Python packages do not need to be installed. This repository distributes the demo exclusively; neither the full version nor the source code is published here.

### Integrity verification

To verify downloaded files, use [SHA256SUMS](https://github.com/eleora-dev/calciototale/releases/download/v1.0.1/SHA256SUMS).

## Full version on Steam

The full version launches on **2 October 2026**. Visit the [Calcio Totale Steam page](https://store.steampowered.com/app/5247020/Calcio_Totale/) to add it to your wishlist and purchase it on release day.

## Installation and startup

### Windows

Extract the complete ZIP into a writable folder, open the `CalcioTotale` directory and run `CalcioTotale.exe`. This is a portable build: do not run it directly from the ZIP and do not place it in `Program Files`. Saves are stored in `user/` beside the executable.

### Linux

Extract the archive and run `CalcioTotale/CalcioTotale`. The build is produced and tested on Fedora 44 and stores `user/` beside the executable.

## Operating-system security warnings

The Windows build does not yet have a code signature and may trigger a Microsoft Defender SmartScreen warning. Download packages only from this official repository and verify `SHA256SUMS` before use.

## Main features

- two career modes: *Solo la Maglia* and *Sentieri di Gloria*;
- configurable technical control: line-ups, tactics, training and match management can be directed by the player or delegated to the technical staff;
- Serie A, Serie B and all three Serie C groups, with 100 selectable Italian clubs plus 145 European and international clubs in the base database;
- Coppa Italia, Coppa Italia Serie C, Supercoppa Italiana, play-offs and play-outs;
- UEFA competitions, Intercontinental Cup and Club World Cup;
- formations, line-ups, tactics, roles, shirt numbers, training, injuries, suspensions and match reports;
- transfers, loans, negotiations, pre-contracts, scouting and youth development;
- finances, income statement and player-registration accounting, board objectives, staff, stadium and training-centre development;
- ticketing, sponsors, TV rights, press, social channels and merchandising;
- tables, calendars, statistics, awards, records and contextual news;
- nine local career slots.

## Privacy

CalcioTotale is an offline desktop game:

- no account or remote server is required;
- it does not include telemetry, analytics or advertising;
- normal gameplay does not make network requests;
- career data remains on the user's device unless the user copies or shares it.

The links in the About dialog open the default browser only when selected. See the complete bilingual [privacy policy](privacy.html) for further details.

## Licence and rights

The official build may be downloaded, installed and used for personal, non-commercial purposes under the [CalcioTotale proprietary licence](LICENSE). Redistribution, modification, publication, commercial use and attempts to derive the source code are not permitted without prior written authorisation.

Third-party components and materials, including Python, Qt/PySide6, PyInstaller, build-time Pillow, icons and fonts, remain subject to their respective licences, terms and rights. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and the [`licenses/`](licenses/) directory; each package also includes `BUILD_COMPONENTS.txt` with the principal versions actually used.

CalcioTotale is an unofficial project and is not affiliated with, endorsed by or sponsored by any football federation, league, competition, club, player or data provider.

## Author

Gerardo Perilli · [Eleòra](https://github.com/eleora-dev)
