---
date: 2026-08-10
description: Scopri come dividere i file PDF con GroupDocs.Merger for .NET. I tutorial
  C# ti guidano a dividere PDF di grandi dimensioni, estrarre pagine e combinare immagini
  in PDF in modo efficiente.
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: Tutorial GroupDocs.Merger for .NET
og_description: Scopri come dividere i file PDF con GroupDocs.Merger for .NET. I tutorial
  C# ti guidano a dividere PDF di grandi dimensioni, estrarre pagine e combinare immagini
  in PDF in modo efficiente.
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: Come dividere PDF con GroupDocs.Merger for .NET – guida
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  headline: How to split PDF with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  name: How to split PDF with GroupDocs.Merger for .NET
  steps:
  - name: load the PDF document
    text: Create a `PdfDocument` instance by passing the file path or a stream. The
      constructor reads the document header without loading all pages into memory.
  - name: split by page range
    text: Use the `Split` method, providing a `PageRange` object that defines the
      start and end pages. The method returns a collection of new `PdfDocument` objects,
      each representing the requested segment.
  - name: save the resulting files
    text: Iterate over the split documents and call `Save` with a unique file name.
      You can also apply compression or password protection before saving.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then use `Split` or
      `Extract` as you would with an unprotected file.
    question: Can I split a password‑protected PDF?
  - answer: There is no hard limit; the library streams pages, so you can split PDFs
      with thousands of pages as long as you have sufficient disk space for the output
      files.
    question: How many pages can I split at once?
  - answer: It supports cross‑format merging, allowing you to combine PPTX slides
      with PDF pages into a single PDF output.
    question: Does GroupDocs.Merger support merging PowerPoint files with PDFs?
  - answer: Enable streaming mode (`PdfLoadOptions.Stream = true`) to keep memory
      usage low while splitting or extracting pages.
    question: What is the recommended way to handle very large PDFs?
  - answer: Yes. Use the `Bookmarks` collection to identify chapter start pages and
      programmatically call `Split` for each range.
    question: Is there a way to automate splitting of every chapter in a PDF?
  type: FAQPage
tags:
- split PDF
- GroupDocs.Merger
- C# document processing
- PDF manipulation
- document merging
title: Come dividere PDF con GroupDocs.Merger for .NET
type: docs
url: /it/net/
weight: 10
---

# Come dividere PDF con GroupDocs.Merger per .NET

## Gestione avanzata dei documenti con GroupDocs.Merger

`GroupDocs.Merger for .NET` è una libreria .NET che consente agli sviluppatori di combinare, dividere e manipolare documenti in più di 50 formati di file. Se hai bisogno di sapere **come dividere PDF**, questa guida ti mostra i passaggi esatti usando GroupDocs.Merger per .NET, completa di scenari reali e consigli di best‑practice.

## Risposte rapide
- **Come dividere un PDF in pagine singole?** Chiama `PdfDocument.Split` con un intervallo di pagine `1‑1` per ogni pagina.  
- **Posso estrarre solo pagine specifiche?** Sì – passa i numeri di pagina desiderati a `Split` o `Extract`.  
- **La protezione con password è supportata?** Assolutamente; usa `PdfDocument.Protect` prima di salvare.  
- **Come combinare immagini in un PDF?** Carica ogni immagine come `PdfPage` e aggiungila a un nuovo documento.  
- **E i PDF di grandi dimensioni?** Usa la modalità streaming per evitare di caricare l'intero file in memoria.

## Che cosa significa dividere PDF?
**Come dividere PDF** si riferisce al processo di suddivisione di un file PDF multi‑pagina in documenti PDF più piccoli e separati—sia per pagine individuali, intervalli di pagine o criteri personalizzati—utilizzando API programmatiche. È comunemente usato per isolare sezioni, ridurre la dimensione del file o preparare documenti per la distribuzione. L'operazione può essere eseguita programmaticamente tramite librerie come GroupDocs.Merger, che espongono metodi per specificare intervalli di pagine esatti e impostazioni di output.

## Perché usare GroupDocs.Merger per dividere PDF?
GroupDocs.Merger elabora **55+** formati di input e output, gestisce PDF fino a **2 GB** senza caricamento completo in memoria, e può dividere un PDF di 500 pagine in meno di **3 secondi** su un server tipico. Questi numeri di prestazioni quantificati lo rendono una scelta affidabile per pipeline di documenti ad alto throughput.

## Come dividere file PDF con GroupDocs.Merger?
PdfDocument è la classe principale che rappresenta un file PDF all'interno di GroupDocs.Merger. Per dividere un PDF, prima carica il file sorgente in un'istanza di PdfDocument, quindi specifica le pagine che desideri estrarre usando il metodo Split. Il metodo restituisce oggetti PdfDocument separati per ogni segmento, che puoi quindi salvare individualmente. Questo approccio funziona per qualsiasi dimensione di documento e richiede solo poche righe di codice.

### Passo 1: caricare il documento PDF
Crea un'istanza di `PdfDocument` passando il percorso del file o uno stream. Il costruttore legge l'intestazione del documento senza caricare tutte le pagine in memoria.

### Passo 2: dividere per intervallo di pagine
Usa il metodo `Split`, fornendo un oggetto `PageRange` che definisce le pagine di inizio e fine. Il metodo restituisce una collezione di nuovi oggetti `PdfDocument`, ciascuno rappresentante il segmento richiesto.

### Passo 3: salvare i file risultanti
Itera sui documenti divisi e chiama `Save` con un nome file univoco. Puoi anche applicare compressione o protezione con password prima di salvare.

## Come combinare immagini in PDF?
PdfDocument è la classe principale usata per creare nuovi file PDF in GroupDocs.Merger. Per combinare immagini, carica ogni file immagine e aggiungilo come nuova pagina a una nuova istanza di PdfDocument usando il metodo AddPage. Dopo che tutte le immagini sono state aggiunte, salva il documento, che preserva la risoluzione originale e incorpora le immagini come pagine basate su vettori quando il formato lo consente. Il risultato è un PDF di alta qualità contenente tutte le immagini fornite.

## Come proteggere PDF con password?
PdfDocument è l'oggetto che rappresenta un documento PDF e fornisce funzionalità di sicurezza. Dopo aver caricato o creato un PdfDocument, chiama il suo metodo Protect con una password utente e flag di permesso opzionali come stampa o copia. Il metodo cripta il file e, quando successivamente chiami Save, il PDF risultante può essere aperto solo dagli utenti che conoscono la password, garantendo la riservatezza.

## Come estrarre pagine da PDF?
PdfDocument è la classe principale che rappresenta un file PDF in GroupDocs.Merger. Per estrarre pagine, istanzia un PdfDocument con il file sorgente, quindi invoca il metodo Extract, passando un elenco di numeri di pagina che desideri conservare. Il metodo restituisce un nuovo PdfDocument contenente solo quelle pagine, che puoi poi salvare come PDF separato. Questa tecnica è utile per creare report personalizzati o condividere sezioni specifiche.

## Come unire presentazioni PowerPoint?
Merge è un metodo fornito da GroupDocs.Merger che concatena più documenti in un unico file di output. Per unire presentazioni PowerPoint, carica ogni file .pptx come oggetto Document, quindi chiama il metodo Merge su un nuovo PdfDocument o PresentationDocument, passando la collezione di documenti sorgente. La libreria preserva le animazioni delle diapositive, le transizioni e la formattazione, producendo una presentazione combinata che può essere salvata come PDF o PPTX.

## Come dividere pagine PDF di grandi dimensioni?
PdfLoadOptions.Stream è una proprietà che abilita la modalità streaming, consentendo a GroupDocs.Merger di elaborare file PDF di grandi dimensioni senza caricare l'intero documento in memoria. Quando si lavora con PDF molto grandi, imposta PdfLoadOptions.Stream su true prima di caricare il file. Questo riduce il consumo di memoria e ti permette di dividere o estrarre pagine in modo efficiente, anche per file più grandi di 1 GB, mantenendo le prestazioni.

## Caratteristiche principali e capacità

- **Unire più documenti** attraverso oltre 55 formati in un unico file coeso
- **Unire pagine specifiche o intervalli di pagine** da diversi documenti sorgente
- **Dividere documenti** per numeri di pagina, intervalli o criteri di pagine pari/dispari
- **Manipolare l'ordine delle pagine** tramite spostamento, rimozione, rotazione o scambio
- **Proteggere i documenti** con protezione password e controlli di permesso granulari
- **Estrarre pagine specifiche** per creare nuovi documenti mirati
- **Elaborare oltre 55 formati** includendo PDF, Office, immagini e archivi con un'API unificata

## Categorie dei tutorial di GroupDocs.Merger per .NET

### [Unire e comprimere file](./merge-compress-files/)
Impara a unire e comprimere formati di archivio come 7z, TAR e ZIP in modo efficiente. I nostri tutorial ti guidano nella combinazione di archivi con GroupDocs.Merger per .NET con esempi C# completi.

### [Unire immagini](./image-merging/)
Padroneggia le tecniche per unire BMP, GIF, PNG, SVG, TIFF e altri formati di immagine. Scopri come combinare immagini in documenti singoli preservando qualità e formattazione.

### [Unire documenti](./document-merging/)
Unisci DOC, DOCX, PDF, RTF e vari formati di documento in file unificati. Questi tutorial coprono scenari di unione di documenti con passaggi di implementazione dettagliati e best practice.

### [Unire fogli di calcolo](./spreadsheet-merging/)
Unisci file Excel (XLAM, XLS, XLSX, XLSM, XLTX) e altri formati di fogli di calcolo mantenendo l'integrità dei dati, le formule e la formattazione con queste guide passo‑passo.

### [Unire Visio](./visio-merging/)
Combina diagrammi e disegni Visio (VDX, VSDM, VSDX, VSSM, VSSX) in modo efficiente con i nostri tutorial specializzati per la gestione di documenti diagramma nelle applicazioni .NET.

### [Unire presentazioni](./presentation-merging/)
Impara a unire PowerPoint e altri formati di presentazione (PPS, PPSX, PPT, OTP) preservando diapositive, animazioni e formattazione con esempi di codice completi.

### [Caricamento documenti](./document-loading/)
Scopri vari approcci per caricare documenti da file, stream e URL con la configurazione corretta per diversi formati. Padroneggia il primo passo essenziale nell'elaborazione dei documenti.

### [Informazioni sul documento](./document-information/)
Estrai metadati preziosi dai documenti includendo dettagli sul formato, conteggio pagine e proprietà. Impara ad analizzare i documenti programmaticamente prima di elaborarli.

### [Unire documenti](./document-joining/)
Unisci più file senza soluzione di continuità con tecniche avanzate di unione. I nostri tutorial ti mostrano come unire documenti con controllo preciso su contenuto e struttura.

### [Unire specifico per formato](./format-specific-merging/)
Esplora operazioni di unione ottimizzate su misura per formati di file specifici. Impara tecniche specializzate per diversi tipi di documento per ottenere i migliori risultati.

### [Opzioni avanzate di unione](./advanced-joining-options/)
Porta l'unione di documenti al livello successivo con questi tutorial avanzati che coprono selezione complessa di pagine, unione cross‑format e strategie di preservazione del contenuto.

### [Sicurezza dei documenti](./document-security/)
Implementa una protezione robusta per i tuoi documenti. Impara ad aggiungere, rimuovere e aggiornare password, gestire permessi e garantire la riservatezza dei documenti nelle tue applicazioni.

### [Operazioni sulle pagine](./page-operations/)
Padroneggia il controllo preciso delle pagine del documento con tutorial su riordino, rotazione, rimozione e modifica di pagine individuali per una gestione personalizzata dei documenti.

### [Estrazione di documenti](./document-extraction/)
Estrai contenuti specifici dai documenti con queste guide dettagliate. Impara a selezionare e salvare pagine o sezioni particolari come file separati con codice minimo.

### [Importazione di documenti](./document-import/)
Arricchisci i documenti con contenuti esterni includendo oggetti OLE e file incorporati. Impara a importare contenuti da varie fonti per arricchire i tuoi documenti.

### [Operazioni sulle immagini](./image-operations/)
Elabora file immagine in modo efficace con i nostri tutorial completi che coprono unione di immagini, conversione e tecniche di manipolazione nelle tue applicazioni .NET.

### [Divisione di documenti](./document-splitting/)
Dividi i documenti in modo intelligente in componenti più piccoli con questi tutorial sulla divisione di documenti per numeri di pagina, intervalli e criteri personalizzati.

### [Operazioni di testo](./text-operations/)
Lavora con documenti basati su testo in modo efficiente usando le nostre guide sull'elaborazione di TXT, CSV e altri formati di testo, includendo tecniche di divisione e unione basate su linee.

### [Licenze](./licensing/)
Configura correttamente GroupDocs.Merger nei tuoi progetti con i nostri tutorial dettagliati sulle licenze che coprono tutti gli scenari di distribuzione e ambienti.

## Formati di file supportati

GroupDocs.Merger per .NET supporta **oltre 55** formati di documento popolari, includendo:

- **Formati di documento**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **Fogli di calcolo**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **Presentazioni**: PPT, PPTX, PPS, PPSX, ODP
- **Immagini**: BMP, GIF, JPG, PNG, SVG, TIFF
- **Diagrammi**: VDX, VSDX, VSX, VTX, VSTX, VSSX
- **Archivi**: ZIP, TAR, 7Z
- **E molti altri!**

## Domande frequenti

**D: Posso dividere un PDF protetto da password?**  
R: Sì. Carica il documento con il parametro password, quindi usa `Split` o `Extract` come faresti con un file non protetto.

**D: Quante pagine posso dividere contemporaneamente?**  
R: Non c'è un limite rigido; la libreria trasmette le pagine in streaming, quindi puoi dividere PDF con migliaia di pagine purché tu abbia spazio su disco sufficiente per i file di output.

**D: GroupDocs.Merger supporta l'unione di file PowerPoint con PDF?**  
R: Supporta l'unione cross‑format, consentendo di combinare diapositive PPTX con pagine PDF in un unico output PDF.

**D: Qual è il modo consigliato per gestire PDF molto grandi?**  
R: Abilita la modalità streaming (`PdfLoadOptions.Stream = true`) per mantenere basso l'uso della memoria durante la divisione o l'estrazione delle pagine.

**D: Esiste un modo per automatizzare la divisione di ogni capitolo in un PDF?**  
R: Sì. Usa la collezione `Bookmarks` per identificare le pagine di inizio capitolo e chiama programmaticamente `Split` per ogni intervallo.

---

**Ultimo aggiornamento:** 2026-08-10  
**Testato con:** GroupDocs.Merger 23.9 per .NET  
**Autore:** GroupDocs

## Tutorial correlati

- [Come unire file PDF in modo efficiente usando GroupDocs.Merger per .NET](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [Come unire pagine PDF specifiche con GroupDocs.Merger per .NET: Guida completa](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Come unire file PDF con segnalibri usando GroupDocs.Merger per .NET](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)