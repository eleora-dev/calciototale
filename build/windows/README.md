# Build nativa windows

Il payload contiene il gioco C++17, Qt e le risorse.

Lo ZIP include le DLL redistribuibili Microsoft C++ x64 accanto all'eseguibile, copiate dalla cartella Redist di Visual Studio. L'avvio non dipende dal runtime C++ già installato sul computer. Il packaging fallisce se le DLL necessarie non sono disponibili; il solo installer `vc_redist.x64.exe` non è sufficiente per il pacchetto portabile.

Requisiti di build: Windows x64, Visual Studio 2022 C++ x64, Windows SDK, LLVM con `clang-cl`, Ninja, CMake 3.21+ e Qt SDK 6.7+ (Widgets e Svg) per MSVC con `windeployqt` nel PATH. Il packaging usa gli strumenti C++ in `dev/packaging/`.

Lo script configura l’ambiente Visual Studio x64 e compila con Ninja e clang-cl,
compatibile con l’ABI MSVC delle librerie Qt. Questo consente di incorporare i
cataloghi testuali senza il limite di dimensione delle stringhe del compilatore
MSVC. I cataloghi e il loro contenuto rimangono identici fra le piattaforme.

```powershell
./build/windows/build.ps1 -Edition both
```

Le edizioni disponibili sono `full`, `demo` e `both`. Versione ed etichetta degli archivi si impostano con `CALCIOTOTALE_VERSION` e `CALCIOTOTALE_RELEASE_LABEL`. Il tool compila il target `calciototale_owned`, copia le risorse originali, distribuisce Qt e verifica l'avvio del pacchetto con `--owned-build-smoke` prima dell'archiviazione. `BUILD_COMPONENTS.json` contiene gli hash dei file.

Per riusare un binario locale già compilato:

```powershell
./dev/packaging/build.ps1
./build/packaging/Release/ct_package.exe --binary build/desktop/calciototale_owned.exe --edition full --output dist/native
```

La build va eseguita sul sistema di destinazione. La procedura Linux conserva la dipendenza dalla glibc della macchina di build; la compatibilità con il runtime Steam richiede una build nel relativo contenitore. Windows e macOS richiedono verifica sul rispettivo sistema. Il percorso del nuovo SDK può essere indicato tramite `CMAKE_PREFIX_PATH`.
