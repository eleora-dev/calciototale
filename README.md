# CalcioTotale

[English version](README.en.md)

CalcioTotale è un videogioco gestionale calcistico locale e per giocatore singolo, incentrato sul calcio italiano. La build pubblica attuale è la **versione 1.0 beta**, con database aggiornato alla stagione **2025-26**.

> **Lingua:** il gioco e la sua interfaccia sono attualmente disponibili esclusivamente in italiano.

![Windows](https://img.shields.io/badge/Windows-x64-0078d4)
![Linux](https://img.shields.io/badge/Linux-x86__64-fcc624)
![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon%20%7C%20Intel-000000)
![Versione](https://img.shields.io/badge/versione-1.0%20beta-f6a91a)
![Licenza](https://img.shields.io/badge/licenza-proprietaria-red)
![Offline](https://img.shields.io/badge/gioco-offline-41cd52)

---

![CalcioTotale](assets/branding/screenshot.png)

---

## Download

I pacchetti ufficiali della [Release v1.0beta](https://github.com/eleora-dev/calciototale/releases/tag/v1.0beta) sono disponibili per:

Pacchetti aggiornati il **18 agosto 2026**.

- [Windows 10/11 x64 — ZIP portabile](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/CalcioTotale-1.0beta-windows-x64.zip)
- [Linux x86_64 — archivio portabile](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/CalcioTotale-1.0beta-linux-x86_64.tar.gz)
- [Fedora 44 x86_64 — pacchetto RPM](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/calciototale-1.0-0.beta.1.fc44.x86_64.rpm)
- [macOS 13+ Apple Silicon](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/CalcioTotale-1.0beta-macOS-arm64.zip)
- [macOS 13+ Intel](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/CalcioTotale-1.0beta-macOS-x86_64.zip)

I pacchetti sono autonomi: non è necessario installare Python o pacchetti Python. Questo repository distribuisce esclusivamente le build eseguibili ufficiali; il codice sorgente è privato.

### Verifica dell'integrità

Per controllare i file scaricati è disponibile [SHA256SUMS](https://github.com/eleora-dev/calciototale/releases/download/v1.0beta/SHA256SUMS).

## Installazione e avvio

### Windows

Estrai completamente lo ZIP in una cartella scrivibile, apri la directory `CalcioTotale` e avvia `CalcioTotale.exe`. È una build portabile: non avviarla direttamente dallo ZIP e non collocarla in `Program Files`. I salvataggi sono conservati in `saves/` accanto all'eseguibile.

### Linux

Per la versione portabile, estrai l'archivio e avvia `CalcioTotale/CalcioTotale`. La build è generata e collaudata su Fedora 44. Su Fedora puoi in alternativa installare l'RPM con:

```bash
sudo dnf install ./calciototale-1.0-0.beta.1.fc44.x86_64.rpm
```

La build portabile conserva `saves/` accanto all'eseguibile; l'RPM usa `${XDG_DATA_HOME:-$HOME/.local/share}/calciototale/saves/`.

### macOS

Scegli il pacchetto `arm64` per i Mac Apple Silicon oppure `x86_64` per i Mac Intel. Estrai lo ZIP e trascina `CalcioTotale.app` in `Applicazioni`. I salvataggi sono conservati in `~/Library/Application Support/CalcioTotale/saves/` e rimangono separati dall'applicazione.

## Avvisi di sicurezza del sistema operativo

La build Windows non dispone ancora di una firma del codice e può mostrare un avviso Microsoft Defender SmartScreen. Le build macOS hanno una firma ad hoc ma non sono firmate con un certificato Apple Developer ID né notarizzate da Apple; Gatekeeper può quindi richiedere di confermare il primo avvio tramite clic destro sull'app e **Apri**. Scarica i pacchetti soltanto da questo repository ufficiale e verifica il file `SHA256SUMS` prima dell'uso.

## Caratteristiche principali

- due modalità carriera: *Solo la Maglia* e *Sentieri di Gloria*;
- Serie A, Serie B e tutti e tre i gironi di Serie C, con 100 club italiani selezionabili e altri 121 club europei e internazionali nel database di base;
- Coppa Italia, Coppa Italia Serie C, Supercoppa Italiana, play-off e play-out;
- competizioni UEFA, Coppa Intercontinentale e Mondiale per Club;
- moduli, formazioni, tattiche, ruoli, numeri di maglia, allenamento, infortuni, squalifiche e cronache delle partite;
- trasferimenti, prestiti, trattative, precontratti, osservazione e sviluppo dei giovani;
- finanze, obiettivi societari, staff, stadio e centro di allenamento;
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

I componenti e i materiali di terze parti, compresi Qt/PySide6, PyInstaller, icone, font e dipendenze degli strumenti di sviluppo, rimangono soggetti alle rispettive licenze, condizioni e titolarità. Consulta [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) e la directory [`licenses/`](licenses/).

CalcioTotale è un progetto non ufficiale e non è affiliato, approvato o sponsorizzato da federazioni, leghe, competizioni, club, giocatori o fornitori di dati.

## Autore

Gerardo Perilli · [Eleòra](https://github.com/eleora-dev)
