---
date: '2026-07-25'
description: Scopri come dividere un file per righe usando GroupDocs.Merger for Java
  – una guida passo‑a‑passo per una divisione efficiente dei documenti nei progetti
  Java.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Dividi file per righe usando GroupDocs.Merger for Java. Questa guida
  mostra come suddividere grandi file di testo in parti rapidamente, con esempi di
  codice e consigli di best‑practice.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Dividi file per righe con GroupDocs.Merger for Java – Veloce e Facile
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: Come dividere un file per righe con GroupDocs.Merger for Java
type: docs
url: /it/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Come dividere un file per righe con GroupDocs.Merger per Java

Se hai bisogno di **split file by lines**—ad esempio, per suddividere un enorme file di log in parti più piccole, alimentare batch di dati in una pipeline o trasformare un lungo report in file di capitolo separati—questo tutorial ti mostra esattamente come farlo con GroupDocs.Merger per Java. Scoprirai perché la libreria fa risparmiare tempo, otterrai un'implementazione pronta all'uso e imparerai consigli pratici per mantenere la tua applicazione veloce e affidabile.

## Risposte rapide
- **Cosa significa “split file by lines”?** Crea file di testo separati che contengono ciascuno un intervallo definito di numeri di riga dal documento originale.  
- **Quale libreria gestisce la divisione?** GroupDocs.Merger per Java fornisce una semplice API per la divisione per intervalli di righe.  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per i test; è necessaria una licenza permanente per l'uso in produzione.  
- **Posso dividere per conteggio dei caratteri invece?** Non direttamente—usa un passaggio di pre‑elaborazione per riformattare il file prima della divisione.  
- **Quale versione di Java è supportata?** Qualsiasi runtime Java 8+ è compatibile.

## Cos'è “split file by lines”?
**Split file by lines** significa prendere un singolo documento di testo e suddividerlo in più file, ognuno contenente uno specifico intervallo di righe consecutive (ad esempio, righe 1‑3, 4‑6, ecc.). Questo approccio è ideale quando vuoi elaborare i dati in parallelo, ridurre la pressione sulla memoria o semplicemente rendere più facile la navigazione di file lunghi.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger astrae le operazioni di I/O a basso livello, permettendoti di concentrarti sulla logica di business. Gestisce efficientemente file fino a 2 GB senza caricare l'intero documento in memoria, supporta **70+** formati di input e output, e fornisce un'API fluida che si integra perfettamente con build Maven o Gradle. L'uso di questa libreria riduce i tempi di sviluppo fino all'**80 %** rispetto a loop I/O fatti a mano.

## Prerequisiti
- **Java Development Kit (JDK) 8 o superiore** – assicurati che `java` e `javac` siano nel tuo PATH.  
- **GroupDocs.Merger per Java** – aggiungi la libreria via Maven, Gradle o download diretto.  
- **Conoscenza di base di Java** – dovresti sentirti a tuo agio con classi, metodi e gestione delle eccezioni.

## Configurazione di GroupDocs.Merger per Java
Aggiungi la libreria al tuo progetto usando uno dei metodi seguenti.

**Maven** – incolla questa dipendenza nel tuo `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – includi la seguente riga in `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Download diretto** – puoi anche scaricare il JAR dalla pagina di rilascio ufficiale: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza
Inizia con una prova gratuita per esplorare l'API. Per carichi di lavoro di produzione, ottieni una licenza temporanea o completa dal portale GroupDocs.

## Come dividere un file di testo per righe (implementazione Java)

Di seguito trovi una guida concisa, passo‑per‑passo. Ogni passo è spiegato in linguaggio semplice prima del segnaposto che indica dove si trova il codice reale, così sai esattamente cosa sta succedendo.

### Passo 1: Definire i percorsi di origine e destinazione
Prima, indica alla libreria dove si trova il tuo file originale e dove devono essere scritti i frammenti divisi.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Passo 2: Configurare le opzioni di divisione
Crea un'istanza di `TextSplitOptions` che descriva gli intervalli di righe desiderati. L'array `new int[] { 3, 6 }` indica all'API di tagliare dopo la riga 3 e la riga 6, producendo due parti: righe 1‑3 e righe 4‑6.  
**Definition:** `TextSplitOptions` è un oggetto di configurazione che contiene l'array di intervalli di righe e regole opzionali per la denominazione dell'output.  
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Passo 3: Inizializzare il Merger ed eseguire la divisione
Infine, istanzia `Merger` con il file di origine e chiama `split()` con le opzioni appena create.  
**Definition:** `Merger` è la classe principale in GroupDocs.Merger che orchestra le operazioni di manipolazione dei documenti come divisione, unione ed estrazione di pagine.  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Quando la chiamata `split()` termina, troverai due nuovi file in `YOUR_OUTPUT_DIRECTORY`, ciascuno contenente gli intervalli di righe specificati.

## Applicazioni pratiche (Perché è importante)
1. **Pipeline di elaborazione dati** – Suddividi file di log massivi in blocchi più piccoli per l'analisi parallela, riducendo drasticamente il tempo totale di elaborazione.  
2. **Gestione documentale** – Trasforma un unico report in file a livello di capitolo, facilitando la distribuzione a diversi team.  
3. **Segmentazione dei contenuti** – Prepara sezioni di un grande articolo per piattaforme di pubblicazione mirate, migliorando SEO e leggibilità.

## Suggerimenti sulle prestazioni
- **Stream‑line I/O** – Preferisci `Files.newBufferedReader` quando lavori con file molto grandi per mantenere basso l'uso di memoria.  
- **Chiudi le risorse** – Sebbene GroupDocs.Merger gestisca la maggior parte della pulizia, chiudere esplicitamente eventuali stream personalizzati evita perdite.  
- **Monitora la memoria** – Dividere file di dimensioni gigabyte può essere intensivo in termini di memoria; assegna un heap sufficiente (`-Xmx2g` o superiore) se necessario.  
- **Elaborazione batch** – Quando dividi molti file, riutilizza una singola istanza di `Merger` per ridurre l'overhead di creazione degli oggetti.

## Problemi comuni e soluzioni
| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| `OutOfMemoryError` | Il file di origine è troppo grande per l'heap. | Aumenta l'heap JVM o dividi usando intervalli più piccoli. |
| `FileNotFoundException` | Percorso errato o permessi insufficienti. | Verifica che `filePath` e `filePathOut` siano assoluti e scrivibili. |
| Empty output files | L'array di intervalli non copre l'intero documento. | Assicurati che l'ultimo intervallo termini a o oltre il conteggio totale delle righe. |

## Domande frequenti

**Q: Posso dividere i file in base al conteggio dei caratteri invece che al numero di righe?**  
A: Attualmente, GroupDocs.Merger per Java si concentra sugli intervalli di righe. Tuttavia, puoi pre‑elaborare il testo per ottenere il conteggio di caratteri desiderato per riga prima di usare questa funzionalità.

**Q: Esiste un limite al numero di intervalli che posso specificare per la divisione?**  
A: Non c'è un limite rigido nella libreria; le prestazioni potrebbero degradare se richiedi migliaia di divisioni molto piccole perché ogni divisione comporta overhead di I/O.

**Q: Come gestisco gli errori durante la divisione dei file?**  
A: Avvolgi la logica di divisione in un blocco try‑catch e registra i dettagli di `MergerException`. L'API fornisce messaggi chiari che indicano il punto di errore.

**Q: La libreria supporta altri formati basati su testo come CSV o TSV?**  
A: Sì, poiché CSV e TSV sono file di testo semplice, la stessa logica di intervalli di righe si applica. Trattali come file `.txt` quando chiami l'API.

**Q: Posso automatizzare la divisione per più file in una cartella?**  
A: Assolutamente. Itera su `Files.list(Paths.get("folder"))`, applica le stesse `TextSplitOptions` a ciascun file e raccogli le parti generate.

## Risorse aggiuntive
- [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)
- [Latest Releases](https://releases.groupdocs.com/merger/java/)
- [Buy GroupDocs](https://purchase.groupdocs.com/buy)
- [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)
- [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Ultimo aggiornamento:** 2026-07-25  
**Testato con:** GroupDocs.Merger 23.12 per Java  
**Autore:** GroupDocs

## Tutorial correlati

- [How to Split a Text File into Separate Line Documents Using GroupDocs.Merger for Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [split pdf java: Document Splitting with GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Load Local Document Java Using GroupDocs.Merger – Guide](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)