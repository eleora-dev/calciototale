# Sorgenti e interfaccia di CalcioTotale

`app/` contiene l'interfaccia Qt e il controller. `engine/` contiene modelli,
regole, simulazione, salvataggi e interfacce di sviluppo. Le sottocartelle
raggruppano i file per area funzionale; `app/common/` raccoglie i componenti
condivisi. I test e le verifiche dell'interfaccia sono in `../dev/tests/`.

Le immagini originali sono in `../assets/`. Qt applica ritaglio, scala e colore
in memoria; disegna anche maglie e simboli del titolo, senza PNG intermedi.
Testi, stili e definizioni delle trasformazioni sono in `ui/`.

Compilazione dalla cartella principale:

```sh
cmake -S src -B build/desktop -DCMAKE_BUILD_TYPE=Release
cmake --build build/desktop --target calciototale_owned ct_career -j2
```

Servono C++17 e Qt 6.7 o successivo con Core, Gui, Widgets e Svg.
Gli script di distribuzione sono in `../build/linux/`, `../build/windows/`
e `../build/macos/`. `build/desktop/` è l'unica compilazione locale corrente.

I commenti del codice sono scritti in italiano e descrivono comportamento,
vincoli e responsabilità dei componenti. Le attribuzioni degli algoritmi e
delle librerie sono raccolte in `../THIRD_PARTY_NOTICES.md` e `../licenses/`.
