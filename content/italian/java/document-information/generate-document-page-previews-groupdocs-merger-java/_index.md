---
date: '2026-01-24'
description: Scopri come visualizzare in anteprima i documenti generando anteprime
  di pagina con GroupDocs.Merger per Java, un modo rapido per convertire le pagine
  in immagini per la generazione di miniature dei documenti.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: Come visualizzare l'anteprima dei documenti con GroupDocs.Merger per Java
type: docs
url: /it/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

visualizzare rapidamente i documenti** , offrendo agli utenti un'istantanea visiva senza aprire l'intero file. In questo tutorial imparerai a generare tali anteprime usando GroupDocs.Merger per Java, una libreria che semplifica **la conversione delle pagine in immagini** e supporta **la generazione di miniature dei documenti** nelle tue applicazioni.

## Risposte rapide
- **Cosa significa “preview documents”?** Generazione di rappresentazioni immagine leggere di ogni pagina.  
- **Quale formato viene usato per le anteprime?** JPEG per impostazione predefinita, ma sono supportati altri formati.  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per lo sviluppo; è necessaria una licenza a pagamento per la produzione.  
- **Posso personalizzare il percorso di output?** Sì, implementando un `PageStreamFactory` personalizzato.  
- **Quale versione di Java è richiesta?** JDK 8 o successivo.

## Cos'è “preview documents”?
Visualizzare l'anteprima dei documenti significa creare miniature visive (spesso JPEG o PNG) per ogni pagina in modo che gli utenti possano scorrere rapidamente il contenuto. Questa tecnica migliora l'esperienza utente nei sistemi di gestione documentale, nei portali e in qualsiasi applicazione che gestisce molti file.

## Perché usare GroupDocs.Merger per Java?
- **Conversione rapida** delle pagine in immagini senza aprire l'intero documento in un'interfaccia.  
- **Supporto integrato** per molti formati (PDF, DOCX, XLSX, ecc.).  
- **API estensibile** ti consente di controllare dove e come vengono salvati i file di anteprima.  

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
- **Free Trial:** Inizia scaricando una prova gratuita per esplorare le funzionalità.  
- **Temporary License:** Ottieni una licenza temporanea per accesso esteso durante lo sviluppo.  
- **Purchase:** Per l'uso in produzione completa, acquista una licenza da [GroupDocs](https://purchase.groupdocs.com/buy).

Una volta aggiunta la libreria, inizializzala con il percorso del documento che desideri visualizzare in anteprima:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Come visualizzare l'anteprima dei documenti: Guida passo‑pass: Inizializza Merger e definisci un PageStreamFactory
Il `PageStreamFactory` indica alla libreria dove scrivere ogni immagine di anteprima.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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

### Passo 2: Genera le anteprime
Chiama il metodo `generatePreview` con le opzioni appena configurate.

```java
merger.generatePreview(previewOption);
```

### Converti pagine in immagini – PageStreamFactory personalizzato
Se hai bisogno di più controllo sul nome dei file o sulla posizione di archiviazione, implementa la tua factory:

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

## Generazione di miniature dei documenti – Applicazioni pratiche
Generare anteprime è particolarmente utile per:

1. **Document Management Systems** – Gli utenti possono scorrere i file senza aprirli.  
2. **Content Review Platforms** – Controlli visivi rapidi prima di approvare i caricamenti.  
3. **Educational Tools** – Gli studenti possono dare un'occhiata alle diapositive delle lezioni o alle pagine dei libri di testo.  

## Considerazioni sulle prestazioni
- **Rilascia gli stream prontamente** per liberare memoria.  
- **Evita di caricare interi documenti** in memoria; lascia che la libreria gestisca il paging.  
- **Usa impostazioni di qualità dell'immagine appropriate** per bilanciare velocità e fedeltà visiva.

## Domande frequenti

**Q: A cosa serve GroupDocs.Merger per Java?**  
A: È usato per unire, dividere e gestire documenti in modo efficiente, inclusa la generazione di anteprime.

**Q: Come gestisco le eccezioni durante le operazioni di stream?**  
A: Avvolgi la creazione e la chiusura dello stream in blocchi try‑catch JPEG?**  
A `PreviewMode` in PNG, BMP, ecc., per soddisfare le tue esigenze.

**Q: Quali sono i problemi comuni nella generazione di anteprime dei document altre applicazioni Java del flusso di lavoro.

## Risorse aggiuntive
- [Documentazione](https://docs.groupdocs.com/merger/java/)
- [Riferimento API](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Acquista](https://purchase.groupdocs.com/buy)
- [Prova gratuita](https://releases.groupdocs.com/merger/java/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Supporto](https://forum.groupdocs.com/c/merger/)

 ultima versione (2025‑latest)  
**Autore:** GroupDocs