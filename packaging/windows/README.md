# Build Windows portabile

La build produce una cartella autonoma `dist/CalcioTotale/`, l'archivio versionato `dist/CalcioTotale-1.0.7-windows-x64.zip` e `dist/SHA256SUMS`. Il computer dell'utente non deve avere Python, PySide6 o altre dipendenze installate.

PyInstaller non è un cross-compiler: questa procedura va eseguita su Windows x64. Lo script crea un ambiente virtuale pulito nella directory temporanea di Windows, installa automaticamente le dipendenze e lo elimina al termine.

## Requisiti della macchina di build

- Windows 10 o 11 x64;
- Python x64 3.10 o successivo disponibile come `python`;
- CMake 3.20 o successivo disponibile nel `PATH`;
- Visual Studio 2022 o Build Tools 2022 con gli strumenti MSVC C++ x64 e il Windows SDK;
- accesso a PyPI per installare le dipendenze durante la build.

La venv temporanea usa PyInstaller 6.21 e Pillow 10–12. Pillow serve soltanto al packaging e alla conversione dell'icona dell'eseguibile: il gioco non lo importa a runtime.

Da PowerShell, nella root del progetto:

```powershell
powershell -ExecutionPolicy Bypass -File .\packaging\windows\build.ps1
```

L'edizione si sceglie soltanto al momento del packaging:

```powershell
.\packaging\windows\build.ps1 -Edition full
.\packaging\windows\build.ps1 -Edition demo
.\packaging\windows\build.ps1 -Edition both
```

Senza `-Edition` viene creato soltanto il pacchetto completo; la demo usa il
suffisso `-demo`.

Se il comando Python corretto non è quello predefinito:

```powershell
powershell -ExecutionPolicy Bypass -File .\packaging\windows\build.ps1 `
  -PythonExecutable "C:\percorso\python.exe"
```

Lo script compila automaticamente il motore C++17 tramite CMake e include `ct_engine.dll` in `native/`, insieme alle dipendenze rilevate da PyInstaller. L'utente finale non deve installare CMake o un compilatore. Lo script esegue anche uno smoke test dell'artefatto prima di creare lo ZIP. I salvataggi della build portabile vengono scritti in `user/`, accanto a `CalcioTotale.exe`.

## Collaudo prima della distribuzione

Su una macchina Windows pulita, senza Python installato:

1. estrarre completamente lo ZIP in una cartella scrivibile;
2. avviare `CalcioTotale.exe`;
3. creare una carriera, salvare in uno slot, chiudere e ricaricare;
4. verificare icone, magliette delle squadre, font, cursori e scaling del display;
5. verificare che `README.md`, `README.it.md`, `README.es.md`, `LICENSE`, `THIRD_PARTY_NOTICES.md`, `privacy.html`, `licenses/` e `BUILD_COMPONENTS.txt` siano presenti;
6. confrontare le versioni in `BUILD_COMPONENTS.txt` con `THIRD_PARTY_NOTICES.md` e completare gli obblighi applicabili della distribuzione PySide6/Qt Community.

Questa è una build portabile, non un installer. Non va collocata in `Program Files`, perché i salvataggi risiedono accanto all'eseguibile. Firma del codice e installer sono passaggi separati. La pipeline predefinita usa PySide6/Qt Community; un'eventuale build sotto licenza commerciale Qt richiede dipendenze, credenziali e documentazione dedicate.
