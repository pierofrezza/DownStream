# DownStream 1.0.0

**7 ottobre 2026 · build 87 · macOS 15 Sequoia o successivo · Apple Silicon e Intel**

DownStream 1.0.0 è la prima release pubblica dell'interfaccia macOS nata dall'evoluzione del precedente workflow StreamDownloader.

L'obiettivo della 1.0 è riunire in un'unica applicazione analisi HLS, selezione delle tracce, sottotitoli, profili, coda, retry e mux finale, mantenendo il controllo manuale quando serve e automatizzando le operazioni ripetitive.

## Analisi e selezione delle tracce

DownStream può analizzare URL e playlist HLS/M3U8 e presentare le varianti disponibili in modo leggibile.

La configurazione permette di selezionare:

- variante video;
- una o più tracce audio quando la sorgente lo consente;
- sottotitoli HLS;
- contenitore finale e opzioni di mux compatibili con la sorgente.

## Sottotitoli HLS

La gestione dei sottotitoli distingue rendition differenti anche quando condividono la stessa lingua.

Quando i metadati sono presenti, DownStream può riconoscere separatamente:

- sottotitoli normali;
- forced;
- SDH;
- tracce senza classificazione esplicita.

I download SRT usano nomi distinti per evitare collisioni tra tracce della stessa lingua.

## MP4, MKV e TS

DownStream supporta diversi percorsi di esportazione:

- **MP4**;
- **MKV**;
- **TS**, quando la sorgente originale lo rende disponibile e il workflow selezionato è compatibile.

Per sorgenti TS più datate può eseguire una normalizzazione/remux senza ricodifica quando necessario per migliorare la compatibilità del file finale.

## Audio esterno e mux

Sono disponibili workflow per aggiungere o sostituire audio esterno mantenendo il controllo sulle tracce finali.

A seconda del contenitore e della configurazione, DownStream può utilizzare FFmpeg, MP4Box, mkvmerge o Subler per completare il file.

## Profili

Le configurazioni possono essere salvate e riutilizzate tramite profili.

Sono supportati anche profili temporanei, utili per applicare una configurazione senza sostituire quella permanente corrente.

## Coda, download simultanei e controllo attività

La 1.0 include una coda di lavori con:

- più job pronti o configurabili;
- download simultanei configurabili;
- pausa e ripresa;
- stop e salto del lavoro;
- retry automatici;
- cronologia dei lavori;
- log dettagliati opzionali.

Il progresso resta monotono durante le operazioni di recupero, evitando apparenti ritorni indietro quando vengono riprocessati frammenti HLS.

## Recupero HLS

Il motore 1.0 include un percorso di verifica e recupero dedicato ai frammenti HLS problematici.

Quando necessario può effettuare retry mirati e ricostruire il risultato senza ripartire inutilmente da zero, mantenendo una sintesi leggibile dell'attività nel log/interfaccia.

## Compatibilità e distribuzione

DownStream 1.0.0 richiede:

- **macOS 15 Sequoia o successivo**;
- Mac con **Apple Silicon** oppure **Intel**.

Sono distribuite tre varianti:

- Apple Silicon;
- Intel;
- Universal.

La Universal contiene entrambe le architetture ed è la scelta consigliata quando non si conosce l'architettura del Mac.

## Verifica release

La build 87 è la baseline funzionale finale della 1.0.0.

La QA finale ha coperto i principali flussi di download singolo e multiplo, coda, download simultanei, pausa/ripresa, retry, profili, sottotitoli, MP4Box, Subler, MKV e TS, oltre alle tre configurazioni di architettura distribuite.

Le applicazioni sono firmate con Apple Developer ID, utilizzano Hardened Runtime e sono notarizzate da Apple. Anche i tre DMG sono firmati, notarizzati, stapled e accettati da Gatekeeper.

Checksum SHA-256 finali:

```text
e3c469027782488f8254526cf87db0f9b6bf9d820245248a26bcb3c08fd35bec  DownStream-1.0.0-Apple-Silicon.dmg
c6ed57242244ca5d37a69318f51568ee03f9fe29fa0482ec8fe233f6cfba32e0  DownStream-1.0.0-Intel.dmg
1e741ffacf178bac679429174bf85ff240bc0f8cc010dd5917553a27c68a2b1a  DownStream-1.0.0-Universal.dmg
```

## Componenti di terze parti

DownStream distribuisce strumenti open source separati, tra cui yt-dlp, FFmpeg, MKVToolNix/mkvmerge, GPAC/MP4Box e Subler.

Questi componenti restano soggetti alle rispettive licenze. Consulta `THIRD_PARTY_NOTICES.md` e i materiali di conformità sorgente pubblicati insieme alla release.

## Uso responsabile

DownStream deve essere utilizzato solo con contenuti che l'utente è autorizzato a scaricare, copiare o elaborare. Non è progettato per aggirare DRM o altre misure tecniche di protezione.
