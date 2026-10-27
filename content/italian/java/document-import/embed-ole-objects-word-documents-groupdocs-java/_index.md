---
date: '2026-10-27'
description: Scopri come incorporare PDF nei documenti Word e aggiungere PDF ai file
  Word con GroupDocs.Merger for Java. Tutorial passo‑passo per un'integrazione OLE
  senza interruzioni.
keywords:
- how to embed pdf in word
- embed pdf in word document
- embed pdf as ole
- embed multiple pdfs word
- add pdf icon to word
lastmod: '2026-10-27'
og_description: Scopri come incorporare PDF in Word con GroupDocs.Merger for Java.
  Segui questo tutorial conciso per aggiungere PDF come oggetti OLE nei documenti
  Word.
og_image_alt: Guide showing how to embed PDF files into Word documents using GroupDocs.Merger
  for Java
og_title: Come incorporare PDF in Word usando GroupDocs.Merger for Java – Guida passo‑passo
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber
  - name: configure OleWordProcessingOptions
    text: '`OleWordProcessingOptions` controls the visual representation of the embedded
      object. You can align the object to the left, center, or right, add a caption
      underneath, and even specify whether the embedded file should be displayed as
      an icon or as a preview. - **`setWidth()` / `setHeight()`** – cont'
  - name: initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (optional) re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- Java document processing
- OLE embedding
- Word automation
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: Define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber`** – the page that will
      host the OLE object.
  - name: Configure OleWordProcessingOptions
    text: The `OleWordProcessingOptions` class defines how the OLE object looks inside
      the Word document. You can set width, height, alignment, and even a caption.
      - **`setWidth()` / `setHeight()`** – control how large the PDF icon appears
      inside the Word document.
  - name: Initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (Optional) Re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
title: Come incorporare PDF in Word usando GroupDocs.Merger for Java – Guida completa
type: docs
url: /it/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# Come incorporare pdf in word usando GroupDocs.Merger per Java

Incorporare un PDF direttamente all'interno di un documento Word può migliorare notevolmente la collaborazione, poiché i lettori non devono più passare da un file all'altro. In questa guida scoprirai **come incorporare pdf in word** documenti usando GroupDocs.Merger per Java, e vedrai consigli pratici su **aggiungere pdf a word** nei flussi di lavoro. Ti guideremo passo passo da come configurare la libreria alla personalizzazione di dimensioni e posizione dell'oggetto OLE, così potrai automatizzare la creazione dei documenti con fiducia.

## Risposte rapide
- **Quale libreria è necessaria?** GroupDocs.Merger for Java (ultima versione)  
- **Posso incorporare qualsiasi tipo di file?** Sì – PDF, immagini, fogli di calcolo, ecc., come oggetti OLE  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è necessaria una licenza commerciale per la produzione  
- **Quale IDE Java funziona meglio?** IntelliJ IDEA, Eclipse, o qualsiasi IDE che supporti Maven/Gradle  
- **Quanto tempo richiede l'implementazione?** Circa 10‑15 minuti per un'integrazione di base  

## Cos'è incorporare pdf in word?
Incorporare un PDF crea un oggetto OLE (Object Linking and Embedding) all'interno del file Word, consentendo al PDF di essere aperto direttamente dal documento. Il file incorporato mantiene la formattazione e l'interattività originali, mentre il documento Word rimane un unico pacchetto autonomo. Questo approccio semplifica la distribuzione, garantisce la coerenza delle versioni e offre ai lettori un accesso immediato al materiale supplementare senza uscire dall'ambiente Word.

## Perché aggiungere pdf a word usando GroupDocs.Merger?
GroupDocs.Merger automatizza l'inserimento OLE, la regolazione delle dimensioni e il posizionamento, eliminando la necessità di modifiche manuali. La libreria elabora fino a **30+ formati di input e output** e può incorporare **centinaia di PDF** in un unico batch mantenendo l'uso della memoria sotto **200 MB** su una JVM tipica. Questa scalabilità la rende ideale per documentazione su larga scala, contratti o kit di marketing.

## Prerequisiti
- **Librerie e dipendenze:** Includi la libreria GroupDocs.Merger via Maven o Gradle.  
- **Ambiente di sviluppo:** IntelliJ IDEA, Eclipse, o qualsiasi IDE Java.  
- **Conoscenze di base:** Familiarità con Java e i concetti di manipolazione dei documenti.  

## Come configuro GroupDocs.Merger per Java?
Per iniziare, aggiungi la libreria GroupDocs.Merger al tuo progetto usando Maven, Gradle o un download manuale del JAR. Dopo che la dipendenza è stata risolta, importa le classi principali come `Merger`, `OleWordProcessingOptions` e le utility I/O necessarie. Assicurati che il tuo progetto utilizzi Java 8 o versioni successive e che la versione della libreria corrisponda alla tua licenza.

### Maven
Aggiungi questa dipendenza al tuo file `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Include questo nel tuo file `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Download diretto
In alternativa, scarica l'ultima versione dalla [pagina di rilascio di GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/).

**Acquisizione licenza:** Puoi iniziare con una prova gratuita o ottenere una licenza temporanea per valutare le funzionalità prima di acquistare. Visita [Purchase GroupDocs](https://purchase.groupdocs.com/buy) per maggiori dettagli.

## Come funziona l'inizializzazione di base?
La classe `Merger` è il punto di ingresso per tutte le operazioni di elaborazione dei documenti in GroupDocs.Merger per Java. Dopo aver creato un'istanza di `Merger`, puoi chiamare metodi come `importDocument` per incorporare oggetti OLE. Importa le classi necessarie per lavorare con gli oggetti OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Come posso incorporare un PDF in un documento Word passo‑per‑passo?
Incorporare un PDF comporta il caricamento del file Word di origine, la creazione di un'istanza `OleWordProcessingOptions` per definire l'aspetto, e la chiamata a `importDocument` con il percorso del PDF e le opzioni. La libreria inserisce l'oggetto OLE nella posizione specificata, dopodiché salvi il documento per produrre un file autonomo.

### Passo 1: definire i percorsi dei file e la pagina di destinazione
Imposta il documento Word di origine, il PDF che desideri incorporare e dove dovrebbe apparire l'oggetto OLE.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – percorso del file Word esistente.  
- **`embeddedFilePath`** – il PDF che vuoi **aggiungere pdf a word**.  
- **`outputFilePath`** – dove verrà salvato il nuovo documento.  
- **`pageNumber`** – la pagina che ospiterà l'oggetto OLE.

### Passo 2: configurare OleWordProcessingOptions
`OleWordProcessingOptions` controlla la rappresentazione visiva dell'oggetto incorporato. Puoi allineare l'oggetto a sinistra, al centro o a destra, aggiungere una didascalia sotto, e persino specificare se il file incorporato deve essere visualizzato come icona o come anteprima.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – controllano la dimensione dell'icona PDF all'interno del documento Word.

### Passo 3: inizializzare Merger e importare l'oggetto OLE
Crea un'istanza `Merger` per il documento di origine, importa l'oggetto OLE e salva il risultato.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```
- **`importDocument()`** – accetta `OleWordProcessingOptions` e inserisce il PDF come oggetto OLE.  
- **`save()`** – scrive il documento modificato su `outputFilePath`.

### Passo 4: (opzionale) riapplicare la configurazione per oggetti aggiuntivi
Se devi incorporare altri PDF, ripeti **Passo 1‑3** con nuovi percorsi file e numeri di pagina. La stessa classe `OleWordProcessingOptions` ti consente di controllare ogni oggetto individualmente.

## Come posso configurare OleWordProcessingOptions per scenari avanzati?
`OleWordProcessingOptions` è il centro di configurazione per l'incorporamento OLE. Puoi allineare l'oggetto a sinistra, al centro o a destra, aggiungere una didascalia sotto, e persino specificare se il file incorporato deve essere visualizzato come icona o come anteprima. Il frammento di codice qui sotto ripete la configurazione di base per chiarezza:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Quali sono le applicazioni pratiche dell'incorporamento di PDF in Word?
Incorporare PDF è utile in molti contesti professionali perché mantiene i contenuti correlati insieme preservando la formattazione originale di ogni file. Ad esempio, i manuali tecnici possono includere schemi dettagliati, i rapporti finanziari possono allegare dichiarazioni di audit, i contratti legali possono incorporare allegati, e i depliant di marketing possono includere schede tecniche di prodotto—tutto senza richiedere download separati o link esterni.

## Come influiscono le considerazioni sulle prestazioni sui documenti di grandi dimensioni?
Durante l'elaborazione di file Word di grandi dimensioni o di più oggetti OLE, gestisci memoria e I/O in modo efficiente. Rimuovi contenuti non necessari, incorpora solo le pagine richieste e assegna sufficiente spazio heap JVM usando il flag `-Xmx`. Le recenti versioni di GroupDocs.Merger migliorano la velocità di elaborazione fino al **35 %** per documenti con più di **200 pagine**, e riducono il consumo di memoria di picco di circa **40 %** rispetto alle versioni precedenti.

## Quali problemi comuni potrei incontrare e come risolverli?
I problemi tipici includono percorsi file errati, errori di out‑of‑memory, PDF di origine corrotti e icone OLE mancanti. Assicurati che i percorsi di Word e PDF siano assoluti o correttamente relativi alla radice del progetto, aumenta la dimensione dell'heap JVM per batch di grandi dimensioni, verifica che ogni PDF si apra normalmente prima dell'incorporamento e conferma che il modello Word di destinazione consenta l'inserimento OLE. Regolare questi fattori di solito risolve la maggior parte dei fallimenti di incorporamento.

## Domande frequenti

**Q: Cos'è l'incorporamento OLE?**  
A: L'incorporamento consente di inserire oggetti come PDF nei documenti Word come collegamenti che mantengono la loro funzionalità originale.

**Q: Posso incorporare più oggetti OLE in un documento?**  
A: Sì, ognuno può essere configurato per pagine e dimensioni diverse usando `OleWordProcessingOptions` separati.

**Q: Esiste un limite alla dimensione dei file incorporati?**  
A: Il limite è generalmente determinato dalle restrizioni di Word, ma GroupDocs.Merger gestisce file di grandi dimensioni in modo efficiente.

**Q: Come risolvere gli errori di incorporamento?**  
A: Verifica che i percorsi dei file siano corretti e che la JVM abbia abbastanza memoria. Controlla che il PDF di origine non sia corrotto.

**Q: Posso modificare gli oggetti incorporati dopo l'inserimento?**  
A: Puoi riaprire il file Word in Microsoft Word e modificare l'oggetto OLE, o rieseguire il codice Merger con opzioni aggiornate.

## Risorse aggiuntive
- [Documentazione GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Riferimento API](https://reference.groupdocs.com/merger/java/)
- [Scarica l'ultima versione](https://releases.groupdocs.com/merger/java/)
- [Acquista GroupDocs](https://purchase.groupdocs.com/buy)
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Forum di supporto](https://forum.groupdocs.com/c/merger/)

---

**Ultimo aggiornamento:** 2026-10-27  
**Testato con:** GroupDocs.Merger for Java latest version  
**Autore:** GroupDocs  

---

## Tutorial correlati

- [Come incorporare PDF in Excel usando GroupDocs.Merger per Java - Importare un oggetto OLE – Guida passo‑per‑passo](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [Incorporare immagini come oggetti OLE in Java con GroupDocs.Merger: Guida completa](/merger/java/image-operations/embed-images-ole-java-groupdocs-merger/)
- [Aggiungere allegato PDF usando GroupDocs.Merger per Java – Guida completa](/merger/java/format-specific-merging/embed-documents-pdf-groupdocs-merger-java/)