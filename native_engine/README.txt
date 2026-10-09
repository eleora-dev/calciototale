Motore numerico C++ di Calcio Totale

Versione dell'applicazione: 1.0.7.

Il motore Python chiama direttamente la libreria C++ per i punteggi delle
formazioni, il confronto degli otto moduli CPU e l'assegnazione ungherese,
il filtro dei candidati del mercato CPU, i rating in blocco, le spese previste
delle gare future, i conteggi mensili degli stipendi
del mercato, la forza individuale in gara e i crediti di allenamento,
la valutazione degli ordini del ritorno, le clausole casa/trasferta,
i calcoli grezzi dello sviluppo stagionale, i totali delle classifiche
e la pubblicazione delle gare nel calendario.
Non vengono sostituiti metodi
a runtime e non viene riscritto codice tramite AST.

L'avvio normale dal progetto è sufficiente:

  python3 -B calciototale.py

Il motore nativo è la scelta predefinita. All'avvio vengono verificati il formato
binario dell'interfaccia e tutti i kernel contro le formule Python. L'algoritmo
ungherese mantiene lo stesso ordine nei pareggi; i bonus giovani/contratti/rotazione,
le decisioni casuali, l'interfaccia e l'avanzamento sincrono restano nel codice
attuale. La libreria non accede a salvataggi o RNG.

Il mercato usa uno snapshot limitato al singolo passaggio. Giocatori e squadre
modificati da trasferimenti, contratti e precontratti vengono aggiornati prima
della ricerca successiva. I criteri di credibilità e le decisioni economiche
restano nel motore Python. I conteggi dei prestiti leggono gli importi attuali;
lo snapshot e i suoi indici vengono eliminati anche in caso di errore.

I rating inviano una struttura compatta con i soli valori necessari al calcolo.
Le somme tecniche e le penalità di posizione riusano risultati numerici limitati
in memoria, con tutti gli input nella chiave: modificare attributi, morale, tetto
di serie o posizioni naturali produce subito una nuova valutazione. Gli elenchi
di vendita e l'accesso ai precontratti vengono letti una volta per squadra entro
ciascun aggiornamento del passaggio di mercato.

Le previsioni delle spese di gara calcolano una volta l'organizzazione del club e
inviano tutte le partite future al kernel C++; gli arrotondamenti alle migliaia
restano identici alla formula della singola gara. Biglietteria e ricavi delle
strutture riusano risultati soltanto nella stessa previsione e per gli stessi
valori di affluenza, ambito e importanza. Ogni nuova previsione legge lo stato
attuale, compresi staff, prezzi, stadio e calendario.

I due canali della comunicazione condividono una lettura del contesto sportivo
entro la stessa richiesta, conservando valutazioni e risultati indipendenti.
L'indice delle traduzioni compila le espressioni regolari solo per i candidati
ancora utili e conserva gli stessi criteri di scelta e ordine nei pareggi.

Il calendario conserva i medesimi sorteggi Python e l'ordine dei pareggi.
Nel passaggio stagionale i contributi tecnici individuali vengono riusati solo
entro la finestra di sviluppo e aggiornati dopo crescita differita, crescita
immediata, declino e correttivi dei giovani. Anche la generazione dei nuovi
giovani indicizza i nomi soltanto durante il riempimento delle rose.

La costruzione e il refresh della schermata calendario condividono una sola
lettura del programma corrente. Gli indici e i risultati della pubblicazione
vengono eliminati al termine dell'operazione: non cambiano il preload o la cache
di navigazione. Le classifiche mantengono ordinamento, scontri diretti e copie
indipendenti delle righe. Le tabelle mercato evitano i ricalcoli di geometria
per ciascun pulsante durante il riempimento e aggiornano il viewport alla fine.

Somme e arrotondamenti decimali che dipendono dalla versione di Python restano
in Python. I kernel restituiscono i crediti grezzi: viene applicato il medesimo
round(..., 4) del gioco prima di aggiornare i dati dei calciatori.

Uso dai sorgenti

  CMake 3.20 o successivo e un compilatore C++17 sono necessari per la prima compilazione.
  Linux: g++ e CMake. Windows: Visual Studio 2022 C++ x64 e CMake.
  macOS: toolchain Apple C++ e CMake.

  La libreria viene compilata automaticamente in packaging/build/native_engine quando
  mancano i file compilati o cambiano i sorgenti C++/header/CMake. Gli altri
  avvii riusano lo stesso file e non eseguono il compilatore. La directory
  di build è ignorata da Git e non contiene copie del gioco.
  Le compilazioni tra processi sono serializzate. Se cambiano i sorgenti,
  una nuova libreria viene preparata in una sottocartella della cache;
  i processi già aperti conservano la propria libreria fino alla chiusura.

  Per preparare la libreria senza avviare il gioco:

    python3 -B native_engine/build.py

  Per verificare tutte le funzioni native e le risorse dell'avvio normale:

    python3 -B calciototale.py --calciototale-build-smoke

Build distribuite

  Gli script di packaging compilano la libreria prima di PyInstaller.
  Gli spec la includono come binary in native/, insieme alle dipendenze
  individuate da PyInstaller. La libreria distribuita è già compilata:
  gli acquirenti non devono installare CMake o un compilatore.

  Un pacchetto senza la libreria è un errore: la build smoke verifica il
  backend effettivo e i risultati dei suoi calcoli. Il gioco distribuito
  non compila e non cerca i sorgenti C++ sul computer dell'acquirente.

  Windows e Linux sono compilati separatamente nei relativi ambienti.
  Il workflow Steam Linux usa lo stesso SDK Steam Runtime già configurato.
  macOS compila le architetture e la versione minima richieste dal packaging.

Verifica

  python3 -B tools/run_tests.py test_native_engine --jobs 1
  python3 -B tools/run_tests.py test_native_extra_kernels --jobs 1
  python3 -B tools/run_tests.py test_native_build --jobs 1
  python3 -B tools/run_tests.py test_native_seasons --jobs 1

  Il confronto esplicito Python è selezionabile solo per diagnostica/verifica:

    CALCIOTOTALE_ENGINE_BACKEND=python python3 -B calciototale.py

  I test del motore confrontano nuova carriera, tutti i club/moduli, scelte
  effettive CPU, avanzamenti, salvataggi completi e RNG tra i due backend.
  Il backend selezionato non viene scritto nel salvataggio.

Implementazione

  lineup.cpp                 Calcoli nativi e scelta degli XI provvisori CPU.
  kernels.cpp                Assegnazione, filtro mercato, stipendi, allenamento.
  seasons.cpp                Calendari, sviluppo, totali classifiche e pubblicazione.
  CMakeLists.txt             Build con floating point rigoroso, senza fast-math.
  build.py                   Compilazione e cache per sorgenti e packaging.
  ../engine/native_lineups.py Binding ctypes, gestione ABI e preparazione dati.
  ../engine/native_kernels.py Kernel aggiuntivi e snapshot temporaneo del mercato.
  ../engine/native_seasons.py Binding e indici temporanei per stagione e calendario.
  ../engine/squad_lineups.py  Chiamate dirette del motore.
