---
date: '2026-10-06'
description: Scopri come unire immagini png in Java con GroupDocs.Merger. Questa guida
  passo‑passo copre l'installazione, l'inizializzazione del codice, le opzioni di
  unione e consigli pratici per combinare file PNG.
keywords:
- how to merge png
- combine png files
- java image processing
- java image manipulation
- java merge images
lastmod: '2026-10-06'
og_description: Scopri come unire immagini png in Java con GroupDocs.Merger. Segui
  questa guida per configurare la libreria, impostare le opzioni di unione e creare
  grafiche composite in modo efficiente.
og_image_alt: Developer guide showing Java code that merges PNG images using GroupDocs.Merger
og_title: Come unire immagini png in Java usando GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-10-06'
  description: Learn how to merge png images in Java with GroupDocs.Merger. This step‑by‑step
    guide covers setup, code initialization, merge options, and practical tips for
    combining PNG files.
  headline: How to merge png images in Java using GroupDocs.Merger
  type: TechArticle
- description: Learn how to merge png images in Java with GroupDocs.Merger. This step‑by‑step
    guide covers setup, code initialization, merge options, and practical tips for
    combining PNG files.
  name: How to merge png images in Java using GroupDocs.Merger
  steps:
  - name: import necessary classes
    text: 'Start by importing the required classes from the GroupDocs package:'
  - name: define file paths
    text: 'Set up absolute or relative paths for the source image and any additional
      images you want to combine:'
  - name: initialize the Merger object and configure join options
    text: Create a `Merger` instance with the primary image, then specify how subsequent
      images should be combined. `ImageJoinMode.Vertical` stacks images on top of
      each other, while `ImageJoinMode.Horizontal` places them side‑by‑side.
  - name: perform the merge and save the result
    text: 'Add each extra image with `join` and write the merged output to disk: Adjust
      the `ImageJoinMode` enum if you need a different orientation, such as `Horizontal`
      for side‑by‑side banners.'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java
    question: What library should I use?
  - answer: Yes – call `join` for each additional image.
    question: Can I merge multiple PNGs at once?
  - answer: '`ImageJoinMode.Vertical`'
    question: Which merge mode creates a vertical stack?
  - answer: A trial license works for testing; a paid license removes limitations.
    question: Do I need a license?
  - answer: JDK 8 or later
    question: What Java version is required?
  type: FAQPage
tags:
- merge png
- GroupDocs.Merger
- Java image processing
- java image manipulation
- image merging tutorial
title: Come unire immagini png in Java usando GroupDocs.Merger
type: docs
url: /it/java/document-information/merge-png-images-groupdocs-merger-java/
weight: 1
---

# Come unire immagini png in Java usando GroupDocs.Merger

Unire file PNG programmaticamente è una necessità frequente quando è necessario creare un unico banner, combinare risorse di design o generare grafiche composite al volo. In questo tutorial imparerai **come unire png** immagini con GroupDocs.Merger per Java, dall'installazione della libreria alla produzione del file finale unito. Che tu stia creando un servizio web che assembla risorse di marketing o un'utilità desktop per l'elaborazione batch, i passaggi seguenti ti porteranno rapidamente al risultato.

## Risposte rapide
- **Quale libreria dovrei usare?** GroupDocs.Merger for Java  
- **Posso unire più PNG contemporaneamente?** Sì – chiama `join` per ogni immagine aggiuntiva.  
- **Quale modalità di unione crea una pila verticale?** `ImageJoinMode.Vertical`  
- **Ho bisogno di una licenza?** Una licenza di prova funziona per i test; una licenza a pagamento rimuove le limitazioni.  
- **Quale versione di Java è richiesta?** JDK 8 o successiva  

## Cos'è una libreria Java per la manipolazione di immagini?
Una **java image manipulation library** è un insieme di classi Java che consentono agli sviluppatori di modificare, combinare e trasformare programmaticamente file immagine senza occuparsi della gestione a basso livello dei pixel. GroupDocs.Merger è una di queste librerie, offrendo operazioni di alto livello come unire, dividere e convertire immagini e documenti. Utilizzare una libreria dedicata fa risparmiare tempo di sviluppo, migliora le prestazioni e garantisce una gestione affidabile di molti formati di immagine.

## Perché usare GroupDocs.Merger per l'unione di PNG?
Carica i tuoi due file PNG e chiama `join` – la libreria esegue il lavoro pesante in una singola riga di codice. GroupDocs.Merger supporta **30+ formati di immagini e documenti**, elabora file di centinaia di pagine senza caricare l'intero contenuto in memoria e può gestire immagini fino a **500 MB** mantenendo l'utilizzo della CPU sotto il **30 %** su un server tipico. Queste capacità quantificate lo rendono una scelta scalabile sia per piccole utility sia per pipeline di livello enterprise.

## Prerequisiti
- **Java Development Kit (JDK):** versione 8 o successiva installata.  
- **Maven o Gradle:** per la gestione delle dipendenze.  
- **Conoscenza di base di Java:** dovresti sentirti a tuo agio con classi, oggetti e gestione delle eccezioni.  
- **Licenza GroupDocs:** una chiave di prova è sufficiente per lo sviluppo; acquista una licenza completa per l'uso in produzione.

## Configurare GroupDocs.Merger per Java

### Installazione Maven
Aggiungi la seguente dipendenza al tuo file `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Installazione Gradle
Per i progetti che usano Gradle, includi questo nel tuo file `build.gradle`:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Download diretto
In alternativa, scarica l'ultima versione direttamente dalla [pagina dei rilasci di GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/).

Per attivare una prova o acquistare una licenza, visita il loro sito web su [GroupDocs Purchases](https://purchase.groupdocs.com/buy) e segui i passaggi per ottenere la tua licenza temporanea o completa.

## Inizializzazione di base
La classe `Merger` è il componente principale che gestisce l'unione di immagini e altre operazioni sui documenti.

```java
import com.groupdocs.merger.Merger;

class ImageMerger {
    public static void main(String[] args) {
        Merger merger = new Merger("path/to/your/image.png");
    }
}
```

## Come unire immagini png con GroupDocs.Merger
I passaggi seguenti dimostrano come combinare più file PNG in un'unica immagine usando l'API di alto livello di GroupDocs.Merger. Inizializzando l'oggetto Merger, aggiungendo le immagini di origine, selezionando una modalità di unione e salvando il risultato, è possibile creare compositi verticali o orizzontali con un codice minimo.

### Panoramica
Puoi unire file PNG in poche righe di codice Java. La libreria astrae la manipolazione a livello di pixel, permettendoti di concentrarti sulla logica di business della tua applicazione.

### Passo 1: importare le classi necessarie
Inizia importando le classi necessarie dal pacchetto GroupDocs:

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.ImageJoinMode;
import com.groupdocs.merger.domain.options.ImageJoinOptions;
```

### Passo 2: definire i percorsi dei file
Imposta percorsi assoluti o relativi per l'immagine di origine e per eventuali immagini aggiuntive da combinare:

```java
String sourceImagePath = "YOUR_DOCUMENT_DIRECTORY/sample.png";
String additionalImagePath = "YOUR_DOCUMENT_DIRECTORY/additional_sample.png";
String outputFolder = "YOUR_OUTPUT_DIRECTORY";
String outputFile = new File(outputFolder, "merged.png").getPath();
```

### Passo 3: inizializzare l'oggetto Merger e configurare le opzioni di unione
Crea un'istanza `Merger` con l'immagine primaria, quindi specifica come le immagini successive devono essere combinate. `ImageJoinMode.Vertical` impila le immagini una sopra l'altra, mentre `ImageJoinMode.Horizontal` le posiziona fianco a fianco.

```java
Merger merger = new Merger(sourceImagePath);
ImageJoinOptions joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
```

### Passo 4: eseguire l'unione e salvare il risultato
Aggiungi ogni immagine extra con `join` e scrivi l'output unito su disco:

```java
merger.join(additionalImagePath, joinOptions);
merger.save(outputFile);
```

Regola l'enumerazione `ImageJoinMode` se hai bisogno di un orientamento diverso, come `Horizontal` per banner affiancati.

## Applicazioni pratiche
Unire immagini PNG è utile in molti scenari reali:

1. **Materiali di marketing:** Assembla più elementi di design in un unico banner per campagne pubblicitarie.  
2. **Sviluppo web:** Genera dinamicamente immagini di intestazione responsive unendo risorse di dimensioni diverse.  
3. **Fotografia:** Crea panorami o collage da una serie di scatti senza editing manuale.  

Integrare questa funzionalità in un sistema di gestione dei contenuti, una libreria di risorse digitali o uno strumento di design personalizzato può accelerare notevolmente i flussi di lavoro di produzione.

## Considerazioni sulle prestazioni
- **Gestione della memoria:** Usa l'API di streaming `Merger` per file più grandi di 200 MB per evitare `OutOfMemoryError`.  
- **Allocazione delle risorse:** Assegna almeno 2 GB di heap quando elabori PNG ad alta risoluzione superiori a 3000 × 3000 px.  
- **Concorrenza:** Esegui le unioni su thread separati solo dopo aver confermato la thread‑safety dell'istanza `Merger` (la libreria è thread‑safe per operazioni di sola lettura).  

Seguire queste best practice garantisce un funzionamento fluido anche sotto carico elevato.

## Domande frequenti

**Q1: Posso unire più di due immagini PNG contemporaneamente?**  
A1: Sì, chiama `join` ripetutamente per ogni immagine aggiuntiva prima di invocare `save`. La libreria le concatenerà nell'ordine specificato.

**Q2: Come gestisco le eccezioni durante il processo di unione?**  
A2: Avvolgi la logica di unione in un blocco `try‑catch` e cattura `MergerException` per acquisire errori specifici dell'API, quindi gestiscili o registrali secondo necessità.

**Q3: GroupDocs.Merger è gratuito da usare?**  
A3: Puoi iniziare con una licenza di prova gratuita che fornisce piena funzionalità per la valutazione. L'uso in produzione richiede una licenza acquistata per rimuovere i limiti di utilizzo.

**Q4: Quali formati supporta GroupDocs.Merger oltre a PNG?**  
A5: La libreria supporta oltre 30 formati, inclusi JPEG, BMP, TIFF, PDF, DOCX e XLSX. Consulta la matrice ufficiale dei formati per l'elenco completo.

**Q5: Come posso personalizzare dinamicamente il nome e la posizione del file di output?**  
A5: Costruisci la stringa `outputFile` usando variabili come timestamp, ID utente o valori di configurazione, quindi passala al metodo `save`.

## Risorse
- [Documentazione GroupDocs](https://docs.groupdocs.com/merger/java/) – guide complete e tutorial.  
- [documentazione](https://docs.groupdocs.com/merger/java/) – stesso URL con testo alternativo.  
- [Documentazione GroupDocs](https://docs.groupdocs.com/merger/java/) – portale ufficiale della documentazione.  
- [Riferimento API GroupDocs](https://reference.groupdocs.com/merger/java/) – descrizioni dettagliate dei metodi API.  
- [Rilasci GroupDocs](https://releases.groupdocs.com/merger/java/) – pagina di download per tutti i rilasci della libreria.  
- [Pagina di acquisto GroupDocs](https://purchase.groupdocs.com/buy) – dove acquistare una licenza completa.  
- [Prova gratuita GroupDocs](https://releases.groupdocs.com/merger/java/) – ottieni una versione di prova della libreria.  
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/) – richiedi una licenza a breve termine per i test.  
- [Forum di supporto GroupDocs](https://forum.groupdocs.com/c/merger/) – aiuto della community e Q&A.

---

**Ultimo aggiornamento:** 2026-10-06  
**Testato con:** ultima versione di GroupDocs.Merger (al 2026)  
**Autore:** GroupDocs

## Tutorial correlati

- [Come unire immagini in Java: padroneggiare l'unione di immagini con GroupDocs.Merger per file BMP](/merger/java/image-operations/mastering-image-merging-java-groupdocs-merger/)  
- [Come combinare immagini TIFF usando GroupDocs.Merger per Java: guida passo‑passo](/merger/java/format-specific-merging/merge-tiff-files-groupdocs-merger-java/)  
- [Unire facilmente file SVGZ usando GroupDocs.Merger per Java: guida completa](/merger/java/format-specific-merging/merge-svgz-files-groupdocs-merger-java/)