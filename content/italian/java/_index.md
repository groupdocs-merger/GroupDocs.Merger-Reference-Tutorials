---
date: 2026-06-16
description: Scopri come dividere PDF e unire PDF con GroupDocs.Merger per Java –
  guida passo passo che copre split pdf java, merge pdf java, protect pdf java e altro.
is_root: true
keywords:
- split pdf java
- java combine pdf files
- groupdocs merger for java
- protect pdf java
- merge multiple pdfs java
linktitle: Tutorial su GroupDocs.Merger per Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to split PDF and merge PDFs with GroupDocs.Merger for Java
    – step-by-step guide covering split pdf java, merge pdf java, protect pdf java,
    and more.
  headline: How to Split PDF and Merge PDFs with GroupDocs.Merger for Java
  type: TechArticle
- questions:
  - answer: Instantiate a `Merger`, call `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`,
      and specify an output folder—each range becomes a separate PDF file.
    question: How do I split PDFs using GroupDocs.Merger in Java?
  - answer: Yes—GroupDocs.Merger supports cross‑format merging, allowing you to combine
      PDFs with Excel files (`merge excel files java`) into a single PDF output.
    question: Can I merge PDFs and Excel sheets together?
  - answer: After calling `merge()`, invoke `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))`
      to encrypt the final document.
    question: How do I add password protection after merging?
  - answer: Enable streaming (`Merger.setStreaming(true)`) to process files in a buffered
      fashion, which dramatically reduces memory consumption for large documents.
    question: Is it possible to merge PDFs without loading the entire file into memory?
  - answer: A commercial GroupDocs.Merger license is mandatory for production deployments;
      a free 30‑day trial is available for development and testing.
    question: What licensing is required for production use?
  type: FAQPage
title: Come dividere PDF e unire PDF con GroupDocs.Merger per Java
type: docs
url: /it/java/
weight: 10
---

# Come dividere PDF e unire PDF con GroupDocs.Merger per Java

Nelle moderne applicazioni Java, **split pdf java** è una necessità frequente—sia che tu debba suddividere un enorme rapporto in capitoli più gestibili, sia che tu voglia combinare diverse fatture in un unico archivio. GroupDocs.Merger per Java rende sia la divisione che l'unione di PDF (e oltre 50 altri formati) un gioco da ragazzi, offrendo elaborazione ad alte prestazioni con poche righe di codice. In questo tutorial esploreremo l'API principale, percorreremo scenari reali e ti indirizzeremo a tutorial più approfonditi per ogni esigenza di elaborazione documenti che potresti incontrare.

## Risposte Rapide
- **Qual è l'uso principale di GroupDocs.Merger?** Combina, divide e manipola documenti in più di 50 formati, inclusi PDF, Word, Excel e immagini.  
- **Posso dividere PDF in Java?** Sì – l'API offre un metodo dedicato “split pdf java” che consente di definire intervalli di pagine o divisioni basate sulla dimensione.  
- **Come unisco più PDF in Java?** Usa la classe `Merger` con il flusso di lavoro “merge pdf java” per unire i file istantaneamente.  
- **È disponibile la protezione con password dopo l'unione?** Assolutamente; la funzionalità “protect pdf java” cripta il risultato con una password a tua scelta.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza commerciale di GroupDocs.Merger per qualsiasi distribuzione in produzione; è disponibile una prova gratuita per la valutazione.

## Cos'è “how to merge PDFs” con GroupDocs.Merger?
`GroupDocs.Merger for Java` è una libreria che combina programmaticamente più file PDF (o qualsiasi formato supportato) in un unico documento ben strutturato. Preserva automaticamente l'ordine delle pagine, i metadati e le impostazioni di sicurezza opzionali, consentendoti di realizzare flussi di lavoro documentali complessi con un minimo di codice.

## Perché usare GroupDocs.Merger per Java?
Carica i PDF di origine, specifica le pagine desiderate e chiama `merge()`—l'API si occupa del lavoro pesante. Offre **oltre 50 formati di input e output**, elabora **centinaia di pagine al secondo** e funziona sia in ambienti on‑premises che cloud senza dipendenze esterne.

## Padroneggia la Manipolazione dei Documenti con GroupDocs.Merger

GroupDocs.Merger per Java è un'API potente che consente agli sviluppatori Java di combinare, dividere e manipolare documenti su oltre 50 popolari formati di file. La nostra serie completa di tutorial fornisce guide dettagliate, passo‑passo, su come sfruttare tutte le capacità di GroupDocs.Merger per ottimizzare i flussi di lavoro di gestione dei documenti.

Che tu abbia bisogno di **unire più PDF**, combinare documenti Word, unire fogli di calcolo, consolidare presentazioni o lavorare con immagini – questi tutorial ti aiuteranno a implementare funzionalità di elaborazione documenti robuste nelle tue applicazioni Java con un minimo di codice.

## Cosa Puoi Realizzare con GroupDocs.Merger

- **Unire più documenti** in un unico file mantenendo la formattazione e l'integrità del contenuto.  
- **Unire pagine o intervalli specifici** da diversi documenti di origine.  
- **Dividere documenti di grandi dimensioni** in file più piccoli e gestibili.  
- **Manipolare l'ordine delle pagine** tramite operazioni di spostamento, rimozione, rotazione o scambio.  
- **Proteggere i documenti** con crittografia password e gestione dei permessi.  
- **Estrarre contenuto** da sezioni specifiche del documento.  
- **Elaborare documenti** su numerosi formati includendo PDF, Word, Excel, PowerPoint e altro.

## Categorie di Tutorial di GroupDocs.Merger per Java

### [Caricamento Documenti](./document-loading/)
Padroneggia il primo passo essenziale nell'elaborazione dei documenti. Impara varie tecniche per caricare documenti da file, stream e URL con la corretta configurazione per diversi formati.

### [Informazioni sul Documento](./document-information/)
Estrai metadati preziosi dai tuoi documenti. Questi tutorial ti mostrano come accedere alle proprietà del documento, al conteggio delle pagine e ai dettagli del formato per una migliore gestione dei documenti.

### [Unione Documenti](./document-joining/)
Combina più documenti senza soluzione di continuità. Scopri come unire file interi o selezionare pagine specifiche da varie fonti in un unico documento coerente.

### [Unione Specifica per Formato](./format-specific-merging/)
Ottimizza le operazioni di unione per tipi di file specifici. Impara tecniche specializzate per unire PDF, documenti Word, fogli di calcolo Excel, presentazioni PowerPoint e altro.

### [Opzioni Avanzate di Unione](./advanced-joining-options/)
Porta l'unione dei documenti al livello successivo. Esplora scenari di unione complessi con selezione personalizzata delle pagine, unione cross‑format e opzioni di conservazione del contenuto.

### [Sicurezza Documenti](./document-security/)
Implementa una protezione robusta per i tuoi documenti. Impara ad aggiungere, rimuovere o aggiornare password, gestire i permessi e garantire la riservatezza dei documenti.

### [Operazioni su Pagine](./page-operations/)
Ottieni un controllo preciso sulle pagine del documento. Scopri tecniche per riordinare, ruotare, rimuovere e modificare pagine individuali all'interno dei tuoi documenti.

### [Estrazione Documenti](./document-extraction/)
Estrai contenuti specifici da documenti più grandi. Impara come selezionare e salvare pagine o sezioni particolari come file separati.

### [Importazione Documenti](./document-import/)
Arricchisci i documenti con contenuti esterni. Questi tutorial mostrano come importare contenuti da varie fonti, inclusi oggetti OLE e allegati.

### [Operazioni Immagine](./image-operations/)
Elabora file immagine in modo efficace. Esplora metodi per lavorare con le immagini, inclusi unire, convertire e incorporare nei documenti.

### [Divisione Documenti](./document-splitting/)
Dividi i documenti in modo strategico. Impara tecniche per dividere i file per numeri di pagina, intervalli o criteri specifici per creare più documenti di output.

### [Operazioni Testo](./text-operations/)
Manipola documenti basati su testo in modo efficiente. Scopri approcci per elaborare file di testo, inclusi unire, dividere per righe e conversione di formato.

### [Licenze](./licensing/)
Configura correttamente GroupDocs.Merger nei tuoi progetti. Scopri le opzioni di licenza, gli approcci di configurazione e le considerazioni per il deployment.

## Formati di File Supportati

GroupDocs.Merger per Java supporta un'ampia gamma di formati di documento, includendo:

- **Elaborazione di Documenti**: DOCX, DOC, RTF, ODT, DOTX, DOTM, DOT  
- **Fogli di Calcolo**: XLSX, XLS, XLSM, XLSB, ODS, XLT, XLTX  
- **Presentazioni**: PPTX, PPT, PPSX, PPS, ODP, POT  
- **Documenti Portatili**: PDF, XPS  
- **Diagrammi Visio**: VSDX, VSDM, VSTX, VSSX, VDX, VSX, VTX  
- **eBook**: EPUB  
- **Immagini**: BMP, JPG, PNG, TIFF  
- **Web**: HTML, MHT, MHTML  
- **Testo**: TXT, CSV, TSV  
- **E molto altro!** (oltre 50 formati in totale)

## Iniziare

I tutorial in questa sezione seguono un approccio pratico, code‑first, con esempi completi che puoi implementare direttamente nelle tue applicazioni. Ogni tutorial include:

- Spiegazione chiara della funzionalità e dei casi d'uso  
- Istruzioni di implementazione passo‑passo  
- Esempi di codice completi con commenti (il codice è fornito nei sotto‑tutorial collegati)  
- Opzioni di configurazione e approcci alternativi  
- Considerazioni sulle prestazioni e best practice  

Inizia a esplorare i nostri tutorial oggi per sbloccare tutto il potenziale di GroupDocs.Merger per Java nei tuoi flussi di lavoro di elaborazione documenti!

## Come Dividere PDF in Java?

Dividi un PDF in pagine individuali o intervalli personalizzati in sole tre righe di Java. Chiama il metodo `split()` su un'istanza di `Merger`, passa il percorso del file di origine e specifica l'intervallo di pagine o la dimensione desiderata. La libreria scrive ogni segmento in un file separato preservando la qualità originale e i metadati.

Puoi anche dividere per dimensione (ad esempio blocchi da 5 MB) o per un elenco di numeri di pagina, ideale per generare PDF per capitolo da un unico documento master. L'operazione viene eseguita in tempo lineare rispetto al numero di pagine, rendendola adatta per l'elaborazione batch su larga scala.

## Come Unire più PDF in Java?

Carica ogni PDF di origine con il metodo `addDocument()` di `Merger`, disponili nell'ordine desiderato e invoca `merge()`. L'API armonizza automaticamente le dimensioni delle pagine, aggiorna i segnalibri e consolida le proprietà del documento. Puoi anche unire PDF con altri formati—come Word o Excel—convertendoli al volo, ottenendo un unico output PDF unificato.

Per scenari ad alta velocità, abilita la modalità streaming per evitare di caricare interi file in memoria. Questo riduce l'uso dell'heap fino all'80 % quando si elaborano documenti con centinaia di pagine.

## Comprendere la Classe Merger

La classe `Merger` è il componente centrale di GroupDocs.Merger per Java che orchestra le operazioni di combinazione, divisione e sicurezza dei documenti. Espone metodi fluenti come `addDocument()`, `split()`, `protect()` e `merge()` per costruire pipeline di elaborazione concise.

### Panoramica dei Metodi Chiave
- `addDocument(String path)`: Accoda un file di origine per l'unione successiva.  
- `split(String source, SplitOptions options)`: Divide un documento basandosi su intervalli di pagine o limiti di dimensione.  
- `protect(String output, ProtectionOptions options)`: Applica protezione con password e restrizioni di permessi.  
- `merge(String output)`: Esegue le operazioni accodate e scrive il documento finale.  

Questi metodi sono thread‑safe e possono essere concatenati per un codice espressivo e leggibile.

## Problemi Comuni e Soluzioni

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| **Errori di out‑of‑memory su PDF di grandi dimensioni** | Caricamento dell'intero file in memoria | Abilita la modalità streaming (`Merger.setStreaming(true)`) o dividi il file in blocchi più piccoli prima dell'unione. |
| **Disallineamento dell'orientamento delle pagine** | I PDF di origine hanno pagine miste portrait/landscape | Usa `rotatePage(int pageNumber, RotationAngle angle)` prima dell'unione per standardizzare l'orientamento. |
| **Impossibile aprire la sorgente protetta da password** | Mancanza della password di decrittazione | Fornisci la password tramite `DocumentLoadOptions.setPassword("yourPwd")` quando aggiungi il documento. |
| **Metadati persi dopo l'unione** | L'unione predefinita scarta i metadati personalizzati | Chiama `setPreserveMetadata(true)` sull'istanza `Merger` per mantenere le proprietà originali. |

## Domande Frequenti

**D: Come divido i PDF usando GroupDocs.Merger in Java?**  
R: Istanzia un `Merger`, chiama `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))` e specifica una cartella di output—ogni intervallo diventa un file PDF separato.

**D: Posso unire PDF e fogli Excel insieme?**  
R: Sì—GroupDocs.Merger supporta l'unione cross‑format, consentendo di combinare PDF con file Excel (`merge excel files java`) in un unico output PDF.

**D: Come aggiungo la protezione con password dopo l'unione?**  
R: Dopo aver chiamato `merge()`, invoca `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))` per criptare il documento finale.

**D: È possibile unire PDF senza caricare l'intero file in memoria?**  
R: Abilita lo streaming (`Merger.setStreaming(true)`) per elaborare i file in modalità bufferizzata, riducendo drasticamente il consumo di memoria per documenti di grandi dimensioni.

**D: Quale licenza è necessaria per l'uso in produzione?**  
R: È obbligatoria una licenza commerciale di GroupDocs.Merger per le distribuzioni in produzione; è disponibile una prova gratuita di 30 giorni per sviluppo e test.

---

**Ultimo Aggiornamento:** 2026-06-16  
**Testato Con:** GroupDocs.Merger for Java 23.12 (latest at time of writing)  
**Autore:** GroupDocs

## Tutorial Correlati

- [Unire PDF Efficientemente Usando GroupDocs.Merger per Java: Guida Passo‑Passo](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [Come Unire File DOCX Facilmente con GroupDocs.Merger per Java: Guida Passo‑Passo](/merger/java/format-specific-merging/merge-docx-files-groupdocs-merger-java/)
- [Come Unire File PowerPoint in Java Usando GroupDocs.Merger: Guida Passo‑Passo](/merger/java/format-specific-merging/merge-powerpoint-files-java-groupdocs-merger-guide/)