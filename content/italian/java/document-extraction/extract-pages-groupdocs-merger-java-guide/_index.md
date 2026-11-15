---
date: '2026-11-15'
description: Scopri come estrarre pagine specifiche java usando GroupDocs.Merger per
  Java, includendo pagine pari, pagine dispari e intervalli personalizzati. Vedi anche
  come dividere le pagine PDF in Java.
images:
- /java/document-extraction/extract-pages-groupdocs-merger-java-guide/og-image.png
keywords:
- extract specific pages java
- split pdf pages java
- groupdocs merger java
- java document processing
- page extraction
lastmod: '2026-11-15'
og_description: Estrai pagine specifiche java usando GroupDocs.Merger per Java. Questa
  guida ti mostra come estrarre pagine pari, pagine dispari, intervalli personalizzati
  e dividere le pagine PDF in modo efficiente con poche righe di codice.
og_image_alt: Guide showing extract specific pages java using GroupDocs.Merger
og_title: Estrai pagine specifiche java con GroupDocs.Merger per Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-15'
  description: Learn how to extract specific pages java using GroupDocs.Merger for
    Java, including even pages, odd pages, and custom ranges. Also see how to split
    PDF pages in Java.
  headline: Extract specific pages java with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to extract specific pages java using GroupDocs.Merger for
    Java, including even pages, odd pages, and custom ranges. Also see how to split
    PDF pages in Java.
  name: Extract specific pages java with GroupDocs.Merger for Java
  steps:
  - name: define input and output paths
    text: Specify the full file system paths for the source document and the destination
      file.
  - name: configure extraction options
    text: '`ExtractOptions` lets you set the start page, end page, and the `RangeMode`
      (even, odd, or custom). The example below extracts only even pages between 1
      and 3, which means page 2 will be saved.'
  - name: perform extraction and save the result
    text: Invoke the `extract` method on the `Merger` instance and write the new document
      to disk. **Pro tip:** Wrap the extraction logic in a `try‑catch` block to handle
      `IOException` and format‑specific exceptions gracefully.
  type: HowTo
- questions:
  - answer: Use `RangeMode.OddPages` when creating `ExtractOptions`.
    question: How do I extract odd‑numbered pages?
  - answer: Yes—GroupDocs.Merger supports PDF, DOCX, PPTX, XLSX, and many other formats.
    question: Can I use this with PDFs?
  - answer: The API throws an `IOException`. Verify the path and check file permissions.
    question: What if my document path is incorrect?
  - answer: Enclose the extraction code in a `try‑catch` block and log the exception
      details for troubleshooting.
    question: How should I handle exceptions during extraction?
  - answer: There’s no hard limit, but extracting very large ranges may require additional
      heap memory.
    question: Is there a limit on the number of pages I can extract?
  type: FAQPage
tags:
- extract pages java
- GroupDocs.Merger
- Java document processing
- page extraction
- PDF split java
title: Estrai pagine specifiche java con GroupDocs.Merger per Java
type: docs
url: /it/java/document-extraction/extract-pages-groupdocs-merger-java-guide/
weight: 1
---

# Estrai pagine specifiche java con GroupDocs.Merger per Java

In questo tutorial imparerai come **estrarre pagine specifiche java** da qualsiasi tipo di documento supportato—Word, PDF, PowerPoint, Excel e altro—utilizzando GroupDocs.Merger per Java. Vedrai perché l'estrazione basata su intervallo è importante, come mirare alle pagine pari, alle pagine dispari o a qualsiasi elenco di pagine personalizzato, e come integrare la soluzione in un progetto Java standard.

## Risposte rapide
- **Cosa significa “estrarre pagine specifiche”?** Significa selezionare solo le pagine di cui hai bisogno da un documento più grande e salvarle come un nuovo file.  
- **Quali formati sono supportati?** Word, PDF, PowerPoint, Excel, HTML, immagini e oltre 30 altri formati.  
- **Posso estrarre solo le pagine pari?** Sì—imposta `RangeMode.EvenPages` nelle opzioni di estrazione.  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per i test; è necessaria una licenza completa per l'uso in produzione.  
- **Quante righe di codice?** Sono necessarie meno di 20 righe per estrarre un intervallo personalizzato.

## Cos'è l'estrazione di pagine specifiche java?
L'estrazione di pagine specifiche java è l'operazione programmatica di prelevare un sottoinsieme di pagine da un documento sorgente e creare un nuovo file indipendente. Questa tecnica è essenziale quando ti serve solo una clausola di un contratto, un singolo capitolo o un gruppo di fatture, evitando l'onere di inviare l'intero documento.

## Perché estrarre pagine specifiche per intervallo?
Estrarre pagine specifiche per intervallo riduce la dimensione del file, protegge le sezioni sensibili e accelera i processi successivi come la firma elettronica, la generazione automatica di report o l'indicizzazione batch. GroupDocs.Merger può richiedere le pagine 1‑5, tutte le pagine pari o qualsiasi elenco arbitrario in una singola chiamata API, eliminando la modifica manuale e risparmiando tempo di sviluppo prezioso.

## Prerequisiti
- **GroupDocs.Merger for Java** aggiunto come dipendenza Maven o Gradle.  
- **JDK 8** o versioni successive installate e configurate sulla tua macchina di sviluppo.  
- Familiarità di base con I/O di file Java e gestione delle eccezioni.

## Configurazione di GroupDocs.Merger per Java

### Configurazione Maven
Aggiungi la dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Configurazione Gradle
Aggiungi la riga al tuo file `build.gradle`:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Download diretto
Puoi anche scaricare gli ultimi binari da [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Passaggi per l'acquisizione della licenza
1. **Prova gratuita** – scarica una versione di prova per esplorare l'API.  
2. **Licenza temporanea** – richiedi una chiave temporanea per test più estesi.  
3. **Acquisto** – acquista una licenza completa per l'uso in produzione.

### Inizializzazione e configurazione di base
La classe `Merger` è l'oggetto API principale che carica un documento e fornisce operazioni di estrazione. Di seguito il codice minimo necessario per creare un'istanza `Merger`:

```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/YourDocument.docx";
Merger merger = new Merger(filePath);
```

## Come estrarre pagine specifiche per intervallo
Carica il documento sorgente, configura le opzioni di estrazione e salva il risultato—tutto in tre semplici passaggi.

### Passo 1: definire i percorsi di input e output
Specifica i percorsi completi del file di sistema per il documento sorgente e il file di destinazione.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/YourDocument.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ExtractedPages.docx";
```

### Passo 2: configurare le opzioni di estrazione
`ExtractOptions` ti consente di impostare la pagina iniziale, la pagina finale e il `RangeMode` (pari, dispari o personalizzato). L'esempio seguente estrae solo le pagine pari tra 1 e 3, il che significa che la pagina 2 verrà salvata.

```java
import com.groupdocs.merger.domain.options.ExtractOptions;
import com.groupdocs.merger.domain.options.RangeMode;

// Extract options configured for even pages from page 1 to 3
ExtractOptions extractOptions = new ExtractOptions(1, 3, RangeMode.EvenPages);
```

### Passo 3: eseguire l'estrazione e salvare il risultato
Invoca il metodo `extract` sull'istanza `Merger` e scrivi il nuovo documento su disco.

```java
// Initialize Merger with input document path
Merger merger = new Merger(filePath);

// Perform extraction based on defined options
merger.extractPages(extractOptions);

// Save the extracted pages to a new file
merger.save(filePathOut);
```

**Consiglio professionale:** Avvolgi la logica di estrazione in un blocco `try‑catch` per gestire `IOException` o eccezioni specifiche del formato in modo corretto.

## Applicazioni pratiche

| Scenario | Come l'estrazione aiuta |
|----------|--------------------------|
| **Revisione legale** | Estrai solo le clausole necessarie per un'analisi rapida, mantenendo nascoste le sezioni riservate. |
| **Ricerca accademica** | Isola capitoli o sezioni dai libri di testo per citazioni o lettura offline. |
| **Report finanziario** | Estrai tabelle o dichiarazioni da report multi‑pagina, riducendo la dimensione del file per la distribuzione via email. |

## Considerazioni sulle prestazioni
- **Gestione della memoria** – I PDF di grandi dimensioni possono consumare una notevole quantità di heap. Aumenta l'heap della JVM (`-Xmx2g`) se incontri `OutOfMemoryError`.  
- **I/O dei file** – Usa stream bufferizzati quando leggi/scrivi file di grandi dimensioni per ridurre la latenza del disco.  
- **Elaborazione batch** – Quando estrai intervalli da molti documenti, elabora in sequenza o utilizza un pool di thread con concorrenza controllata per evitare l'esaurimento delle risorse di sistema.  

GroupDocs.Merger supporta l'estrazione da **oltre 30 formati di documento** e può gestire file fino a **2 GB** senza caricare l'intero file in memoria, offrendo velocità di estrazione di **15 MB/s** su un server tipico.

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **Percorso file non valido** | Verifica il percorso completo e assicurati che l'applicazione abbia i permessi di lettura/scrittura. |
| **Formato non supportato** | Conferma che il tipo di documento (ad es., DOCX, PDF) sia elencato nei formati supportati. |
| **Errori di out‑of‑memory** | Elabora i file di grandi dimensioni in blocchi più piccoli o aumenta la dimensione dell'heap JVM (`-Xmx`). |
| **RangeMode non si comporta come previsto** | Controlla nuovamente i valori di inizio/fine e assicurati che rientrino nel conteggio delle pagine del documento. |

## Domande frequenti

**Q: Come estraggo le pagine dispari?**  
A: Usa `RangeMode.OddPages` quando crei `ExtractOptions`.

**Q: Posso usarlo con i PDF?**  
A: Sì—GroupDocs.Merger supporta PDF, DOCX, PPTX, XLSX e molti altri formati.

**Q: Cosa succede se il percorso del mio documento è errato?**  
A: L'API genera un `IOException`. Verifica il percorso e controlla i permessi del file.

**Q: Come dovrei gestire le eccezioni durante l'estrazione?**  
A: Avvolgi il codice di estrazione in un blocco `try‑catch` e registra i dettagli dell'eccezione per la risoluzione dei problemi.

**Q: Esiste un limite al numero di pagine che posso estrarre?**  
A: Non c'è un limite rigido, ma estrarre intervalli molto grandi può richiedere più memoria heap.

## Risorse
- [Documentazione](https://docs.groupdocs.com/merger/java/)
- [Riferimento API](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/)
- [Acquista prodotti GroupDocs](https://purchase.groupdocs.com/buy)
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Forum di supporto](https://forum.groupdocs.com/c/merger/)

Seguendo questa guida, ora disponi di un metodo affidabile per **estrarre pagine specifiche java** da qualsiasi documento supportato utilizzando GroupDocs.Merger per Java. Buon coding!

**Ultimo aggiornamento:** 2026-11-15  
**Testato con:** GroupDocs.Merger ultima versione (Java)  
**Autore:** GroupDocs

## Tutorial correlati
- [Dividi PDF in pagine con GroupDocs.Merger per Java](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Unisci pagine specifiche java – Unisci documenti con GroupDocs.Merger](/merger/java/document-joining/join-pages-groupdocs-merger-java-tutorial/)
- [Come caricare PDF da URL Java – Tutorial di caricamento documenti per GroupDocs.Merger](/merger/java/document-loading/)