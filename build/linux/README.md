# Build nativa linux

Il payload contiene il gioco C++17, Qt e le risorse. Non include un interprete Python, PySide6, Shiboken o un bundle PyInstaller.

Requisiti di build: Linux x86_64, CMake 3.20+, compilatore C++17, Qt SDK 6.7+ con Widgets, Svg e plugin SVG, `patchelf`; `rpm-build` per il formato RPM. Python 3.10+ serve soltanto allo script di packaging in `tools/package_native.py`; non è una dipendenza del gioco.

```bash
./build/linux/build.sh --target portable --edition both
```

Le edizioni disponibili sono `full`, `demo` e `both`. Versione ed etichetta degli archivi si impostano con `CALCIOTOTALE_VERSION` e `CALCIOTOTALE_RELEASE_LABEL`. Il tool compila il target `calciototale_owned`, copia le risorse originali, distribuisce Qt e verifica l'avvio del pacchetto con `--owned-build-smoke` prima dell'archiviazione. `BUILD_COMPONENTS.json` contiene gli hash dei file.

Per riusare un binario locale già compilato:

```bash
python3 -B tools/package_native.py --binary build/desktop/calciototale_owned --edition full --output dist/native
```

La build va eseguita sul sistema di destinazione. La procedura Linux conserva la dipendenza dalla glibc della macchina di build; la compatibilità con il runtime Steam richiede una build nel relativo contenitore. Windows e macOS richiedono verifica sul rispettivo sistema. Il percorso del nuovo SDK può essere indicato tramite `CMAKE_PREFIX_PATH`.
