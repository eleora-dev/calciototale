# Build Linux e Fedora

La procedura usa un'unica build PyInstaller `onedir` e produce due formati:

- `CalcioTotale-1.0.7-linux-x86_64.tar.gz`: archivio portabile per Linux;
- `calciototale-1.0.7-1.fc*.x86_64.rpm`: pacchetto Fedora con launcher, icona e voce nel menu applicazioni.

Il payload autonomo contiene Python, PySide6/Qt, la libreria numerica C++17 e tutte le risorse runtime. L'utente finale non deve installare Python, pacchetti `pip`, CMake o un compilatore.

## Perché esistono due artefatti

Fedora è già coperta dall'archivio Linux, ma l'RPM offre un'installazione di sistema corretta. I due artefatti non contengono build differenti del gioco: l'RPM riusa esattamente il payload già sottoposto allo smoke test.

Un eseguibile Linux non è automaticamente compatibile con ogni distribuzione. La glibc e le librerie native della macchina di build stabiliscono il limite minimo effettivo. Per distribuire l'archivio portabile a più distribuzioni, costruirlo e collaudarlo sulla distribuzione più vecchia che si intende supportare. L'RPM va costruito sulla release Fedora meno recente tra quelle supportate.

## Requisiti della macchina di build

- Linux x86_64;
- Python x86_64 3.10 o successivo con supporto `venv`;
- CMake 3.20 o successivo, g++ con supporto C++17 e make;
- accesso a PyPI durante la build pulita;
- `rpmbuild` per creare l'RPM (`rpm-build` su Fedora);
- `desktop-file-validate` consigliato (`desktop-file-utils` su Fedora).

La venv temporanea usa PyInstaller 6.21 e Pillow 10–12. Pillow serve soltanto alla preparazione del pacchetto e delle icone: il gioco non lo importa a runtime.

Da Fedora:

```bash
sudo dnf install python3 cmake gcc-c++ make rpm-build desktop-file-utils
./packaging/linux/build.sh
```

Lo script crea una venv temporanea, installa versioni bloccate degli strumenti, compila la libreria C++ con CMake e la include in `native/` nel payload PyInstaller. Esegue poi lo smoke test e scrive gli artefatti e `SHA256SUMS` in `dist/linux/`. La directory temporanea viene rimossa automaticamente.

Target singoli e opzioni utili:

```bash
./packaging/linux/build.sh --target portable
./packaging/linux/build.sh --target rpm
./packaging/linux/build.sh --python /percorso/python3
./packaging/linux/build.sh --use-current-environment
```

L'edizione si sceglie soltanto al momento del packaging:

```bash
./packaging/linux/build.sh --edition full
./packaging/linux/build.sh --edition demo
./packaging/linux/build.sh --edition both
```

Senza `--edition` viene creato soltanto il pacchetto completo. La demo usa il
suffisso `-demo`; l'RPM demo è separato e installa il comando `calciototale-demo`.

L'ultima opzione serve per collaudi locali veloci e richiede che PyInstaller e PySide6 siano già installati; per una release va preferita la venv pulita.

## Uso dell'archivio Linux

```bash
tar -xzf CalcioTotale-1.0.7-linux-x86_64.tar.gz
./CalcioTotale/CalcioTotale
```

La cartella estratta deve essere scrivibile: i salvataggi portabili risiedono in `CalcioTotale/user/`. Per spostare il gioco con le carriere basta copiare l'intera cartella.

## Installazione Fedora

```bash
sudo dnf install ./calciototale-1.0.7-1.fc*.x86_64.rpm
```

Il gioco appare nel menu applicazioni e può essere avviato anche con `calciototale`. I salvataggi dell'RPM risiedono in `${XDG_DATA_HOME:-$HOME/.local/share}/calciototale/user/` e non vengono rimossi disinstallando il pacchetto.

## Collaudo prima della distribuzione

1. verificare `sha256sum -c SHA256SUMS`;
2. provare l'archivio su ciascuna distribuzione Linux dichiarata come supportata;
3. installare l'RPM su una Fedora pulita con `dnf`;
4. creare una carriera, salvare, chiudere e ricaricare;
5. controllare icone, magliette delle squadre, font, cursori, rendering grafico Qt e scaling sotto Wayland e X11;
6. verificare la presenza di `README.md`, `README.it.md`, `README.es.md`, `LICENSE`, `THIRD_PARTY_NOTICES.md`, `privacy.html`, `licenses/` e `BUILD_COMPONENTS.txt`;
7. confrontare le versioni in `BUILD_COMPONENTS.txt` con `THIRD_PARTY_NOTICES.md` e completare gli obblighi applicabili della distribuzione PySide6/Qt Community.

La firma RPM e il repository DNF restano passaggi di pubblicazione separati. La pipeline predefinita usa PySide6/Qt Community; un'eventuale build sotto licenza commerciale Qt richiede dipendenze, credenziali e documentazione dedicate.
