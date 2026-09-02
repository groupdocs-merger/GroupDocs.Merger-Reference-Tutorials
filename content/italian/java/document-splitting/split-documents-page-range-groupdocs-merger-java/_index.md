---
date: '2026-07-25'
description: Scopri come dividere le pagine dei documenti Word usando GroupDocs.Merger
  per Java, con esempi passo‑passo per PDF, DOCX e PPTX, oltre ai filtri di pagine
  dispari/pari.
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Scopri come dividere le pagine dei documenti Word usando GroupDocs.Merger
  per Java, con esempi passo‑passo per PDF, DOCX e PPTX, oltre ai filtri di pagine
  dispari/pari.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Dividi le pagine dei documenti Word con GroupDocs.Merger per Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Dividi le pagine dei documenti Word con GroupDocs.Merger per Java
type: docs
url: /it/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Dividi le pagine dei documenti Word con GroupDocs.Merger per Java

In questo tutorial imparerai come **dividere le pagine dei documenti Word**—e altri formati come PDF e PPTX—usando GroupDocs.Merger per Java. Che tu debba estrarre una singola clausola di un contratto, generare dispense da una presentazione, o suddividere un rapporto enorme in parti gestibili, l'API ti consente di specificare intervalli di pagine precisi, filtri dispari/pari o output a pagina singola con poche righe di codice.

## Risposte rapide
- **Cosa significa “estrarre pagine specifiche”?** Significa creare nuovi documenti che contengono solo le pagine che selezioni dal file sorgente.  
- **Quali formati sono supportati?** PDF, DOCX, PPTX e molti altri formati popolari.  
- **Posso filtrare per pagine dispari o pari?** Sì, usando l'opzione `RangeMode` (ad es., `OddPages`).  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per la valutazione; è necessaria una licenza permanente per la produzione.  
- **È adatto per documenti di grandi dimensioni?** Sì—dividi le sezioni di documenti grandi per mantenere basso l'uso di memoria.

## Cos'è l'estrazione di pagine specifiche?
Estrarre pagine specifiche significa prendere un sottoinsieme selezionato di pagine da un documento originale e creare un nuovo file indipendente che contiene solo quelle pagine. Questa tecnica è utile per generare report mirati, condividere clausole contrattuali individuali o distribuire diapositive specifiche di una presentazione senza esporre l'intero documento sorgente.

## Perché usare GroupDocs.Merger per Java per dividere PDF e documenti Word?
Carica solo le pagine di cui hai bisogno e lascia che GroupDocs.Merger gestisca il lavoro pesante. La libreria supporta **oltre 50 formati di input e output**, può elaborare file fino a **2 GB** senza caricare l'intero documento in memoria, e fornisce un'API coerente per PDF, DOCX, PPTX e altri—così eviti di dover utilizzare più strumenti.

## Prerequisiti
- **GroupDocs.Merger for Java** (ultima versione)  
- **JDK 8+**  
- Un IDE come IntelliJ IDEA o Eclipse  
- Maven o Gradle per la gestione delle dipendenze  

## Configurazione di GroupDocs.Merger per Java
Aggiungi la libreria al tuo progetto usando lo strumento di build preferito.

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Download diretto**: Puoi anche scaricare la libreria direttamente da [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza
Puoi ottenere una licenza tramite:
- **Free Trial** – Prova tutte le funzionalità senza limitazioni.  
- **Temporary License** – Periodo di valutazione esteso.  
- **Purchase** – Licenza permanente per la produzione.

**Inizializzazione e configurazione di base**  
La classe `Merger` è il punto di ingresso per tutte le operazioni di divisione. Rappresenta un documento in memoria e fornisce metodi per manipolare le pagine. Per inizializzare GroupDocs.Merger, crea un'istanza di `Merger` con il percorso del tuo documento:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Come estrarre pagine specifiche usando GroupDocs.Merger per Java
Per estrarre pagine specifiche, carica il documento sorgente con un'istanza `Merger`, configura un oggetto `SplitOptions` con le pagine di inizio e fine desiderate e, facoltativamente, imposta `RangeMode` (ad es., `OddPages` o `EvenPages`). Quindi chiama `merger.split(options)` che crea nuovi file contenenti solo le pagine selezionate.

### Risposta diretta
Crea un'istanza `Merger`, configura un oggetto `SplitOptions` con `RangeMode.OddPages` e le pagine di inizio/fine desiderate, quindi chiama `merger.split(options)`. Questo flusso in un solo passaggio estrae solo le pagine dispari all'interno dell'intervallo specificato e le scrive nel modello di output fornito.

### Passo 1: Definire i percorsi di input e output
Imposta il file sorgente e il modello di destinazione per i file divisi:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Passo 2: Configurare le opzioni di divisione (Intervallo e filtro)
La classe `SplitOptions` indica alla libreria quali pagine estrarre e quale filtro applicare. `RangeMode` è un'enumerazione che specifica quali pagine includere, come dispari, pari o tutte le pagine. La proprietà `filePathOut` definisce il modello di denominazione, mentre `startPage` e `endPage` impostano l'intervallo inclusivo. `RangeMode.OddPages` mantiene solo le pagine dispari all'interno di quell'intervallo, estraendo effettivamente **pagine specifiche**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Passo 3: Eseguire l'operazione di divisione
Esegui la divisione usando le opzioni configurate:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Suggerimenti per la risoluzione dei problemi
- Verifica che i percorsi dei file siano corretti e accessibili.  
- Assicurati che i numeri di pagina siano entro il conteggio totale delle pagine del documento; altrimenti verrà generata un'eccezione.  

## Come dividere un PDF in pagine singole (split pdf single pages)
Per dividere un PDF in pagine individuali, apri il file con un'istanza `Merger` e imposta `RangeMode.AllPages` in un oggetto `SplitOptions`. Specifica un modello di denominazione per l'output, quindi invoca `merger.split(options)`. La libreria genererà un file PDF separato per ogni pagina, preservando il contenuto e la formattazione originali.

## Come dividere un documento grande in modo efficiente (split large document)
Quando si elaborano documenti molto grandi, dividili in intervalli di pagine più piccoli (ad es., 1‑100, 101‑200) per ridurre il consumo di memoria. Crea `SplitOptions` separate per ogni intervallo, esegui `merger.split(options)` in sequenza e chiudi l'istanza `Merger` dopo ogni batch. Questo approccio mantiene gestibili l'uso della CPU e dell'I/O.

## Come dividere le pagine dispari di un PDF (split pdf odd pages)
Per estrarre solo le pagine dispari da un PDF, configura un oggetto `SplitOptions` con `RangeMode.OddPages`. Imposta il modello di output desiderato e, facoltativamente, definisci un intervallo di pagine se non ti serve l'intero documento. Chiama `merger.split(options)` e la libreria produrrà file contenenti solo le pagine dispari.

## Applicazioni pratiche
1. **Document Segmentation** – Suddividi i contratti in PDF a livello di clausola per una revisione più semplice.  
2. **Report Management** – Estrai un capitolo o un'appendice specifici da un lungo rapporto annuale.  
3. **Presentation Preparation** – Isola diapositive individuali per riunioni mirate.  

Puoi anche integrare questa logica con database o sistemi di gestione dei contenuti per automatizzare i flussi di lavoro.

## Considerazioni sulle prestazioni
- **Memory Management** – Chiama `merger.close()` (o affidati a try‑with‑resources) dopo l'elaborazione per rilasciare i handle dei file.  
- **Selective Ranges** – Richiedi solo le pagine di cui hai realmente bisogno; questo minimizza l'uso di I/O e CPU.  

## Conclusione
Ora disponi di un metodo chiaro, passo dopo passo, per **dividere le pagine dei documenti Word** (e altri formati supportati) usando GroupDocs.Merger per Java. Questa funzionalità semplifica i tuoi flussi di lavoro sui documenti e ti consente di fornire esattamente il contenuto di cui i tuoi utenti hanno bisogno.

### Prossimi passi
- Sperimenta con diversi valori di `RangeMode` (ad es., `EvenPages`, `AllPages`).  
- Combina la divisione con la funzionalità di **merge** per riordinare o concatenare le pagine estratte.  
- Esplora l'intera API per documenti protetti da password, filigrane e altro.  

## Domande frequenti
**Q: Che cos'è GroupDocs.Merger per Java?**  
A: GroupDocs.Merger per Java è una libreria robusta che consente di unire, dividere e riordinare pagine su molti formati di documento, inclusi PDF, DOCX e PPTX.

**Q: Posso usare GroupDocs.Merger con altri linguaggi di programmazione?**  
A: Sì, esistono capacità simili per .NET e C++.

**Q: Come gestisco le eccezioni durante l'elaborazione dei documenti?**  
A: `MergerException` è il tipo di eccezione lanciata da GroupDocs.Merger quando si verifica un errore di elaborazione. Avvolgi le chiamate in blocchi `try‑catch` e ispeziona `MergerException` per informazioni dettagliate sull'errore.

**Q: È possibile dividere i documenti senza filtrare per pagine dispari/pari?**  
A: Assolutamente—imposta `RangeMode.AllPages` o ometti il parametro di filtro per dividere per numeri di pagina esatti.

**Q: Quali sono i requisiti di sistema per usare GroupDocs.Merger?**  
A: Java 8 o superiore e un IDE compatibile; non sono richieste dipendenze native aggiuntive.

## Risorse
- [Documentazione di GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Riferimento API](https://reference.groupdocs.com/merger/java/)
- [Scarica la libreria](https://releases.groupdocs.com/merger/java/)
- [Acquista licenza](https://purchase.groupdocs.com/buy)
- [Prova gratuita e licenza temporanea](https://releases.groupdocs.com/merger/java/)
- [Forum di supporto](https://forum.groupdocs.com/c/merger/)

---

**Ultimo aggiornamento:** 2026-07-25  
**Testato con:** ultima versione di GroupDocs.Merger (Java)  
**Autore:** GroupDocs

## Tutorial correlati
- [Rimuovere efficientemente pagine da documenti Word usando GroupDocs.Merger per Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Gestione avanzata dei documenti - Unire documenti Word con GroupDocs.Merger per Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Come dividere i documenti in file multi-pagina usando GroupDocs.Merger per Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)