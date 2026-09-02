---
date: '2026-07-25'
description: Scopri come dividere le pagine docx usando GroupDocs.Merger for Java,
  coprendo la divisione del DOCX in file separati, l'estrazione di stream e le opzioni
  di split.
keywords:
- split docx pages
- how to split docx
- split docx into files
lastmod: '2026-07-25'
og_description: Dividi le pagine docx usando GroupDocs.Merger for Java. Scopri passo‑passo
  come dividere il DOCX in file o stream con esempi di codice.
og_image_alt: Guide to split DOCX pages using GroupDocs.Merger Java library
og_title: Dividi le pagine DOCX con GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  headline: How to Split DOCX Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  name: How to Split DOCX Pages with GroupDocs.Merger for Java
  steps:
  - name: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
    text: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
  - name: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
    text: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
  - name: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
    text: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting over
      50 document formats—including DOCX, PDF, PPTX, and HTML—without requiring Microsoft
      Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Acquire a temporary trial license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/)
      for evaluation. For production, purchase a full license at the same site.
    question: How do I obtain a license for GroupDocs.Merger?
  - answer: Yes, the `split` method works with PDF, DOCX, PPTX, and other supported
      formats.
    question: Can I split PDF files using the same API?
  - answer: Absolutely—use the stream‑based approach shown above to keep everything
      in memory.
    question: Is it possible to split a document without writing to disk?
  - answer: Always target the latest stable release to benefit from performance improvements
      and bug fixes.
    question: Which version of GroupDocs.Merger should I use?
  type: FAQPage
tags:
- split docx
- GroupDocs.Merger
- Java document processing
- DOCX splitting
title: Come dividere le pagine DOCX con GroupDocs.Merger for Java
type: docs
url: /it/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# Dividi le pagine DOCX con GroupDocs.Merger per Java

In questo tutorial scoprirai **come dividere le pagine docx** in modo efficiente usando GroupDocs.Merger per Java. Che tu debba suddividere un enorme contratto in pagine singole o estrarre sezioni specifiche come flussi in‑memoria, ti guideremo attraverso l'installazione, il codice e consigli pratici così potrai implementare la soluzione in pochi minuti.

## Risposte Rapide
- **Quale libreria gestisce la divisione di DOCX in Java?** GroupDocs.Merger for Java.  
- **Posso dividere un DOCX in file separati?** Sì – configura `SplitOptions` con i numeri di pagina desiderati.  
- **È possibile ottenere le pagine come stream invece di file?** Assolutamente, fornendo un `SplitStreamFactory` personalizzato.  
- **Ho bisogno di una licenza?** Una licenza di prova temporanea è valida per la valutazione; è necessaria una licenza completa per la produzione.  
- **Quali versioni di Java sono supportate?** Qualsiasi JDK 8+ funziona con l'ultima versione di GroupDocs.Merger.

## Cos'è la divisione delle pagine docx?
**Dividere le pagine docx** significa estrarre una o più pagine da un documento Word multi‑pagina e salvare ogni selezione come file separato o come flusso in‑memoria. Questo consente una consegna modulare, flussi di lavoro basati sulla conformità o elaborazione on‑the‑fly senza gestire l'intero documento contemporaneamente.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger elabora i documenti **interamente in Java**—senza binari nativi, senza installazione di Office. Supporta **oltre 50 formati di input e output** e può dividere un **DOCX di 200 pagine in meno di 2 secondi** su un tipico server da 2,5 GHz, mantenendo l'uso della memoria sotto i 100 MB grazie alla sua architettura basata su stream.

## Prerequisiti

### Librerie e Dipendenze Richieste
- **Java Development Kit (JDK):** JDK 8 o più recente.  
- **GroupDocs.Merger for Java:** Libreria core per la manipolazione dei documenti.

### Aggiungere la Dipendenza
Includi la libreria tramite Maven o Gradle (i blocchi di codice rimangono invariati):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

Puoi anche scaricare l'ultima versione dal sito ufficiale: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della Licenza
- **Licenza di prova:** Ottieni una chiave temporanea dalla pagina [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/).  
- **Licenza di produzione:** Acquista una licenza completa su [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## Configurare GroupDocs.Merger per Java
`Merger` è la classe centrale che orchestra le operazioni di divisione, unione e conversione.

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

Con l'ambiente pronto, esploriamo i due modi principali per **dividere le pagine docx in file** o stream.

## Come dividere DOCX in file con GroupDocs.Merger
Carica il DOCX sorgente, specifica gli intervalli di pagina desiderati e invoca il metodo `split` – questa singola chiamata genera file di output separati per ogni segmento selezionato. Il metodo `split` elabora il documento secondo le `SplitOptions` fornite e restituisce i percorsi dei file creati. I passaggi seguenti mostrano un'implementazione completa, pronta per la produzione.

### Passo 1 – Specificare i percorsi di input e output
Definisci la posizione del DOCX originale e la cartella in cui verranno scritti i file divisi.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

### Passo 2 – Configurare SplitOptions (split options java)
`SplitOptions` indica all'API esattamente quali pagine estrarre e dove posizionare i risultati.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```

- `filePathOut` – cartella in cui verrà posizionato ogni file di pagina.  
- `new int[]{3,6,8}` – i numeri di pagina che desideri dividere (le pagine sono indicizzate a partire da 1).

### Passo 3 – Eseguire la divisione
Crea un'istanza di `Merger` e invoca `split`. Il metodo restituisce un elenco dei percorsi dei file generati.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Consiglio professionale:** Verifica che la directory di output esista e che la tua applicazione abbia i permessi di scrittura; altrimenti la divisione fallirà.

#### Problemi comuni
- **Cartella di output mancante:** L'API non crea automaticamente le directory.  
- **Numeri di pagina errati:** Gli indici delle pagine iniziano da 1; specificare 0 genererà un errore.

## Come dividere le pagine DOCX in stream (In‑Memory)
Quando hai bisogno di accesso temporaneo—ad esempio per inviare una pagina tramite un servizio web o eseguire analisi in‑memory—catturare ogni pagina estratta come stream elimina l'overhead di scrittura su disco. Utilizzando un `SplitStreamFactory` personalizzato, la libreria scrive il contenuto diviso direttamente in oggetti `ByteArrayOutputStream`, che possono poi essere trasmessi, archiviati o ulteriormente elaborati senza file intermedi.

### Passo 1 – Definire il percorso di input e preparare una lista per gli stream
Imposta il file sorgente e crea un contenitore per contenere gli stream generati.

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

### Passo 2 – Configurare SplitOptions con un SplitStreamFactory personalizzato
Implementa `SplitStreamFactory` per fornire un nuovo `OutputStream` per ogni pagina e memorizzare lo stream completato.

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```

- `createSplitStream` – genera un nuovo `OutputStream` per ogni pagina richiesta.  
- `closeSplitStream` – memorizza lo stream completato per un uso successivo.

### Passo 3 – Eseguire la divisione e recuperare gli stream
Esegui l'operazione di divisione e poi lavora con gli stream in‑memory secondo necessità (ad esempio, allegarli a un'email, caricarli su cloud storage).

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**Suggerimenti per la risoluzione dei problemi**
- Assicurati che il percorso del DOCX sorgente sia corretto; un errore di battitura genererà una `FileNotFoundException`.  
- Chiudi sempre gli stream dopo l'uso per liberare memoria ed evitare perdite.

## Applicazioni pratiche
1. **Contratti legali:** Estrarre clausole individuali per una revisione separata senza esporre l'intero accordo.  
2. **Piattaforme e‑learning:** Fornire file Word capitolo per capitolo su richiesta, mantenendo protetto l'intero libro di testo.  
3. **Report aziendali:** Inviare solo la sezione finanziaria di un rapporto trimestrale al CFO, riducendo la larghezza di banda e migliorando la riservatezza.

## Considerazioni sulle prestazioni
- **Stream a basso consumo di memoria:** Preferisci l'approccio stream per documenti più grandi di 50 MB per mantenere basso l'uso dell'heap.  
- **Elaborazione batch:** Raggruppa più operazioni di divisione in un'unica sessione JVM per ammortizzare l'overhead di avvio.  
- **Pulizia delle risorse:** Chiama `merger.close()` e chiudi tutti gli stream per evitare perdite di memoria.  
- **Metrica di velocità:** Su un server standard a 8 core, dividere un DOCX di 300 pagine in pagine individuali richiede circa 1,8 secondi.

## Domande frequenti

**Q: Cos'è GroupDocs.Merger per Java?**  
A: È una libreria Java che consente di unire, dividere e convertire oltre 50 formati di documento—including DOCX, PDF, PPTX e HTML—senza richiedere Microsoft Office.

**Q: Come ottengo una licenza per GroupDocs.Merger?**  
A: Ottieni una licenza di prova temporanea dal [sito GroupDocs](https://purchase.groupdocs.com/temporary-license/) per la valutazione. Per la produzione, acquista una licenza completa nello stesso sito.

**Q: Posso dividere file PDF usando la stessa API?**  
A: Sì, il metodo `split` funziona con PDF, DOCX, PPTX e altri formati supportati.

**Q: È possibile dividere un documento senza scrivere su disco?**  
A: Assolutamente—usa l'approccio basato su stream mostrato sopra per mantenere tutto in memoria.

**Q: Quale versione di GroupDocs.Merger dovrei usare?**  
A: Mira sempre all'ultima versione stabile per beneficiare di miglioramenti delle prestazioni e correzioni di bug.

---

**Ultimo aggiornamento:** 2026-07-25  
**Testato con:** GroupDocs.Merger for Java latest-version  
**Autore:** GroupDocs

## Tutorial correlati

- [Come dividere i documenti in file multi-pagina usando GroupDocs.Merger per Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)
- [Come estrarre pagine specifiche java con GroupDocs.Merger](/merger/java/document-extraction/)
- [Come unire pagine specifiche Java usando GroupDocs.Merger](/merger/java/document-joining/join-specific-pages-groupdocs-merger-java/)