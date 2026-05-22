---
date: '2026-02-06'
description: Scopri come dividere i file DOCX usando GroupDocs.Merger per Java, coprendo
  la divisione dei docx in file, le opzioni di split in Java e l'estrazione di stream.
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: Come dividere un DOCX con GroupDocs.Merger per Java
type: docs
url: /it/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# Master Java Document Splitting with GroupDocs.Merger: Split DOCX Pages into Files and Streams

In questo tutorial scoprirai **come dividere i docx** in modo efficiente con GroupDocs.Merger per Java. Che tu debba suddividere un grande contratto in pagine separate o estrarre sezioni specifiche come stream, ti guideremo passo dopo passo, dalla configurazione all'uso pratico.

## Quick Answers
- **Quale libreria gestisce la divisione dei DOCX in Java?** GroupDocs.Merger per Java.  
- **Posso dividere un DOCX in file separati?** Sì – usa `SplitOptions` con i numeri di pagina.  
- **È possibile ottenere le pagine come stream invece che come file?** Assolutamente sì, fornendo un `SplitStreamFactory` personalizzato.  
- **È necessaria una licenza?** Una licenza di prova temporanea è sufficiente per la valutazione; per la produzione è richiesta una licenza completa.  
- **Quali versioni di Java sono supportate?** Qualsiasi JDK 8+ funziona con l'ultima release di GroupDocs.Merger.

## What is “how to split docx”?
Dividere un DOCX significa prendere un documento Word multi‑pagina e creare file (o stream) individuali che contengono una o più pagine selezionate. Questo è utile per la consegna modulare dei documenti, flussi di lavoro di conformità o elaborazioni on‑the‑fly dove non si desidera memorizzare file temporanei.

## Why use GroupDocs.Merger for Java?
- **Zero‑dependency processing:** Funziona con Java puro, senza binari nativi.  
- **Fine‑grained control:** Scegli le pagine esatte, i formati di output e persino gli stream in memoria.  
- **Scalable performance:** La divisione basata su stream riduce la pressione sulla memoria per file di grandi dimensioni.  

## Prerequisites

### Required Libraries and Dependencies
- **Java Development Kit (JDK):** JDK 8 o versioni successive.  
- **GroupDocs.Merger for Java:** La libreria principale per la manipolazione dei documenti.

### Adding the Dependency
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

Puoi anche scaricare l'ultima release dal sito ufficiale: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### License Acquisition
- **Trial license:** Ottieni una chiave temporanea dalla pagina [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/).  
- **Production license:** Acquista una licenza completa su [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## Setting Up GroupDocs.Merger for Java
Inizializza la libreria nel tuo progetto Java:

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

Con l'ambiente pronto, esploriamo i due modi principali per **split docx into files** o stream.

## How to Split DOCX into Files with GroupDocs.Merger

### Split Document into Single Pages
#### Overview
Questo approccio crea un file separato per ciascuna pagina selezionata, ideale per distribuire sezioni individuali.

#### Step‑by‑Step Implementation

**Step 1 – Specify Input and Output Paths**  
Definisci dove si trova il DOCX originale e dove devono essere salvati i file divisi.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**Step 2 – Configure SplitOptions (split options java)**  
Indica alla libreria quali pagine estrarre.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – cartella in cui verrà collocato ogni file di pagina.  
- `new int[]{3,6,8}` – i numeri di pagina che **vuoi** dividere.

**Step 3 – Perform the Split**  
Esegui l'operazione con l'istanza `Merger`.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Pro tip:** Verifica che la directory di output esista e che la tua **applicazione** abbia i permessi di **scrittura**; altrimenti la divisione **fallirà**.

### Common Pitfalls
- **Missing output folder:** L'API non crea automaticamente le directory.  
- **Incorrect page numbers:** Gli indici delle pagine partono da 1; specificare 0 genererà un errore.

## How to Split DOCX Pages to Streams (In‑Memory)

### Overview
Quando hai bisogno di accesso temporaneo—ad esempio per inviare una pagina tramite un servizio web—catturare le pagine come stream evita I/O su disco.

#### Step‑by‑Step Implementation

**Step 1 – Define Input Path and Prepare a List for Streams**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**Step 2 – Configure SplitOptions with a Custom SplitStreamFactory**  

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
- `closeSplitStream` – conserva lo stream completato per un uso successivo.

**Step 3 – Execute the Split and Retrieve Streams**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**Troubleshooting Tips**
- Assicurati che il percorso del DOCX di origine sia corretto; un errore di battitura solleverà una `FileNotFoundException`.  
- Chiudi sempre gli stream dopo l'uso per liberare memoria.

## Practical Applications
1. **Legal contracts:** Estrarre clausole individuali per una revisione separata.  
2. **E‑learning platforms:** Fornire file Word capitolo per capitolo senza esporre l'intero libro di testo.  
3. **Business reporting:** Inviare solo la sezione finanziaria di un report trimestrale al CFO.

## Performance Considerations
- **Memory‑efficient streams:** Preferisci l'approccio stream per documenti di grandi dimensioni (>50 MB).  
- **Batch processing:** Raggruppa più operazioni di divisione in un'unica sessione JVM per ridurre il sovraccarico di avvio.  
- **Resource cleanup:** Chiama `merger.close()` e chiudi tutti gli stream per evitare perdite di risorse.

## Conclusion
Ora sai **come dividere i docx** in file separati o stream in‑memory usando GroupDocs.Merger per Java. Queste tecniche ti offrono la flessibilità necessaria per adattare la consegna dei documenti a qualsiasi esigenza aziendale.

**Next Steps**
- Sperimenta con diversi intervalli di pagine e formati di output (PDF, HTML, ecc.).  
- Combina la divisione con la fusione per ricomporre bundle personalizzati al volo.  

## Frequently Asked Questions

**Q: What is GroupDocs.Merger for Java?**  
A: È una libreria Java che consente di unire, dividere e convertire una vasta gamma di formati di documento, inclusi DOCX, PDF, PPTX e altri.

**Q: How do I obtain a license for GroupDocs.Merger?**  
A: Puoi ottenere una licenza di prova temporanea dal [sito GroupDocs](https://purchase.groupdocs.com/temporary-license/) per la valutazione. Per l'uso in produzione, acquista una licenza completa nello stesso sito.

**Q: Can I split PDF files using the same API?**  
A: Sì, il metodo `split` funziona con PDF, DOCX, PPTX e altri formati supportati.

**Q: Is it possible to split a document without writing to disk?**  
A: Assolutamente sì—usa l'approccio basato su stream mostrato sopra per mantenere tutto in memoria.

**Q: Which version of GroupDocs.Merger should I use?**  
A: Puntare sempre all'ultima release stabile per beneficiare di miglioramenti di performance e correzioni di bug.

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger for Java latest-version  
**Author:** GroupDocs