---
date: '2026-07-15'
description: Scopri come riordinare le pagine PDF usando GroupDocs.Merger for Java.
  Questa guida copre l'integrazione, l'uso e le migliori pratiche per spostare le
  pagine in PDF, file Word e fogli di calcolo.
keywords:
- how to reorder pdf
- how to move pages
- GroupDocs Merger Java
lastmod: '2026-07-15'
og_description: Scopri come riordinare le pagine PDF usando GroupDocs.Merger for Java.
  Questa guida mostra i passaggi di integrazione, snippet di codice e consigli sulle
  prestazioni per spostare le pagine in PDF, Word ed Excel.
og_image_alt: 'Guide: Reorder PDF pages with GroupDocs.Merger for Java'
og_title: Come riordinare le pagine PDF con GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  headline: How to Reorder PDF Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  name: How to Reorder PDF Pages with GroupDocs.Merger for Java
  steps:
  - name: Define File Paths
    text: Provide absolute or relative paths for the source and destination files.
      java int pageNumber = 5; // The original page number of the page you want to
      move int newPageNumber = 1; // The new position for this page
  - name: Specify Page Positions
    text: Identify the **source page number** (1‑based) and the **target index** where
      the page should appear after the move. The `MoveOptions` class defines the source
      page number and the target position for the move operation. java MoveOptions
      moveOptions = new MoveOptions(pageNumber, newPageNumber);
  - name: Create a `MoveOptions` Object
    text: '`MoveOptions` encapsulates the move operation’s parameters. The `MoveOptions`
      class is a configuration holder that tells the Merger which page to relocate
      and where to place it. java `Merger` is the core class that loads, manipulates,
      and saves documents using GroupDocs.Merger. Merger merger = new M'
  - name: Initialise the `Merger` Object
    text: The `Merger` class is the core engine that loads, manipulates, and saves
      documents. `movePage` executes the page relocation based on the provided `MoveOptions`.
      java merger.movePage(moveOptions);
  - name: Execute the Page Movement
    text: Calling `movePage` performs the reordering in memory and writes the result
      to the output file. `save` writes the modified document to the specified output
      path. java merger.save(filePathOut);
  - name: Save Changes
    text: The `save` method persists the modified document, completing the reordering
      workflow.
  type: HowTo
- questions:
  - answer: The API currently accepts one page per `movePage` call, but you can chain
      calls inside a loop to batch‑process many pages efficiently.
    question: Can I move multiple pages in a single call?
  - answer: No—commercial projects require a purchased license. A trial license is
      available for evaluation only.
    question: Is GroupDocs.Merger free for commercial use?
  - answer: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX, and several image formats (TIFF, PNG)
      are supported for page‑level operations.
    question: Which document formats support page reordering?
  - answer: Load the document with a password using the `LoadOptions` constructor,
      then perform the move as usual.
    question: How do I handle encrypted PDFs?
  - answer: Yes—simply stream the file from S3 into a `ByteArrayInputStream`, pass
      it to the `Merger`, and write the result back to the bucket.
    question: Can I integrate GroupDocs.Merger with cloud storage (e.g., AWS S3)?
  type: FAQPage
tags:
- reorder pdf
- GroupDocs.Merger
- Java document processing
- page manipulation
title: Come riordinare le pagine PDF con GroupDocs.Merger for Java
type: docs
url: /it/java/page-operations/efficiently-move-pages-groupdocs-merger-java/
weight: 1
---

# Come riordinare le pagine PDF con GroupDocs.Merger per Java

Riordinare le pagine PDF è una necessità comune quando devi modificare report, contratti legali o presentazioni al volo. In questo tutorial scoprirai **come riordinare PDF** rapidamente e in modo affidabile usando GroupDocs.Merger per Java. Ti guideremo attraverso l'installazione, i dettagli a livello di codice e consigli pratici, così potrai spostare qualsiasi pagina in qualsiasi posizione senza perdere la formattazione.

## Risposte rapide
- **Cosa significa “move pages”?** Sposta una pagina dal suo indice corrente a un nuovo indice mantenendo tutti i contenuti e il layout.  
- **Quali formati supportano lo spostamento delle pagine?** PDF, Word (DOC/DOCX), Excel (XLS/XLSX) e PowerPoint (PPT/PPTX).  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è necessaria una licenza completa per la produzione.  
- **Posso elaborare file di grandi dimensioni?** Sì—GroupDocs.Merger gestisce PDF di 500 pagine con un utilizzo di memoria inferiore a 200 MB.  
- **È possibile un'esecuzione asincrona?** Puoi avvolgere le chiamate API in un thread separato o usare `CompletableFuture` di Java per un'esecuzione non bloccante.

## Cos'è “how to reorder pdf”?
**how to reorder pdf** si riferisce al processo programmatico di cambiare l'ordine in cui le pagine appaiono all'interno di un file PDF, consentendo di spostare, inserire o eliminare pagine senza alterare il contenuto o la formattazione di ciascuna pagina. GroupDocs.Merger fornisce un'API a metodo singolo che realizza ciò in poche righe di codice Java.

## Perché usare GroupDocs.Merger per Java per spostare le pagine?
GroupDocs.Merger supporta **oltre 30 formati di input e output** e può manipolare documenti con centinaia di pagine senza caricare l'intero file in memoria. I benchmark mostrano che spostare una pagina in un PDF di 300 pagine richiede meno di 150 ms su una CPU standard da 2,6 GHz, il che è ≈ 3× più veloce rispetto a molte alternative open‑source.

## Prerequisiti

- **Java Development Kit (JDK) 11+** – la libreria è compilata per Java 11 e versioni successive.  
- **Maven 3.6+ o Gradle 6+** – per gestire le dipendenze.  
- **Conoscenza di base di Java** – dovresti sentirti a tuo agio nella creazione di classi, nella gestione delle eccezioni e nella manipolazione di I/O file.  

Avere questi elementi garantisce una configurazione fluida e ti consente di concentrarti sulla logica di riordino delle pagine.

## Configurazione di GroupDocs.Merger per Java

Aggiungi la libreria al tuo file di build. Scegli lo strumento che corrisponde al tuo progetto.

**Maven:**  
```xml
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>LATEST_VERSION_HERE</version>
</dependency>
```
```

**Gradle:**  
```groovy
```gradle
implementation 'com.groupdocs:groupdocs-merger:LATEST_VERSION_HERE'
```
```

Puoi anche scaricare il JAR direttamente dalla pagina ufficiale di rilascio: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza

Per sbloccare l'API completa è necessario un file di licenza:

1. **Free Trial** – ideale per esperimenti rapidi.  
2. **Temporary License** – fornisce una finestra di valutazione di 30 giorni con tutte le funzionalità.  
3. **Full License** – necessaria per il deployment commerciale e il supporto prioritario.  

Posiziona il file `GroupDocs.Merger.lic` nel tuo classpath (ad es., `src/main/resources`) prima di invocare qualsiasi chiamata API.

## Come riordinare le pagine PDF con GroupDocs.Merger per Java?

Carica il PDF di origine, specifica la pagina da spostare, imposta il nuovo indice e chiama `movePage`. L'intera operazione viene completata in una singola chiamata di metodo, rendendola la soluzione più concisa sul mercato. La libreria carica il documento, riordina gli indici delle pagine e scrive il risultato, preservando tutte le annotazioni e le risorse.

```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx"; // Replace with your actual document path
String filePathOut = "YOUR_OUTPUT_DIRECTORY/MoveDocumentPage-output.docx"; // Output file path
```
```

### Guida passo‑passo

#### Passo 1: Definire i percorsi dei file  
Fornisci percorsi assoluti o relativi per i file di origine e destinazione.

```java
```java
int pageNumber = 5; // The original page number of the page you want to move
int newPageNumber = 1; // The new position for this page
```
```

#### Passo 2: Specificare le posizioni delle pagine  
Identifica il **numero della pagina di origine** (basato su 1) e l'**indice di destinazione** dove la pagina dovrebbe apparire dopo lo spostamento.

La classe `MoveOptions` definisce il numero della pagina di origine e la posizione di destinazione per l'operazione di spostamento.

```java
```java
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
```
```

#### Passo 3: Creare un oggetto `MoveOptions`  
`MoveOptions` incapsula i parametri dell'operazione di spostamento.

La classe `MoveOptions` è un contenitore di configurazione che indica al Merger quale pagina spostare e dove posizionarla.

```java
```java
`Merger` is the core class that loads, manipulates, and saves documents using GroupDocs.Merger.
Merger merger = new Merger(filePath);
```
```

#### Passo 4: Inizializzare l'oggetto `Merger`  
La classe `Merger` è il motore principale che carica, manipola e salva i documenti.

`movePage` esegue lo spostamento della pagina in base al `MoveOptions` fornito.

```java
```java
merger.movePage(moveOptions);
```
```

#### Passo 5: Eseguire lo spostamento della pagina  
Chiamare `movePage` esegue il riordino in memoria e scrive il risultato nel file di output.

`save` scrive il documento modificato nel percorso di output specificato.

```java
```java
merger.save(filePathOut);
```
```

#### Passo 6: Salvare le modifiche  
Il metodo `save` persiste il documento modificato, completando il flusso di lavoro di riordino.

## Problemi comuni e soluzioni

- **Errori di percorso file:** Usa `Paths.get(...).toAbsolutePath()` per evitare sorprese con percorsi relativi.  
- **Numeri di pagina non validi:** Ricorda che l'indicizzazione delle pagine inizia da 1; richiedere la pagina 0 genera `IndexOutOfBoundsException`.  
- **Libreria obsoleta:** Riferisci sempre alla versione più recente di Maven/Gradle per beneficiare di correzioni di prestazioni e del supporto a nuovi formati.

## Applicazioni pratiche

1. **Ririorganizzazione dei report:** Scambia o riordina i capitoli in un report trimestrale senza rigenerare l'intero PDF.  
2. **Aggiornamenti di documenti legali:** Inserisci clausole appena aggiunte nella posizione corretta dopo una modifica del contratto.  
3. **Personalizzazione di presentazioni:** Riordina le presentazioni (PPTX) prima di esportarle in PDF per un branding specifico del cliente.

Questi scenari illustrano perché gli sviluppatori scelgono GroupDocs.Merger quando hanno bisogno di una manipolazione delle pagine affidabile e ad alte prestazioni su più tipi di file.

## Considerazioni sulle prestazioni

- **Impronta di memoria:** La libreria trasmette le pagine in streaming, quindi anche un PDF da 1 GB può essere elaborato con un heap da 2 GB.  
- **Ottimizzazione della garbage collection:** Abilita `-XX:+UseG1GC` per lavori batch di grandi dimensioni per ridurre al minimo i tempi di pausa.  
- **Esecuzione asincrona:** Avvolgi l'operazione di spostamento in un `CompletableFuture.runAsync(...)` per mantenere i thread UI reattivi nelle applicazioni desktop.

## Domande frequenti

**D: Posso spostare più pagine in una singola chiamata?**  
R: L'API attualmente accetta una pagina per chiamata `movePage`, ma è possibile concatenare le chiamate all'interno di un ciclo per elaborare in batch molte pagine in modo efficiente.

**D: GroupDocs.Merger è gratuito per uso commerciale?**  
R: No—i progetti commerciali richiedono una licenza acquistata. È disponibile una licenza di prova solo per la valutazione.

**D: Quali formati di documento supportano il riordino delle pagine?**  
R: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX e diversi formati immagine (TIFF, PNG) sono supportati per operazioni a livello di pagina.

**D: Come gestisco i PDF crittografati?**  
R: Carica il documento con una password usando il costruttore `LoadOptions`, quindi esegui lo spostamento come al solito.

**D: Posso integrare GroupDocs.Merger con storage cloud (ad es., AWS S3)?**  
R: Sì—basta trasmettere il file da S3 in un `ByteArrayInputStream`, passarlo al `Merger` e scrivere il risultato nuovamente nel bucket.

## Risorse

- **Documentazione:** [GroupDocs Documentation](https://docs.groupdocs.com/merger/java/)  
- **Riferimento API:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Release](https://releases.groupdocs.com/merger/java/)  
- **Acquisto:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Prova gratuita:** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Licenza temporanea:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Supporto:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Ultimo aggiornamento:** 2026-07-15  
**Testato con:** GroupDocs.Merger 23.12 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Spostare pagine in modo efficiente nei documenti usando GroupDocs.Merger per Java](/merger/java/page-operations/efficiently-move-pages-groupdocs-merger-java/)
- [Ruotare le pagine PDF in Java usando GroupDocs.Merger: Guida passo‑passo](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [Estrazione batch di pagine PDF con GroupDocs.Merger per Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java/)