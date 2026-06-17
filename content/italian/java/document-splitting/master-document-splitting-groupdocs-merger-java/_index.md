---
date: '2026-05-22'
description: Scopri come dividere PDF in pagine usando GroupDocs.Merger per Java –
  configurazione passo‑passo, flusso di lavoro senza codice e casi d'uso reali.
keywords:
- split pdf into pages
- split pdf java
- extract pdf pages java
- GroupDocs.Merger for Java
- document splitting in Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to split pdf into pages using GroupDocs.Merger for Java –
    step‑by‑step setup, code‑free workflow, and real‑world use cases.
  headline: split pdf into pages with GroupDocs.Merger for Java
  type: TechArticle
- questions:
  - answer: '`split` creates a separate file for each page or range, while `extract`
      combines selected pages into a single new document.'
    question: What is the difference between `split` and `extract` in GroupDocs.Merger?
  - answer: Yes—initialize `Merger` with the password parameter before invoking `split()`.
    question: Can I split password‑protected PDFs?
  - answer: Absolutely. The same API works for DOCX, PPTX, XLSX, HTML, and over 50
      image formats.
    question: Does the library support formats other than PDF?
  - answer: Process them in smaller page ranges, increase the JVM heap, and rely on
      the streaming API to avoid loading the entire file into memory.
    question: How should I handle PDFs that are several hundred megabytes?
  - answer: Yes—a valid license removes trial limits and grants access to premium
      support; a trial license is sufficient for development and testing.
    question: Is a commercial license mandatory for production use?
  type: FAQPage
title: Dividi PDF in pagine con GroupDocs.Merger per Java
type: docs
url: /it/java/document-splitting/master-document-splitting-groupdocs-merger-java/
weight: 1
---

# Dividi PDF in pagine con GroupDocs.Merger per Java

If you need to **split pdf into pages** quickly and reliably in a Java application, you’ve come to the right place. In many projects—whether you’re building a document‑management system, a legal review workflow, or an academic publishing pipeline—breaking a large PDF into single‑page files is a common requirement. This tutorial shows you how to achieve that using **GroupDocs.Merger for Java**, a high‑performance library that handles PDFs, DOCX, PPTX, and many other formats without loading the whole file into memory.

## Risposte rapide
- **Cosa fa “split pdf into pages”?** It extracts each page (or a page range) from a source PDF and saves them as independent PDF files.  
- **Quale libreria è la migliore per questo compito?** GroupDocs.Merger for Java offers the most complete API for splitting, merging, and page‑level manipulation.  
- **Ho bisogno di una licenza per la produzione?** Yes—a commercial license removes trial limits; a free trial is fine for development.  
- **Posso dividere per intervalli personalizzati?** Absolutely—use `SplitOptions` to specify start and end pages.  
- **Il processo è efficiente in termini di memoria?** The library streams pages, so even 500‑page PDFs use less than 100 MB of heap.

## Cos'è split pdf into pages?
**Dividere un PDF in pagine significa estrarre programmaticamente ogni pagina (o un intervallo definito) da un documento di origine e creare file PDF separati per ogni pagina estratta.** Questa operazione è essenziale per flussi di lavoro che richiedono accesso granulare a pagine individuali, come instradamento automatico, stampa selettiva o analisi per pagina.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger elabora **oltre 50 formati di input e output**—inclusi PDF, DOCX, PPTX, HTML e tipi di immagine—mantendo un basso utilizzo di memoria. Può gestire **PDF con centinaia di pagine** in meno di un secondo su hardware server tipico, grazie alla sua architettura di streaming. L'API è intenzionalmente semplice: poche classi (`Merger`, `SplitOptions`) ti consentono di dividere, unire o estrarre pagine con una singola chiamata di metodo.

## Prerequisiti
- **JDK 8+** installato e configurato nel tuo PATH.  
- Un IDE come **IntelliJ IDEA** o **Eclipse** (opzionale ma consigliato).  
- **Maven** o **Gradle** per la gestione delle dipendenze.  
- Accesso alla libreria **GroupDocs.Merger for Java** (download o aggiungi via Maven/Gradle).  

### Librerie e dipendenze richieste
- **GroupDocs.Merger for Java** – aggiungi l'ultima versione al tuo progetto.

  - **Maven**:  
    ```xml
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>latest-version</version>
    </dependency>
    ```

  - **Gradle**:  
    ```gradle
    implementation 'com.groupdocs:groupdocs-merger:latest-version'
    ```

  - **Download diretto**: Puoi anche ottenere il JAR dalla pagina di rilascio ufficiale – [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

## Configurazione di GroupDocs.Merger per Java

### Informazioni sull'installazione
Add the dependency using Maven or Gradle as shown above, or download the JAR manually from the release page – [here](https://releases.groupdocs.com/merger/java/).

### Ottenimento della licenza
Before running any code, obtain a license to avoid trial restrictions:

- **Prova gratuita** – unlimited feature access for 30 days.  
- **Licenza temporanea** – extended testing period for enterprises.  
- **Licenza completa** – removes all usage limits and provides priority support.  

### Inizializzazione e configurazione di base
The `Merger` class is the entry point for all document‑manipulation operations in GroupDocs.Merger. After adding the library to your classpath, you can create a `Merger` instance that points to the source PDF.

```java
import com.groupdocs.merger.Merger;

public class InitializeMerger {
    public static void main(String[] args) throws Exception {
        // Specify the path to your document
        String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
        
        // Initialize Merger with the specified file path
        Merger merger = new Merger(filePath);
        
        System.out.println("Merger initialized successfully!");
    }
}
```

## Come dividere pdf in pagine per intervallo di pagine?
`SplitOptions` definisce l'intervallo di pagine e le opzioni di output per l'operazione di divisione.  
Carica il PDF di origine con `new Merger("source.pdf")`, configura `SplitOptions` per l'intervallo di pagine desiderato e chiama `split()`—l'intera operazione si completa in due righe di codice. Questo approccio trasmette in streaming ogni pagina, quindi anche i PDF di grandi dimensioni vengono elaborati con un minimo consumo di memoria.

### Passo 1: Importa le librerie richieste
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.SplitOptions;
```

### Passo 2: Definisci i percorsi dei file
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRange-Output.docx";
```

### Passo 3: Configura SplitOptions
`SplitOptions` lets you set the start and end pages and customize output file naming.  
```java
// Create SplitOptions specifying pages 3 to 7
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7);
```

The constructor arguments are:

- **filePathOut** – cartella di destinazione per i file divisi.  
- **Start Page (3)** – prima pagina dell'intervallo che desideri estrarre.  
- **End Page (7)** – ultima pagina dell'intervallo.

### Passo 4: Esegui l'operazione di divisione
```java
// Initialize the Merger with the input document path
Merger merger = new Merger(filePath);

// Perform the split operation based on specified options
merger.split(splitOptions);
```

After execution, you’ll find separate one‑page PDFs for pages 3‑7 inside the output folder.

## Funzionalità: Importa le librerie richieste e imposta i percorsi dei file
This helper snippet demonstrates how to build dynamic output paths, which is handy when you need to **create single page java** files programmatically.

```java
import java.nio.file.Paths;
import java.io.File;
```

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
// Construct output file path with dynamic filename component
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY",
    "SplitToSinglePagesByRange-" + Paths.get(filePath).getFileName().toString()).getPath();
```

## Applicazioni pratiche
Here are a few real‑world scenarios where **split pdf into pages** shines:

1. **Sistemi di gestione documentale** – automatically break large contracts into individual clauses for version control.  
2. **Studi legali** – provide each party a single‑page PDF of the relevant section, speeding up review cycles.  
3. **Ambito accademico** – distribute exam pages or lecture slides as separate files for printing or grading.  
4. **Flussi di lavoro editoriali** – split manuscript chapters into separate PDFs for editors, reducing upload times.

Integrating this logic with a CMS or CRM can further automate document delivery pipelines.

## Considerazioni sulle prestazioni
When handling massive PDFs, keep these tips in mind:

- **JVM Heap** – allocate sufficient memory (`-Xmx2g` or higher) for very large files.  
- **I/O in streaming** – GroupDocs.Merger streams pages, keeping peak memory under 100 MB for 500‑page documents.  
- **Pulizia delle risorse** – always close the `Merger` instance or use try‑with‑resources to release file handles.

## Problemi comuni e soluzioni
- **File non trovato** – verify the absolute path and file permissions.  
- **Errori di permesso** – ensure the output directory is writable by the Java process.  
- **Out‑Of‑Memory** – increase JVM heap size or split the document into smaller ranges.

## Domande frequenti

**D: Qual è la differenza tra `split` ed `extract` in GroupDocs.Merger?**  
R: `split` creates a separate file for each page or range, while `extract` combines selected pages into a single new document.

**D: Posso dividere PDF protetti da password?**  
R: Yes—initialize `Merger` with the password parameter before invoking `split()`.

**D: La libreria supporta formati diversi da PDF?**  
R: Absolutely. The same API works for DOCX, PPTX, XLSX, HTML, and over 50 image formats.

**D: Come devo gestire PDF di diverse centinaia di megabyte?**  
R: Process them in smaller page ranges, increase the JVM heap, and rely on the streaming API to avoid loading the entire file into memory.

**D: È obbligatoria una licenza commerciale per l'uso in produzione?**  
R: Yes—a valid license removes trial limits and grants access to premium support; a trial license is sufficient for development and testing.

## Conclusione
You now have a complete, production‑ready approach to **split pdf into pages** using GroupDocs.Merger for Java. This capability lets you build smarter document pipelines, improve performance, and deliver content exactly where it’s needed. Try different page ranges, combine splitting with merging or conversion, and embed the solution into your existing Java services for maximum impact.

---

**Last Updated:** 2026-05-22  
**Tested With:** GroupDocs.Merger 23.9 (latest)  
**Author:** GroupDocs

## Tutorial correlati

- [Estrai in batch le pagine PDF con GroupDocs.Merger per Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java/)
- [Gestisci la divisione di documenti per intervallo di pagine con GroupDocs.Merger per Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Ruota le pagine PDF in Java usando GroupDocs.Merger: Guida passo‑passo](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)