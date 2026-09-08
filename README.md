# CalcioTotale

[English version](README.en.md)

CalcioTotale è un videogioco gestionale calcistico locale e per giocatore singolo, incentrato sul calcio italiano. Questo repository distribuisce la **versione demo 1.0**, con database aggiornato alla stagione **2026-27**.

> **Lingue:** il gioco e la sua interfaccia sono disponibili in italiano e inglese.

![Windows](https://img.shields.io/badge/Windows-x64-0078d4)
![Linux](https://img.shields.io/badge/Linux-x86__64-fcc624)
![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon%20%7C%20Intel-000000)
![Versione](https://img.shields.io/badge/versione-1.0%20Demo-f6a91a)
![Licenza](https://img.shields.io/badge/licenza-proprietaria-red)
![Offline](https://img.shields.io/badge/gioco-offline-41cd52)

---

![CalcioTotale](assets/branding/screenshot.png)

---

## Download

I pacchetti ufficiali della [Release v1.0](https://github.com/eleora-dev/calciototale/releases/tag/v1.0) sono disponibili per:

- [Windows 10/11 x64 — ZIP portabile](https://github.com/eleora-dev/calciototale/releases/download/v1.0/CalcioTotale-1.0-demo-windows-x64.zip)
- [Linux x86_64 — archivio portabile](https://github.com/eleora-dev/calciototale/releases/download/v1.0/CalcioTotale-1.0-demo-linux-x86_64.tar.gz)
- [Fedora 44 x86_64 — pacchetto RPM](https://github.com/eleora-dev/calciototale/releases/download/v1.0/calciototale-demo-1.0-1.fc44.x86_64.rpm)
- [macOS 13+ Apple Silicon](https://github.com/eleora-dev/calciototale/releases/download/v1.0/CalcioTotale-1.0-demo-macOS-arm64.zip)
- [macOS 13+ Intel](https://github.com/eleora-dev/calciototale/releases/download/v1.0/CalcioTotale-1.0-demo-macOS-x86_64.zip)

Pacchetti aggiornati l'**8 settembre 2026**.

La demo permette di iniziare una carriera con tutte le funzionalità e di giocare fino al termine del girone di andata della prima stagione. I pacchetti sono autonomi: non è necessario installare Python o pacchetti Python. Questo repository distribuisce esclusivamente la demo; la versione completa e il codice sorgente non sono pubblicati qui.

### Verifica dell'integrità

Per controllare i file scaricati è disponibile [SHA256SUMS](https://github.com/eleora-dev/calciototale/releases/download/v1.0/SHA256SUMS).

## Installazione e avvio

### Windows

Estrai completamente lo ZIP in una cartella scrivibile, apri la directory `CalcioTotale` e avvia `CalcioTotale.exe`. È una build portabile: non avviarla direttamente dallo ZIP e non collocarla in `Program Files`. I salvataggi sono conservati in `user/` accanto all'eseguibile.

### Linux

Per la versione portabile, estrai l'archivio e avvia `CalcioTotale/CalcioTotale`. La build è generata e collaudata su Fedora 44. Su Fedora puoi in alternativa installare l'RPM con:

```bash
sudo dnf install ./calciototale-demo-1.0-1.fc44.x86_64.rpm
```

La build portabile conserva `user/` accanto all'eseguibile; l'RPM usa `${XDG_DATA_HOME:-$HOME/.local/share}/calciototale/user/`.

### macOS

Scegli il pacchetto `arm64` per i Mac Apple Silicon oppure `x86_64` per i Mac Intel. Estrai lo ZIP e trascina `CalcioTotale.app` in `Applicazioni`. I salvataggi sono conservati in `~/Library/Application Support/CalcioTotale/user/` e rimangono separati dall'applicazione.

## Avvisi di sicurezza del sistema operativo

La build Windows non dispone ancora di una firma del codice e può mostrare un avviso Microsoft Defender SmartScreen. Le build macOS hanno una firma ad hoc ma non sono firmate con un certificato Apple Developer ID né notarizzate da Apple; Gatekeeper può quindi richiedere di confermare il primo avvio tramite clic destro sull'app e **Apri**. Scarica i pacchetti soltanto da questo repository ufficiale e verifica il file `SHA256SUMS` prima dell'uso.

## Caratteristiche principali

- due modalità carriera: *Solo la Maglia* e *Sentieri di Gloria*;
- controllo tecnico configurabile: formazione, tattiche, allenamento e gestione della gara possono essere diretti dal giocatore oppure delegati allo staff;
- Serie A, Serie B e tutti e tre i gironi di Serie C, con 100 club italiani selezionabili e altri 145 club europei e internazionali nel database di base;
- Coppa Italia, Coppa Italia Serie C, Supercoppa Italiana, play-off e play-out;
- competizioni UEFA, Coppa Intercontinentale e Mondiale per Club;
- moduli, formazioni, tattiche, ruoli, numeri di maglia, allenamento, infortuni, squalifiche e cronache delle partite;
- trasferimenti, prestiti, trattative, precontratti, osservazione e sviluppo dei giovani;
- finanze, conto economico e contabilità dei cartellini, obiettivi societari, staff, stadio e centro di allenamento;
- biglietteria, sponsor, diritti TV, stampa, canali social e merchandising;
- classifiche, calendari, statistiche, premi, record e notizie contestuali;
- nove slot locali per le carriere.

## Privacy

CalcioTotale è un gioco desktop offline:

- non richiede un account né un server remoto;
- non include telemetria, sistemi di analisi o pubblicità;
- durante il normale utilizzo non effettua richieste di rete;
- i dati delle carriere rimangono sul dispositivo dell'utente, salvo copia o condivisione da parte dell'utente stesso.

I collegamenti nella finestra Informazioni aprono il browser predefinito soltanto quando vengono selezionati. Per ulteriori dettagli consulta l'[informativa sulla privacy](privacy.html) completa in italiano e inglese.

## Licenza e diritti

La build ufficiale può essere scaricata, installata e utilizzata per uso personale e non commerciale secondo la [licenza proprietaria di CalcioTotale](LICENSE). La redistribuzione, la modifica, la pubblicazione, l'uso commerciale e i tentativi di ricavare il codice sorgente non sono consentiti senza preventiva autorizzazione scritta.

I componenti e i materiali di terze parti, compresi Python, Qt/PySide6, PyInstaller, Pillow usato per la build, icone e font, rimangono soggetti alle rispettive licenze, condizioni e titolarità. Consulta [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) e la directory [`licenses/`](licenses/); ogni pacchetto include inoltre `BUILD_COMPONENTS.txt` con le versioni principali effettivamente usate.

CalcioTotale è un progetto non ufficiale e non è affiliato, approvato o sponsorizzato da federazioni, leghe, competizioni, club, giocatori o fornitori di dati.

## Autore

Gerardo Perilli · [Eleòra](https://github.com/eleora-dev)
