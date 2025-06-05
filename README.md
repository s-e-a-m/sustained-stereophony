# Sustained Stereophony

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Faust](https://img.shields.io/badge/DSP-Faust-orange)](https://faust.grame.fr/)
[![LaTeX](https://img.shields.io/badge/Documentation-LaTeX-blue)](https://www.latex-project.org/)

> *Una raccolta curatoriale sulla storia e teoria della stereofonia per la preservazione e sostenibilità della musica elettroacustica*

## Presentazione del Progetto

**Sustained Stereophony** è un archivio documentale e computazionale dedicato alla stereofonia e al suo ruolo fondamentale nello sviluppo della musica elettroacustica. Dal Théâtrophone di Clément Ader (1881) alle moderne tecniche di spazializzazione Ambisonics, questo repository traccia l'evoluzione delle tecnologie stereofone come patrimonio culturale da preservare e sostenere.

### Contesto S-E-A-M

Questo progetto è parte dell'organizzazione **S-E-A-M** (Sustained ElectroAcoustic Music), che si dedica alla **sostenibilità della musica elettroacustica** attraverso:
- La preservazione delle tecnologie e delle pratiche storiche
- Lo sviluppo di strumenti open source per la continuità creativa
- La documentazione critica del patrimonio elettroacustico
- La ricerca su metodologie sostenibili per l'arte sonora

## Struttura del Repository

```
sustained-stereophony/
├── README.md
├── LICENSE
├── doc/                    # Documentazione tecnica e storica
│   ├── bibliography/       # Bibliografia LaTeX
│   ├── papers/             # Articoli e saggi
│   └── historical/         # Documenti storici
├── src/                    # Implementazioni Faust
│   ├── historical/         # Ricostruzioni di sistemi storici
│   ├── microphones/        # Tecniche microfoniche
│   ├── ambisonics/         # Codifica/decodifica Ambisonics
│   └── psychoacoustics/    # Modelli percettivi
├── ref/                    # Testi di riferimento
│   ├── ader/              # Scritti di Clément Ader
│   ├── blumlein/          # Articoli di Alan Blumlein
│   ├── gerzon/            # Opere di Michael Gerzon
│   └── contemporary/      # Letteratura contemporanea
└── examples/              # Esempi pratici e tutorial
```

## Filosofia del Progetto

### Sostenibilità come Resistenza

La stereofonia non è solo una tecnologia: è un **linguaggio espressivo** che ha plasmato l'estetica della musica elettroacustica. La sua sostenibilità implica:

- **Continuità tecnologica**: Preservare le conoscenze tecniche attraverso implementazioni moderne
- **Continuità estetica**: Mantenere vivi i paradigmi espressivi della spazializzazione sonora  
- **Continuità critica**: Sviluppare una comprensione storica e teorica approfondita

### Dalla Storia all'Implementazione

Ogni sviluppo storico documentato in questo archivio trova una corrispondenza in **implementazioni Faust**, permettendo di:
- Sperimentare con i principi teorici storici
- Comprendere l'evoluzione delle tecniche attraverso la pratica
- Sviluppare nuove creatività a partire da fondamenta consolidate

## Bibliografia Curata

Il cuore documentale del progetto è una **bibliografia tecnica e scientifica** completa che copre:

### Preistoria (1876-1930)
- Esperimenti pionieristici di Clément Ader
- Théâtrophone e primi sistemi binaurali
- Osservazioni empiriche sulla percezione spaziale

### Fondazioni Teoriche (1931-1940)  
- Il brevetto fondamentale di Alan Blumlein
- Studi Bell Labs sulla prospettiva uditiva
- Prime formalizzazioni psicoacustiche

### Sviluppi Moderni (1950-1990)
- Sistemi stereofonici commerciali
- Rivoluzione Ambisonics di Michael Gerzon
- Teoria della localizzazione sonora

### Era Digitale (1990-presente)
- Elaborazione numerica e standard
- Audio binaurale e HRTF
- Tecniche immersive contemporanee

*La bibliografia completa è disponibile in formato BibTeX nella cartella `doc/bibliography/`*

## Implementazioni Faust

### Sistemi Storici
```faust
// Ricostruzione del sistema Blumlein (1931)
blumlein_pair = _ <: *(0.707), *(0.707) : +, -;

// Decodifica MS (Mid-Side)
ms_decode = +, - : *(0.707), *(0.707);
```

### Ambisonics
```faust
// Codifica B-Format di primo ordine
encode_1st = _ <: W, X, Y, Z
with {
    W = _ * 0.707;  // Omnidirezionale
    X = _ * cos(azimuth);   // Figure-8 fronte-retro
    Y = _ * sin(azimuth);   // Figure-8 sinistra-destra  
    Z = _ * cos(elevation); // Figure-8 alto-basso
};
```

*Implementazioni complete disponibili nella cartella `src/`*

## Utilizzo e Contributi

### Per Ricercatori
- Accesso alla bibliografia completa e ai testi di riferimento
- Implementazioni verificabili delle tecniche teoriche
- Documentazione storica per studi comparativi

### Per Compositori
- Strumenti Faust pronti per la composizione
- Esempi pratici di spazializzazione
- Connessione tra teoria storica e pratica contemporanea

### Per Sviluppatori
- Codice open source per sistemi audio spaziali
- Architetture modulari e riutilizzabili
- Test suite per la verifica delle implementazioni

## Come Contribuire

### Documentazione
- Digitalizzazione di testi storici rari
- Traduzioni di articoli in lingue diverse
- Analisi critiche e contestualizzazioni

### Codice
- Implementazioni Faust di nuove tecniche
- Ottimizzazioni e correzioni
- Esempi didattici e tutorial

### Bibliografia
- Segnalazione di nuovi riferimenti
- Correzioni e integrazioni
- Metadati e annotazioni

## Installazione e Dipendenze

### Requisiti
- **Faust** (≥ 2.41.1) per le implementazioni DSP
- **LaTeX** per la compilazione della documentazione
- **Git LFS** per i file di riferimento di grandi dimensioni

### Setup
```bash
git clone https://github.com/S-E-A-M/sustained-stereophony.git
cd sustained-stereophony
git lfs pull  # Per scaricare i PDF di riferimento
```

### Compilazione Documentazione
```bash
cd doc/bibliography
pdflatex bibliography_sectioned.tex
bibtex bibliography_sectioned
pdflatex bibliography_sectioned.tex
pdflatex bibliography_sectioned.tex
```

## Licenza e Riconoscimenti

Questo progetto è rilasciato sotto licenza **Creative Commons Attribution-ShareAlike 4.0** per favorire la massima diffusione e sostenibilità del sapere elettroacustico.

### Riconoscimenti Storici
- **Clément Ader** (1841-1925) - Pioniere della trasmissione binaurale
- **Alan Blumlein** (1903-1942) - Padre della stereofonia moderna  
- **Michael Gerzon** (1945-1996) - Creatore dell'Ambisonics

### Sostieni il Progetto
- ⭐ Aggiungi una stella al repository
- 🍴 Fai un fork per i tuoi esperimenti
- 📚 Contribuisci con documentazione o codice
- 💬 Partecipa alle discussioni nelle Issues

---

## Collegamenti

- **S-E-A-M Organization**: [github.com/S-E-A-M](https://github.com/S-E-A-M)
- **Faust Programming Language**: [faust.grame.fr](https://faust.grame.fr/)
- **Ambisonics Resources**: [ambisonics.net](http://www.ambisonics.net/)

---

*"La stereofonia non è solo tecnica, è filosofia dell'ascolto."*

**Sustained Stereophony** · S-E-A-M Organization · 2025
