---
date: '2026-10-16'
description: Scopri come estrarre e unire pagine in Java usando GroupDocs.Merger.
  Questa guida copre la configurazione, la selezione degli intervalli di pagine, l'unione
  di PDF/DOCX e consigli sulle prestazioni.
keywords:
- extract and merge pages
- merge documents java
- groupdocs merger java
lastmod: '2026-10-16'
og_description: Scopri come estrarre e unire pagine in Java usando GroupDocs.Merger,
  una potente libreria che supporta oltre 50 formati e gestisce documenti di grandi
  dimensioni in modo efficiente.
og_image_alt: Guide showing how to extract and merge pages in Java with GroupDocs.Merger
og_title: Come estrarre e unire pagine in Java con GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  headline: How to extract and merge pages in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  name: How to extract and merge pages in Java with GroupDocs.Merger
  steps:
  - name: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
    text: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
  - name: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
    text: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
  - name: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
    text: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
  type: HowTo
- questions:
  - answer: Yes, simply call `merger.join()` repeatedly for each additional source
      file.
    question: Can I merge more than two documents?
  - answer: It supports PDF, DOCX, DOC, PPTX, PPT, XLSX, XLS, and many other common
      office formats—over 50 in total.
    question: What file types does GroupDocs.Merger support?
  - answer: Use the `extract` method with `PageExtractOptions` to save selected pages
      as a new file. This is covered under the **extract pages java** use case.
    question: How do I extract pages from a document without merging?
  - answer: The library imposes no hard cap; practical limits depend on your system’s
      memory and CPU.
    question: Is there a limit to the number of pages I can join?
  - answer: Absolutely—concatenate timestamps or UUIDs to the filename using `PathConstants.getOutputFilePath()`
      or custom logic.
    question: Can I generate dynamic output file names?
  type: FAQPage
tags:
- merge pages
- GroupDocs.Merger
- Java document processing
- PDF manipulation
- DOCX merging
title: Come estrarre e unire pagine in Java con GroupDocs.Merger
type: docs
url: /it/java/document-joining/join-pages-groupdocs-merger-java-tutorial/
weight: 1
---

# Come estrarre e unire pagine in Java con GroupDocs.Merger

In questo tutorial completo scoprirai come **estrarre e unire pagine** da PDF, file DOCX, fogli di calcolo e molti altri tipi di documento usando GroupDocs.Merger per Java. Che tu abbia bisogno di assemblare brochure personalizzate, estrarre capitoli da più libri o generare un rapporto conciso da file sorgente sparsi, questa guida ti accompagna passo passo attraverso l'intero processo con spiegazioni chiare ed esempi reali.

## Risposte rapide
- **Qual è il caso d'uso principale?** Combina pagine selezionate da PDF, DOCX, XLSX, PPTX e altri formati supportati in un unico file di output.  
- **Quale libreria gestisce questo?** GroupDocs.Merger per Java.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per la valutazione; è necessaria una licenza a pagamento per l'uso in produzione.  
- **Quale versione di Java è richiesta?** Java 8 o superiore.  
- **Posso unire più di due file?** Sì—chiama `join` ripetutamente per ogni documento sorgente aggiuntivo.

## Che cosa significa estrarre e unire pagine?
`extract and merge pages` è il processo di selezione di numeri di pagina o intervalli specifici da uno o più documenti sorgente e di unirli in un nuovo file. Questo elimina il copia‑incolla manuale e garantisce che il documento risultante mantenga la formattazione, i caratteri e le immagini originali.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger per Java è una libreria versatile che consente agli sviluppatori di manipolare i documenti in modo programmatico, offrendo supporto per oltre 50 formati, elaborazione ad alta velocità e basso consumo di memoria, rendendola ideale per flussi di lavoro documentali lato server e operazioni batch su larga scala in ambienti aziendali.

- **Flessibilità di formato:** Supporta più di 50 formati di input e output—including PDF, DOCX, PPTX, XLSX e file immagine—così puoi lavorare con praticamente qualsiasi documento office.  
- **Orientata alle prestazioni:** Elabora solo le pagine richieste, riducendo il consumo di memoria.  
- **Facile integrazione:** Disponibile via Maven o Gradle, con documentazione API chiara e senza dipendenze esterne.  

## Prerequisiti
- Conoscenze di base di programmazione Java.  
- Maven o Gradle per la gestione delle dipendenze.  
- Un IDE come IntelliJ IDEA o Eclipse.  

## Configurazione di GroupDocs.Merger per Java

Aggiungi la libreria al tuo progetto usando uno dei seguenti metodi.

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

In alternativa, scarica l'ultima versione direttamente da [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza
Per sbloccare tutte le funzionalità è necessaria una licenza. Puoi iniziare con una prova gratuita o acquistare una licenza completa sulla [pagina di acquisto](https://purchase.groupdocs.com/buy). È disponibile anche una licenza temporanea per valutazioni a breve termine.

## Come estrarre e unire pagine in Java?
La classe `Merger` è il componente API principale che crea e gestisce le operazioni di unione dei documenti. Carica ogni documento sorgente con il costruttore `Merger`, specifica i numeri di pagina esatti di cui hai bisogno e chiama `join` per combinarli. Infine, salva il risultato unito nel formato desiderato. Questo flusso end‑to‑end richiede solo quattro chiamate di metodo e funziona in modo coerente su tutti i tipi di file supportati.

## Guida passo‑passo per estrarre e unire pagine specifiche

### Passo 1: inizializzare il Merger con un documento principale
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.PageJoinOptions;

String filePath = YOUR_DOCUMENT_DIRECTORY + "/sample.pdf"; // Source PDF document path
Merger merger = new Merger(filePath);
```

### Passo 2: definire le pagine da unire
```java
// Specify the page numbers you wish to join (e.g., pages 1 and 2)
PageJoinOptions joinOptions = new PageJoinOptions(1, 2);
```

### Passo 3: unire le pagine selezionate da un secondo documento
```java
// Path to your DOCX file\ String docxFilePath = YOUR_DOCUMENT_DIRECTORY + "/sample.docx";
merger.join(docxFilePath, joinOptions);
```

### Passo 4: salvare il risultato e rilasciare le risorse
```java
String outputFilePath = YOUR_OUTPUT_DIRECTORY + "/CrossJoinPagesFromVariousDocuments-output.pdf";
merger.save(outputFilePath);

try {
    merger.close();
} catch (Exception e) {
    // Handle exceptions appropriately
}
```

### Passo 5 (opzionale): centralizzare i percorsi dei file con costanti
```java
import java.nio.file.Paths;
import java.io.File;

public class PathConstants {
    public static final String DOCUMENT_BASE_PATH = YOUR_DOCUMENT_DIRECTORY;
    public static final String OUTPUT_BASE_PATH = YOUR_OUTPUT_DIRECTORY;

    public static String getDocumentPath(String fileName) {
        return DOCUMENT_BASE_PATH + "/" + fileName;
    }

    public static String getOutputFilePath() {
        File outputFile = new File(OUTPUT_BASE_PATH, "CrossJoinPagesFromVariousDocuments-output.pdf");
        return outputFile.getPath();
    }
}
```

Usare le costanti rende il codice più pulito e semplifica future modifiche ai percorsi.

## Applicazioni pratiche
Ecco alcuni scenari reali in cui **estrarre e unire pagine** è particolarmente utile:

1. **Consolidamento di documenti:** Estrarre capitoli selezionati da diversi libri di testo in un unico PDF per una rapida revisione.  
2. **Generazione di report:** Unire sezioni chiave da PDF finanziari e PDF derivati da Excel in un unico executive summary.  
3. **Compilazione di ricerche:** Unire estratti da più articoli accademici (PDF, DOCX) in un unico documento di riferimento.

## Considerazioni sulle prestazioni
- **Chiudi il Merger** dopo aver terminato per liberare le risorse native.  
- **Seleziona solo le pagine necessarie** invece di unire file interi; questo riduce drasticamente il tempo di elaborazione.  
- **Gestisci le eccezioni** in modo appropriato per evitare crash quando un file sorgente è mancante o corrotto.  

## Problemi comuni e soluzioni
| Problema | Soluzione |
|----------|-----------|
| **`OutOfMemoryError` su file di grandi dimensioni** | Elabora le pagine in batch più piccoli e chiudi il Merger dopo ogni batch. |
| **Formato file non supportato** | Verifica che il formato sia elencato nei formati supportati da GroupDocs.Merger (PDF, DOCX, XLSX, PPTX, ecc.). |
| **Licenza non applicata** | Assicurati che il file di licenza sia posizionato nella directory radice dell'applicazione o impostato tramite `License license = new License(); license.setLicense("path/to/license.lic");`. |

## Domande frequenti

**Q: Posso unire più di due documenti?**  
A: Sì, basta chiamare `merger.join()` ripetutamente per ogni file sorgente aggiuntivo.

**Q: Quali tipi di file supporta GroupDocs.Merger?**  
A: Supporta PDF, DOCX, DOC, PPTX, PPT, XLSX, XLS e molti altri formati office comuni—oltre 50 in totale.

**Q: Come estrarre pagine da un documento senza unirle?**  
A: Usa il metodo `extract` con `PageExtractOptions` per salvare le pagine selezionate come nuovo file. Questo è coperto nel caso d'uso **extract pages java**.

**Q: Esiste un limite al numero di pagine che posso unire?**  
A: La libreria non impone un limite rigido; i limiti pratici dipendono dalla memoria e dalla CPU del tuo sistema.

**Q: Posso generare nomi di file di output dinamici?**  
A: Assolutamente—concatenare timestamp o UUID al nome del file usando `PathConstants.getOutputFilePath()` o logica personalizzata.

## Risorse
- [Documentazione](https://docs.groupdocs.com/merger/java/)
- [Riferimento API](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/)
- [Acquista una licenza](https://purchase.groupdocs.com/buy)
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Forum di supporto](https://forum.groupdocs.com/c/merger/)

Esplora questi link per approfondire le tue competenze e risolvere eventuali problemi che incontri.

---

**Ultimo aggiornamento:** 2026-10-16  
**Testato con:** GroupDocs.Merger per Java ultima versione  
**Autore:** GroupDocs

## Tutorial correlati

- [Guida all'estrazione di pagine Groupdocs Merger Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java-guide/)
- [Unire PDF Java: Unire PDF in modo efficiente usando GroupDocs.Merger per Java – Guida passo‑passo](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [Spostare pagine Java – Tutorial operazioni di pagina documento per GroupDocs.Merger](/merger/java/page-operations/)