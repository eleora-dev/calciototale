# Build macOS

La procedura crea un bundle autonomo `CalcioTotale.app` e lo distribuisce in uno ZIP che conserva correttamente struttura, collegamenti simbolici e metadati macOS. L'utente finale non deve installare Python, PySide6 o altri pacchetti.

La versione minima dichiarata è **macOS 13**. Sono previste build separate per:

- Apple Silicon: `arm64`;
- Mac Intel: `x86_64`;
- Universal 2: `universal2`, soltanto quando Python e tutte le dipendenze contengono entrambe le architetture.

Per le Release ufficiali sono preferibili i due pacchetti nativi separati: riducono dimensioni e rendono esplicita l'architettura collaudata.

## Requisiti della macchina di build

- macOS 13 o successivo;
- Python 3.10 o successivo, a 64 bit e dell'architettura da produrre;
- Xcode Command Line Tools;
- CMake 3.20 o successivo e Apple Clang con supporto C++17;
- accesso a PyPI durante la build pulita;
- per la distribuzione pubblica, certificato **Developer ID Application** e credenziali del servizio notarile Apple.

La venv temporanea usa PyInstaller 6.21 e Pillow 10–12. Pillow serve soltanto alla preparazione del pacchetto e delle icone: il gioco non lo importa a runtime.

PyInstaller non genera una build macOS valida da Windows o Linux: la procedura deve essere eseguita su un Mac o su un runner GitHub Actions macOS.

## Build locale

Sul Mac, dalla root del progetto:

```bash
./packaging/macos/build.sh
```

Lo script compila il motore C++17 per l'architettura scelta e per la versione minima macOS dichiarata, poi include `libct_engine.dylib` in `native/` nel bundle. L'utente finale non deve installare CMake o un compilatore.

La build usa l'architettura nativa. È possibile richiederla esplicitamente:

```bash
./packaging/macos/build.sh --architecture arm64
./packaging/macos/build.sh --architecture x86_64
```

L'edizione si sceglie soltanto al momento del packaging:

```bash
./packaging/macos/build.sh --edition full
./packaging/macos/build.sh --edition demo
./packaging/macos/build.sh --edition both
```

Senza `--edition` viene creato soltanto il bundle completo; la demo usa il
suffisso `-demo`.

La build Universal 2 è disponibile soltanto con una distribuzione Python e wheel PySide6 Universal 2:

```bash
./packaging/macos/build.sh --architecture universal2
```

Gli artefatti vengono scritti in `dist/macos/`:

```text
CalcioTotale-1.0.7-macOS-arm64.zip
CalcioTotale-1.0.7-macOS-x86_64.zip
SHA256SUMS
```

Senza un'identità Developer ID, PyInstaller applica una firma ad hoc adatta soltanto al collaudo locale. Lo script produce comunque lo ZIP, ma lo segnala esplicitamente come non pubblicabile.

## Firma Developer ID

Il certificato deve essere presente nel Portachiavi della macchina di build. Individuare il nome completo con:

```bash
security find-identity -v -p codesigning
```

Avviare quindi la build impostando l'identità:

```bash
CALCIOTOTALE_CODESIGN_IDENTITY='Developer ID Application: NOME (TEAMID)' \
    ./packaging/macos/build.sh --architecture arm64
```

PyInstaller firma l'eseguibile, le librerie raccolte e il bundle con hardened runtime. Al termine lo script verifica l'intera firma con `codesign --verify`.

## Notarizzazione

Creare una sola volta un profilo `notarytool` nel Portachiavi:

```bash
xcrun notarytool store-credentials calciototale-notary \
    --apple-id 'APPLE_ID' \
    --team-id 'TEAM_ID' \
    --password 'PASSWORD_SPECIFICA_PER_APP'
```

Per firmare, inviare ad Apple, attendere l'esito e incorporare il ticket nel bundle:

```bash
CALCIOTOTALE_CODESIGN_IDENTITY='Developer ID Application: NOME (TEAMID)' \
CALCIOTOTALE_NOTARY_PROFILE='calciototale-notary' \
    ./packaging/macos/build.sh --architecture arm64
```

Lo script esegue `notarytool`, `stapler`, una seconda verifica `codesign`, la valutazione Gatekeeper con `spctl` e ricrea lo ZIP dopo l'inserimento del ticket.

Le credenziali, il certificato e la relativa password non devono mai essere salvati nel repository. In GitHub Actions vanno importati da secret cifrati in un Portachiavi temporaneo del job.

## Installazione e salvataggi

L'utente estrae lo ZIP e trascina `CalcioTotale.app` in `Applicazioni`. I salvataggi non vengono scritti nel bundle, ma nella directory dati standard dell'utente:

```text
~/Library/Application Support/CalcioTotale/user/
```

Questo permette di aggiornare o sostituire l'app senza perdere le carriere.

## Collaudo prima della distribuzione

1. verificare `shasum -a 256 -c SHA256SUMS`;
2. avviare l'app con doppio clic da Finder, non soltanto dal Terminale;
3. verificare `codesign --verify --deep --strict --verbose=2 CalcioTotale.app`;
4. verificare `spctl --assess --type execute --verbose=2 CalcioTotale.app`;
5. provare scaling Retina, fullscreen, barra dei menu, Dock e un display 16:10;
6. creare una carriera, salvare, chiudere e ricaricare;
7. verificare icone, magliette delle squadre, font, cursori e collegamenti esterni;
8. verificare nel bundle `README.md`, `README.it.md`, `README.es.md`, `LICENSE`, `THIRD_PARTY_NOTICES.md`, `privacy.html`, `licenses/` e `BUILD_COMPONENTS.txt`;
9. confrontare le versioni in `BUILD_COMPONENTS.txt` con `THIRD_PARTY_NOTICES.md` e completare gli obblighi applicabili della distribuzione PySide6/Qt Community;
10. collaudare ogni architettura su hardware reale corrispondente.

La pipeline predefinita usa PySide6/Qt Community; un'eventuale build sotto licenza commerciale Qt richiede dipendenze, credenziali e documentazione dedicate.
