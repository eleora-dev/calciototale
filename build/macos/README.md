# Build nativa macos

Il payload contiene il gioco C++17, Qt e le risorse. Non include un interprete Python, PySide6, Shiboken o un bundle PyInstaller.

Requisiti di build: macOS, Xcode Command Line Tools, CMake 3.20+ e Qt SDK 6.7+ (Widgets e Svg) con `macdeployqt` nel PATH. Per Universal 2 servono librerie Qt universali. Python 3.10+ serve soltanto allo script di packaging in `tools/package_native.py`; non è una dipendenza del gioco.

```bash
./build/macos/build.sh --edition both --architecture arm64
```

Le edizioni disponibili sono `full`, `demo` e `both`. Versione ed etichetta degli archivi si impostano con `CALCIOTOTALE_VERSION` e `CALCIOTOTALE_RELEASE_LABEL`. Il tool compila il target `calciototale_owned`, copia le risorse originali, distribuisce Qt e verifica l'avvio del pacchetto con `--owned-build-smoke` prima dell'archiviazione. `BUILD_COMPONENTS.json` contiene gli hash dei file.

Per riusare un binario locale già compilato:

```bash
python3 -B tools/package_native.py --binary build/desktop/calciototale_owned --edition full --output dist/native
```

La build va eseguita sul sistema di destinazione. La procedura Linux conserva la dipendenza dalla glibc della macchina di build; la compatibilità con il runtime Steam richiede una build nel relativo contenitore. Windows e macOS richiedono verifica sul rispettivo sistema. Il percorso del nuovo SDK può essere indicato tramite `CMAKE_PREFIX_PATH`.

La firma usa `CALCIOTOTALE_CODESIGN_IDENTITY`; senza identità viene applicata una firma ad hoc per il collaudo. `CALCIOTOTALE_NOTARY_PROFILE` abilita l'invio a notarytool e la successiva applicazione del ticket. `CALCIOTOTALE_MACOS_MIN_VERSION` imposta il target minimo (predefinito 13.0).
