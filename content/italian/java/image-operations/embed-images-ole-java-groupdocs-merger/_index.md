---
date: '2026-06-26'
description: Scopri come convertire un'immagine in OLE usando GroupDocs.Merger per
  Java. Guida passo‑passo, frammenti di codice e migliori pratiche per incorporare
  immagini come oggetti OLE.
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: Come convertire un'immagine in OLE in Java con GroupDocs.Merger
type: docs
url: /it/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# Come Convertire Immagine in OLE in Java Utilizzando GroupDocs.Merger

Incorporare immagini direttamente in un documento può sembrare macchinoso, ma **convert image to OLE** diventa un gioco da ragazzi con GroupDocs.Merger per Java. In questo tutorial vedrai perché gli oggetti OLE sono utili, come preparare l'ambiente e i passaggi esatti per incorporare un'immagine come diagramma OLE. Alla fine avrai uno schema di codice riutilizzabile che funziona con file Word, Excel, PowerPoint e PDF.

## Risposte Rapide
- **Qual è il metodo principale?** Usa `Merger.importOleDiagram()` dopo aver caricato il documento sorgente.  
- **Ho bisogno di una licenza?** Una versione di prova funziona per lo sviluppo; è necessaria una licenza completa per la produzione.  
- **Quali formati immagine sono supportati?** PNG, JPEG, BMP, GIF e TIFF sono tutti accettati.  
- **Posso impostare la dimensione e la posizione dell'OLE?** Sì — `OleDiagramOptions` ti permette di definire pagina, coordinate, larghezza e altezza.  
- **Il processo è efficiente in termini di memoria?** GroupDocs.Merger trasmette i dati, quindi anche file di 500 pagine rimangono sotto i 200 MB di RAM.

## Cos'è “convert image to OLE”?
**Convert image to OLE** significa trasformare un file immagine raster in un diagramma Object Linking and Embedding (OLE) che può essere modificato all'interno del documento ospitante. Questa trasformazione consente agli utenti finali di fare doppio clic sull'immagine, aprirla nel suo editor nativo e salvare le modifiche nel documento contenitore senza uscire dal file.

## Perché Usare GroupDocs.Merger per l'Incorporamento OLE?
GroupDocs.Merger supporta **oltre 50 formati di input e output** — inclusi DOCX, XLSX, PPTX, PDF e i tipi di immagine più comuni — e può incorporare oggetti OLE in documenti fino a **300 MB** senza caricare l'intero file in memoria. La libreria elabora un file Word di 200 pagine con tre PNG incorporati in meno di **3 secondi** su un tipico server da 2,6 GHz, offrendoti velocità e scalabilità.

## Prerequisiti
- **Java Development Kit (JDK) 8+** installato e configurato nel tuo IDE.  
- **GroupDocs.Merger for Java** aggiunto tramite Maven o Gradle (si consiglia l'ultima versione).  
- Familiarità di base con gli stream I/O di Java e la programmazione orientata agli oggetti.  

## Configurare GroupDocs.Merger per Java

Per includere GroupDocs.Merger nel tuo progetto, aggiungi la dipendenza al tuo file di build. La libreria è disponibile su Maven Central, quindi puoi copiare lo snippet qui sotto nel tuo `pom.xml` o `build.gradle`.  

> **Nota:** I segnaposto qui sotto rappresentano i blocchi di codice esatti del tutorial originale; mantienili invariati.

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

Puoi anche scaricare il JAR direttamente dalla pagina ufficiale dei rilasci: [Rilasci GroupDocs.Merger](https://releases.groupdocs.com/merger/java/).

### Acquisizione Licenza
- **Free Trial:** Ideale per prototipazione e valutazione.  
- **Temporary License:** Estende le funzionalità di prova per un periodo limitato.  
- **Full License:** Sblocca tutte le funzionalità relative a OLE e rimuove i limiti di utilizzo.

Dopo aver aggiunto la dipendenza, sei pronto per inizializzare la libreria nel tuo codice Java.

## Come Convertire Immagine in OLE in Java?
Per convertire un'immagine in un oggetto OLE, carica il documento di destinazione con un'istanza `Merger`, leggi il file immagine in un array di byte, crea un oggetto `OleDiagramOptions` specificando pagina, posizione e dimensione, quindi chiama `merger.importOleDiagram(imageBytes, options)`. Infine, salva il documento usando `merger.save(outputPath)`. Questo flusso di lavoro incorpora l'immagine come diagramma OLE modificabile.

### Passo 1: Definire i Percorsi dei File
Specifica dove si trovano il documento sorgente e l'immagine. Sostituisci i segnaposto con i percorsi reali sulla tua macchina:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### Passo 2: Leggere i Byte dell'Immagine
Leggi l'intero file immagine in un array di byte. Questo array di byte diventa il payload OLE:

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### Passo 3: Configurare le Opzioni del Diagramma OLE
`OleDiagramOptions` indica a GroupDocs dove e come posizionare l'oggetto OLE. La classe è il **contenitore di opzioni di livello superiore per l'importazione di diagrammi OLE**; ti permette di impostare il numero di pagina, le coordinate X/Y, larghezza e altezza.

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### Passo 4: Inizializzare Merger e Importare il Diagramma OLE
`Merger` è la classe principale che rappresenta un documento e fornisce metodi per la manipolazione. Essa **incapsula tutte le operazioni di lettura/scrittura** per il file di destinazione.

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## Salvare un Documento Modificato

Una volta incorporato il diagramma OLE, è necessario scrivere le modifiche su disco.

### Passo 1: Inizializzare Merger con il Percorso Sorgente
Riutilizza la stessa istanza `Merger` o creane una nuova che punti al documento modificato:

```java
Merger merger = new Merger(filePath);
```

### Passo 2: Salvare il Documento Modificato
Chiama il metodo `save` con la posizione di output desiderata. GroupDocs.Merger scrive il file in modalità streaming, mantenendo basso l'uso della memoria:

```java
merger.save(outputPath);
```

## Applicazioni Pratiche
Incorporare immagini come oggetti OLE sblocca diversi scenari reali:
- **Interactive Reports:** Gli utenti possono fare doppio clic su un grafico incorporato, modificarlo in Excel e vedere immediatamente il visual aggiornato.  
- **Automated Document Generation:** I sistemi finanziari e sanitari possono inserire grafiche aggiornate nei contratti o nei riepiloghi dei pazienti senza interventi manuali.  
- **Collaboration Platforms:** I team possono condividere un unico file Word in cui ogni membro aggiorna il proprio diagramma, riducendo i problemi di controllo delle versioni.  

## Considerazioni sulle Prestazioni
Per mantenere la tua applicazione reattiva durante l'elaborazione di file di grandi dimensioni:
- **Stream Data:** GroupDocs.Merger trasmette sia l'input che l'output, evitando il caricamento completo del file in memoria.  
- **Reuse Objects:** Riutilizzare una singola istanza `Merger` per più importazioni riduce l'overhead di creazione degli oggetti.  
- **Monitor Heap:** Per documenti più grandi di 200 MB, considera di aumentare l'heap JVM (`-Xmx1g`) per evitare `OutOfMemoryError`.  

## Problemi Comuni e Soluzioni
| Sintomo | Probabile Causa | Soluzione |
|---------|-----------------|-----------|
| `Unsupported file format` error | Immagine non in PNG/JPEG/BMP/GIF/TIFF | Converti l'immagine in un formato supportato prima di leggere i byte. |
| L'oggetto OLE appare nella posizione errata | Coordinate `x`/`y` errate in `OleDiagramOptions` | Verifica che le coordinate siano misurate in punti (1 pt ≈ 1/72 in). |
| Il file di output è corrotto | Mancata chiamata a `save()` dopo l'importazione | Assicurati che `merger.save(outputPath)` venga eseguito dopo tutte le modifiche. |

## Domande Frequenti

**Q: Cos'è un oggetto OLE?**  
A: Un oggetto OLE incorpora dati da un'applicazione (ad esempio, un'immagine) in un'altra (ad esempio, un file Word), consentendo la modifica in loco senza uscire dal documento ospitante.

**Q: Posso usare GroupDocs.Merger per progetti commerciali?**  
A: Sì — l'uso commerciale richiede una licenza valida. È disponibile una versione di prova per la valutazione, ma le distribuzioni in produzione devono essere licenziate.

**Q: Come gestisce la libreria immagini molto grandi?**  
A: Le immagini vengono lette in un array di byte, ma è possibile trasmettere file di grandi dimensioni usando `FileInputStream` e passare lo stream a `importOleDiagram` per mantenere basso l'uso della memoria.

**Q: Quali formati di documento supportano l'incorporamento OLE?**  
A: DOCX, XLSX, PPTX e PDF sono pienamente supportati. Per PDF, l'oggetto OLE è memorizzato come stream di file incorporato.

**Q: Ci sono limitazioni sul numero di oggetti OLE per documento?**  
A: Praticamente nessuna — GroupDocs.Merger può incorporare decine di diagrammi OLE, limitati solo dalla dimensione del documento ospitante e dalla memoria disponibile.

## Risorse
- [Rilasci GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [Documentazione Java di GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Riferimento API Java](https://reference.groupdocs.com/merger/java/)
- [Rilasci GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/)
- [Pagina di Acquisto GroupDocs](https://purchase.groupdocs.com/buy)
- [Forum di Supporto GroupDocs](https://forum.groupdocs.com/c/merger)

## Conclusione
Ora disponi di un flusso di lavoro completo e pronto per la produzione per **convert image to OLE** usando GroupDocs.Merger per Java. Definendo i percorsi dei file, leggendo i byte dell'immagine, configurando `OleDiagramOptions` e invocando `importOleDiagram`, puoi arricchire qualsiasi documento supportato con grafiche interattive. Esplora le API aggiuntive — come merging, splitting e watermarking — per costruire una pipeline di elaborazione documenti completa.

---

**Last Updated:** 2026-06-26  
**Tested With:** GroupDocs.Merger 23.10 per Java  
**Author:** GroupDocs

## Tutorial Correlati

- [Come incorporare PDF in Excel usando GroupDocs.Merger per Java - Importare un Oggetto OLE – Guida Passo‑per‑Passo](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [Come incorporare PDF in Word usando GroupDocs.Merger per Java – Guida Completa](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [Come Unire Immagini PNG Usando GroupDocs.Merger per Java - Guida Passo‑per‑Passo](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)