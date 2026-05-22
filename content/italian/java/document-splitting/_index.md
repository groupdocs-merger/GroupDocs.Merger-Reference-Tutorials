---
date: 2026-05-22
description: Scopri come creare file PDF a pagina singola e dividere PDF utilizzando
  GroupDocs.Merger per Java. Include guide passo-passo per split pdf java e altro.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: Crea PDF a pagina singola con GroupDocs.Merger Java
type: docs
url: /it/java/document-splitting/
weight: 12
---

# Crea PDF a pagina singola con GroupDocs.Merger Java

Se hai bisogno di **creare PDF a pagina singola** da documenti più grandi o semplicemente di dividere i PDF in parti più gestibili, sei nel posto giusto. Questa guida ti accompagna attraverso gli scenari di divisione più comuni—file multi‑pagina, intervalli di pagine, pagine dispari/pari, divisione DOCX e persino divisioni basate su testo—utilizzando la potente libreria GroupDocs.Merger per Java. Alla fine di questo tutorial saprai esattamente come integrare queste tecniche nelle tue applicazioni, migliorare le prestazioni di gestione dei documenti e mantenere il tuo codice pulito e manutenibile.

## Risposte rapide
- **Cosa significa “create single page PDF”?** Significa estrarre una pagina da un documento sorgente e salvarla come file PDF indipendente.  
- **Quale libreria gestisce il lavoro?** GroupDocs.Merger per Java fornisce un'API fluida per tutte le operazioni di divisione.  
- **Ho bisogno di una licenza?** Una licenza temporanea funziona per lo sviluppo; è necessaria una licenza completa per la produzione.  
- **Posso dividere le pagine dispari e pari di un PDF?** Sì—GroupDocs.Merger ti consente di filtrare le pagine per numeri dispari/pari.  
- **Il supporto per la divisione di DOCX è disponibile?** Assolutamente; è possibile dividere i file DOCX pagina per pagina o per intervalli personalizzati.  

## Che cos'è “create single page PDF”?
Creare un PDF a pagina singola consiste nel prendere un documento sorgente multi‑pagina (PDF, DOCX, PPTX, ecc.) ed estrarre una sola pagina in un proprio file PDF. Questo è utile per generare fatture, certificati o immagini di anteprima dove è necessaria solo una pagina specifica.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger per Java offre un'API unica e coerente che gestisce molti formati di documento garantendo alte prestazioni e basso utilizzo della memoria. Semplifica lo sviluppo astrarre la gestione complessa dei file, permettendoti di concentrarti sulla logica di business anziché sui dettagli di elaborazione a basso livello.

- **Unified API** – Funziona con PDF, DOCX, PPTX, immagini e molti altri formati.  
- **High performance** – Ottimizzato per file di grandi dimensioni e operazioni batch; può elaborare documenti fino a 2 GB senza caricare l'intero file in memoria.  
- **Fine‑grained control** – Dividi per intervallo di pagine, pagine dispari/pari o delimitatori personalizzati.  
- **Stream‑friendly** – L'output può essere salvato su file o restituito come stream per servizi web.

## Prerequisiti
- Java 8 o versioni successive.  
- GroupDocs.Merger per Java aggiunto al tuo progetto (Maven/Gradle).  
- Un file di licenza GroupDocs valido (temporaneo o completo).

## Come creare PDF a pagina singola?
Creare un PDF a pagina singola con GroupDocs.Merger prevede il caricamento del file sorgente, la specifica della pagina o intervallo esatto, l'invocazione dell'operazione di divisione e infine il salvataggio del risultato. Questo flusso di lavoro garantisce che il documento originale rimanga intatto mentre la pagina estratta viene salvata come file PDF indipendente.

La classe `Merger` è il componente principale che carica i documenti sorgente e fornisce la funzionalità di divisione.

### Passo 1: Inizializzare il Merger
La classe `Merger` è il componente principale di GroupDocs.Merger che carica un documento sorgente e fornisce operazioni di divisione. Crea un'istanza passando il percorso del file o uno stream di input.

### Passo 2: Definire i criteri di divisione
Scegli il numero di pagina o l'intervallo esatto di cui hai bisogno. Per un'estrazione a pagina singola, specificherai un intervallo come `1‑1`. Quando devi **split pdf by range**, puoi passare più intervalli come `1‑5, 6‑10`.

### Passo 3: Eseguire la divisione
Chiama il metodo `split` appropriato. Ad esempio, `merger.split(new int[]{1})` estrae la prima pagina, mentre `merger.splitByRange(new int[][]{{1,5},{6,10}})` gestisce più intervalli in una singola chiamata.

### Passo 4: Salvare il risultato
Scrivi ogni output su un percorso file o restituiscilo come `java.io.InputStream`. Questo facilita l'integrazione con le API web o la memorizzazione del risultato in storage cloud.

> **Pro tip:** Quando lavori con PDF di grandi dimensioni, chiama `merger.setOptimizeResources(true)` prima della divisione per ridurre il consumo di memoria.

## Come dividere i file PDF Java in più pagine
La classe `Merger` fornisce l'API principale per caricare e manipolare file PDF. Per dividere un PDF in file separati di una pagina, basta caricare il documento con l'istanza Merger e chiamare il metodo split senza parametri. La libreria crea automaticamente un nuovo PDF per ogni pagina, preservando il contenuto e i metadati originali, ideale per l'elaborazione batch di fatture o report.

## Come dividere le pagine dispari e pari di un PDF
La classe `Merger` è il componente principale che esegue le operazioni di divisione sui documenti. Quando ti servono solo le pagine dispari o pari di un PDF, fornisci un elenco dei numeri di pagina desiderati alla funzione split. Merger genererà un nuovo documento contenente solo quelle pagine, permettendoti di creare rapidamente file separati per contenuti con numeri dispari o pari.

## Come dividere i file docx (come dividere docx)
La classe `Merger` funziona anche con file DOCX. Usa `splitByPage` per generare un DOCX (o PDF) per pagina, o combinalo con `saveAsPdf` se ti serve l'output PDF. Questo copre il flusso di lavoro di conversione **docx to pdf java** in un unico passaggio.

## Come dividere i documenti in file multi‑pagina
La classe `Merger` gestisce la paginazione e la creazione dei file per le operazioni di divisione. Se preferisci suddividere un documento grande in blocchi di dimensione fissa, specifica il numero di pagine per file di output. Merger itererà sul sorgente, creando nuovi PDF ciascuno contenente il numero di pagine definito, semplificando l'archiviazione, la distribuzione e l'elaborazione parallela di documenti estesi.

## Tutorial disponibili

### [Come dividere i documenti in file multi‑pagina usando GroupDocs.Merger per Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Scopri come dividere efficientemente grandi documenti in file più piccoli e multi‑pagina usando GroupDocs.Merger per Java. Ottimizza la gestione dei documenti con facilità.

### [Come dividere un file di testo per intervalli di righe usando GroupDocs.Merger per Java | Guida alla divisione dei documenti](./split-text-file-line-intervals-groupdocs-merger-java/)
Scopri come dividere file di testo in sezioni gestibili usando intervalli di righe con GroupDocs.Merger per Java. Una guida completa per una gestione efficiente dei documenti.

### [Dividere i documenti per intervallo di pagine con GroupDocs.Merger per Java](./split-documents-page-range-groupdocs-merger-java/)
Scopri come dividere i documenti in intervalli di pagine specifici usando GroupDocs.Merger per Java. Semplifica la gestione dei documenti e applica filtri come pagine dispari/pari.

### [Divisione avanzata dei documenti con GroupDocs.Merger: Guida completa](./master-document-splitting-groupdocs-merger-java/)
Scopri come dividere efficientemente i documenti in pagine singole usando GroupDocs.Merger per Java. Questa guida copre configurazione, implementazione e applicazioni pratiche.

### [Divisione avanzata di documenti Java con GroupDocs.Merger: Dividi le pagine DOCX in file e stream](./master-java-document-splitting-groupdocs-merger/)
Scopri come dividere efficientemente i documenti DOCX in pagine separate o stream usando GroupDocs.Merger per Java. Questa guida copre configurazione, implementazione e applicazioni pratiche.

## Risorse aggiuntive

- [Documentazione di GroupDocs.Merger per Java](https://docs.groupdocs.com/merger/java/)
- [Riferimento API di GroupDocs.Merger per Java](https://reference.groupdocs.com/merger/java/)
- [Scarica GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/)
- [Forum di GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Supporto gratuito](https://forum.groupdocs.com/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

## Problemi comuni e soluzioni
| Problema | Soluzione |
|----------|-----------|
| **Sovraccarico di memoria su PDF di grandi dimensioni** | Abilita l'ottimizzazione delle risorse: `merger.setOptimizeResources(true);` |
| **Numeri di pagina errati dopo la divisione** | Ricorda che l'indicizzazione delle pagine inizia da 1, non da 0. |
| **Licenza non trovata** | Verifica il percorso del tuo file `GroupDocs.Merger.lic` e assicurati che sia incluso nel classpath. |
| **La divisione di DOCX produce pagine vuote** | Assicurati che il DOCX sorgente abbia interruzioni di pagina corrette; altrimenti, usa `splitByParagraph` come alternativa. |

## Domande frequenti

**Q: Posso dividere un PDF protetto da password?**  
A: Sì. Carica il documento con il parametro password, quindi esegui qualsiasi operazione di divisione come al solito.

**Q: Come divido solo le pagine dispari di un PDF?**  
A: Fornisci un elenco di pagine contenente solo numeri dispari (ad esempio 1,3,5…) al metodo `split`.

**Q: È possibile dividere un DOCX direttamente in PDF?**  
A: Assolutamente. Dopo aver caricato il DOCX, chiama `saveAsPdf` su ogni segmento diviso.

**Q: Quali formati supporta GroupDocs.Merger per la divisione?**  
A: PDF, DOCX, PPTX, TXT, HTML e molti formati immagine (PNG, JPEG, ecc.).

**Q: Ho bisogno di una licenza separata per ogni tipo di file?**  
A: No. Una singola licenza GroupDocs.Merger copre tutti i formati supportati.

---

**Ultimo aggiornamento:** 2026-05-22  
**Testato con:** GroupDocs.Merger 23.11 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [split pdf java: Divisione di documenti con GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Divisione avanzata di documenti per intervallo di pagine con GroupDocs.Merger per Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Unire PDF in modo efficiente usando GroupDocs.Merger per Java: Guida passo‑passo](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)