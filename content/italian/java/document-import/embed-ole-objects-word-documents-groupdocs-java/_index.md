---
date: '2025-12-19'
description: Scopri come incorporare PDF nei documenti Word e aggiungere PDF ai file
  Word con GroupDocs.Merger per Java. Tutorial passo‑passo per un'integrazione OLE
  senza interruzioni.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: Come incorporare PDF in Word usando GroupDocs.Merger per Java – Guida completa
type: docs
url: /it/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# Come incorporare PDF in Word usando GroupDocs.Merger per Java

Incorporare un PDF direttamente all'interno di un documento Word può migliorare notevolmente la collaborazione, perché i lettori non devono più passare da un file all'altro. In questa guida scoprirai **come incorporare PDF in Word** usando GroupDocs.Merger per Java, e vedrai consigli pratici su **come aggiungere PDF a Word** nei flussi di lavoro. Ti guideremo passo passo, dalla configurazione della libreria alla personalizzazione delle dimensioni e della posizione dell'oggetto OLE.

## Quick Answers
- **Quale libreria è necessaria?** GroupDocs.Merger per Java (ultima versione)  
- **Posso incorporare qualsiasi tipo di file?** Sì – PDF, immagini, fogli di calcolo, ecc., come oggetti OLE  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è necessaria una licenza commerciale per la produzione  
- **Quale IDE Java è consigliato?** IntelliJ IDEA, Eclipse o qualsiasi IDE che supporti Maven/Gradle  
- **Quanto tempo richiede l'implementazione?** Circa 10‑15 minuti per un'integrazione di base  

## Che cos'è l'incorporamento di PDF in Word?
Incornare un PDF crea un oggetto OLE (Object Linking and Embedding) all'interno del file Word. Il PDF rimane pienamente funzionale—gli utenti possono fare doppio clic sull'icona per aprirlo in un visualizzatore PDF, mentre il documento Word rimane autonomo.

## Perché aggiungere PDF a Word usando GroupDocs.Merger?
- **Documentazione a fonte unica:** Mantieni contratti, manuali o report insieme senza collegamenti esterni.  
- **Accessibilità migliorata:** I lettori possono visualizzare il PDF senza uscire dall'ambiente Word.  
- **Adatto all'automazione:** Perfetto per generare report batch o pacchetti legali in modo programmatico.

## Prerequisiti
- **Librerie e dipendenze:** Includi la libreria GroupDocs.Merger tramite Maven o Gradle.  
- **Ambiente di sviluppo:** IntelliJ IDEA, Eclipse o qualsiasi IDE Java.  
- **Conoscenze di base:** Familiarità con Java e i concetti di manipolazione dei documenti.

## Setting Up GroupDocs.Merger for Java
Per incorporare oggetti OLE, aggiungi prima la libreria al tuo progetto.

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
Includi questo nel tuo file `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct Download
In alternativa, scarica l'ultima versione dalla [pagina di rilascio di GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/).

**Acquisizione della licenza:** Puoi iniziare con una prova gratuita o ottenere una licenza temporanea per valutare le funzionalità prima dell'acquisto. Visita [Purchase GroupDocs](https://purchase.groupdocs.com/buy) per maggiori dettagli.

## Basic Initialization
Importa le classi necessarie per lavorare con gli oggetti OLE:

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Guida passo‑passo per incorporare PDF in Word

### Passo 1: Definisci i percorsi dei file e la pagina di destinazione
Imposta il documento Word di origine, il PDF da incorporare e dove dovrebbe apparire l'oggetto OLE.

```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – percorso del file Word esistente.  
- **`embeddedFilePath`** – il PDF che desideri **aggiungere a Word**.  
- **`outputFilePath`** – dove verrà salvato il nuovo documento.  
- **`pageNumber`** – la pagina che ospiterà l'oggetto OLE.

### Passo 2: Configura OleWordProcessingOptions
Personalizza l'aspetto del PDF incorporato impostando le sue dimensioni.

```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – controllano la dimensione dell'icona PDF all'interno del documento Word.

### Passo 3: Inizializza Merger e importa l'oggetto OLE
Crea un'istanza `Merger` per il documento di origine, importa l'oggetto OLE e salva il risultato.

```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – accetta le `OleWordProcessingOptions` e inserisce il PDF come oggetto OLE.  
- **`save()`** – scrive il documento modificato su `outputFilePath`.

### Passo 4: (Opzionale) Riapplica la configurazione per oggetti aggiuntivi
Se devi incorporare altri PDF, ripeti **Passo 1‑3** con nuovi percorsi file e numeri di pagina. La stessa classe `OleWordProcessingOptions` ti permette di controllare ogni oggetto individualmente.

## Configurazione di OleWordProcessingOptions (Avanzato)
Puoi ulteriormente regolare il posizionamento, ad esempio allineando l'oggetto o aggiungendo una didascalia. Il frammento di codice sotto ripete la configurazione di base per chiarezza:

```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Applicazioni pratiche
Incorporare PDF è utile in molti scenari reali:

1. **Manuali tecnici** – Inserisci schemi dettagliati o PDF di riferimento direttamente nella guida.  
2. **Report finanziari** – Aggiungi PDF di audit supplementari senza interrompere il flusso del report principale.  
3. **Contratti legali** – Allegare annexes o allegati come oggetti OLE per un facile accesso durante la revisione.

## Considerazioni sulle prestazioni
Quando si gestiscono documenti di grandi dimensioni o più oggetti OLE, tieni presente questi consigli:

- **Rimuovi contenuti non necessari** – incorpora solo le pagine di cui hai realmente bisogno.  
- **Gestisci la memoria** – usa il flag `-Xmx` di Java per allocare sufficiente heap per file di grandi dimensioni.  
- **Mantieniti aggiornato** – le versioni più recenti di GroupDocs.Merger includono spesso ottimizzazioni delle prestazioni.

## Domande frequenti

**D: Cos'è l'incorporamento OLE?**  
R: L'incorporamento consente di inserire oggetti come PDF nei documenti Word come collegamenti che mantengono la loro funzionalità originale.

**D: Posso incorporare più oggetti OLE in un unico documento?**  
R: Sì, ciascuno può essere configurato per pagine e dimensioni diverse usando `OleWordProcessingOptions` separate.

**D: Esiste un limite alle dimensioni dei file incorporati?**  
R: Il limite è generalmente determinato dalle restrizioni di Word, ma GroupDocs.Merger gestisce file di grandi dimensioni in modo efficiente.

**D: Come risolvere gli errori di incorporamento?**  
R: Verifica che i percorsi dei file siano corretti e che la JVM disponga di sufficiente memoria. Controlla che il PDF di origine non sia corrotto.

**D: Posso modificare gli oggetti incorporati dopo l'inserimento?**  
R: Puoi riaprire il file Word in Microsoft Word e modificare l'oggetto OLE, oppure rieseguire il codice Merger con opzioni aggiornate.

## Risorse aggiuntive
- [Documentazione di GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)  
- [Riferimento API](https://reference.groupdocs.com/merger/java/)  
- [Scarica l'ultima versione](https://releases.groupdocs.com/merger/java/)  
- [Acquista GroupDocs](https://purchase.groupdocs.com/buy)  
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)  
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)  
- [Forum di supporto](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Merger for Java latest version  
**Author:** GroupDocs