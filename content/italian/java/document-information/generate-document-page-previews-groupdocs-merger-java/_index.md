---
date: '2026-06-26'
description: Scopri come convertire le pagine PDF in immagini e visualizzare in anteprima
  i documenti usando GroupDocs.Merger per Java – il modo rapido e affidabile per generare
  le miniature delle pagine.
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: Come convertire le pagine PDF in immagini e visualizzare in anteprima i documenti
  con GroupDocs.Merger per Java
type: docs
url: /it/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# Come convertire le pagine PDF in immagini e visualizzare i documenti con GroupDocs.Merger per Java

Nelle applicazioni moderne è spesso necessario **convertire le pagine pdf in immagini** in modo che gli utenti possano dare un'occhiata a un documento senza scaricare l'intero file. Questo tutorial ti guida nella generazione di anteprime di pagina ad alta qualità con GroupDocs.Merger per Java, coprendo tutto, dall'installazione alla gestione di storage personalizzato. Alla fine, avrai una soluzione riutilizzabile per la generazione di miniature di documenti che funziona su qualsiasi ambiente JDK 8+.

## Risposte rapide
- **Cosa significa “preview documents”?** Generazione di rappresentazioni immagine leggere di ogni pagina.  
- **Quale formato viene utilizzato per le anteprime?** JPEG per impostazione predefinita, ma sono supportati altri formati.  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per lo sviluppo; è necessaria una licenza a pagamento per la produzione.  
- **Posso personalizzare il percorso di output?** Sì, implementando un `PageStreamFactory` personalizzato.  
- **Quale versione di Java è richiesta?** JDK 8 o successiva.

## Che cosa significa “preview documents”?
La visualizzazione dei documenti consiste nel creare miniature visive (solitamente JPEG o PNG) per ogni pagina, così gli utenti possono scorrere rapidamente il contenuto. Questa tecnica migliora l'esperienza utente nei file browser, nei portali di revisione dei contenuti e in qualsiasi sistema che gestisce un gran numero di documenti, fornendo un'indicazione visiva rapida senza aprire il file completo.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger converte le pagine PDF in immagini **in meno di 0,5 secondi per pagina su una CPU tipica da 2 GHz**, supporta **oltre 50 formati di input e output**, e ti consente di trasmettere le anteprime direttamente allo storage senza caricare l'intero file in memoria. La sua API estensibile ti offre anche il pieno controllo sulla qualità dell'immagine, sul formato e sul percorso di destinazione.

## Prerequisiti
- **Libreria GroupDocs.Merger per Java** (vedi installazione sotto).  
- **JDK 8+** installato sulla tua macchina.  
- Un IDE (IntelliJ IDEA, Eclipse, NetBeans) e Maven o Gradle per la gestione delle dipendenze.  

## Configurazione di GroupDocs.Merger per Java
Aggiungi la libreria al tuo progetto usando lo strumento di build preferito.

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

**Download diretto:**  
In alternativa, scarica l'ultima versione da [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza
- **Free Trial:** Inizia scaricando una versione di prova gratuita per esplorare le funzionalità.  
- **Temporary License:** Ottieni una licenza temporanea per accesso esteso durante lo sviluppo.  
- **Purchase:** Per l'uso in produzione, acquista una licenza da [GroupDocs](https://purchase.groupdocs.com/buy).

Una volta aggiunta la libreria, inizializzala con il percorso del documento che desideri visualizzare:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Come visualizzare i documenti: Guida passo‑passo
Carica il file sorgente, configura un `PageStreamFactory` e chiama `generatePreview`.  
`generatePreview` è un metodo che converte ogni pagina del documento in un'immagine secondo le opzioni fornite.

### Passo 1: Inizializzare Merger e definire un PageStreamFactory
`Merger` è la classe principale che fornisce metodi per unire, dividere e generare anteprime di documenti.  
`PageStreamFactory` è un'interfaccia che indica alla libreria dove scrivere ogni immagine di anteprima.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

Qui creiamo un'implementazione personalizzata che scrive ogni immagine di pagina in una cartella specifica con uno schema di denominazione prevedibile.

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### Passo 2: Generare le anteprime
`generatePreview` avvia il processo di conversione in base alle opzioni fornite. Trasmette ogni immagine di pagina al `PageStreamFactory` definito, garantendo un basso utilizzo di memoria.

```java
merger.generatePreview(previewOption);
```

### Convertire le pagine in immagini – PageStreamFactory personalizzato
Se hai bisogno di più controllo sulla denominazione dei file o sulla posizione di storage, implementa la tua factory:

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### Metodi di supporto – Gestione degli stream
Questi metodi di utilità mantengono il codice ordinato e gestiscono le eccezioni in modo pulito.

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## Generazione di miniature di documenti – Applicazioni pratiche
Generare anteprime è particolarmente utile per:

1. **Document Management Systems** – Gli utenti possono scorrere i file senza aprirli.  
2. **Content Review Platforms** – Controlli visivi rapidi prima di approvare i caricamenti.  
3. **Educational Tools** – Gli studenti possono dare un'occhiata a diapositive o pagine di libri di testo.  

## Considerazioni sulle prestazioni
- **Rilasciare gli stream prontamente** per liberare memoria.  
- **Evitare di caricare interi documenti** in memoria; lascia che la libreria gestisca il paging.  
- **Usare impostazioni di qualità dell'immagine appropriate** per bilanciare velocità e fedeltà visiva.  

## Domande frequenti

**Q: A cosa serve GroupDocs.Merger per Java?**  
A: È usato per unire, dividere e gestire documenti in modo efficiente, inclusa la generazione di anteprime e la conversione di formati.

**Q: Come gestire le eccezioni durante le operazioni di stream?**  
A: Avvolgi la creazione e la chiusura dello stream in blocchi try‑catch, come mostrato nei metodi di supporto, per prevenire perdite di memoria.

**Q: Posso generare anteprime in formati diversi da JPEG?**  
A: Sì, cambia l'enumerazione `PreviewMode` in PNG, BMP o TIFF per soddisfare le tue esigenze.

**Q: Quali sono i problemi comuni nella generazione di anteprime di documenti?**  
A: I problemi tipici includono percorsi file errati e dimenticare di chiudere gli stream, il che può causare perdite di memoria.

**Q: Come posso integrare GroupDocs.Merger con altri sistemi?**  
A: Usa la sua API per connetterti a database, servizi web o altre applicazioni Java per un'automazione del flusso di lavoro senza interruzioni.

---

## Risorse
- [Rilasci di GroupDocs.Merger per Java](https://releases.groupdocs.com/merger/java/)  
- [Scarica](https://releases.groupdocs.com/merger/java/)  
- [Documentazione](https://docs.groupdocs.com/merger/java/)  
- [Riferimento API](https://reference.groupdocs.com/merger/java/)  
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)  
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)  
- [Acquisto](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [Supporto](https://forum.groupdocs.com/c/merger/)

**Ultimo aggiornamento:** 2026-06-26  
**Testato con:** GroupDocs.Merger ultima versione (2025‑latest)  
**Autore:** GroupDocs

## Tutorial correlati

- [Tutorial sulle operazioni di pagine di documento per GroupDocs.Merger Java](/merger/java/page-operations/)
- [Come caricare un PDF da un URL usando GroupDocs.Merger per Java: Guida completa](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [Creare PDF a pagina singola con GroupDocs.Merger Java](/merger/java/document-splitting/)