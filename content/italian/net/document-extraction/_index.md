---
date: 2026-08-31
description: Scopri come estrarre pagine specifiche da PDF usando GroupDocs.Merger
  per .NET. Guide passo‑passo coprono scenari di estrazione da Word, PDF e DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Scopri come estrarre pagine specifiche da PDF usando GroupDocs.Merger
  per .NET. Guide dettagliate ti aiutano a prelevare pagine da file PDF, Word e DOCX
  in modo efficiente.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Come estrarre pagine specifiche da PDF con GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Come estrarre pagine specifiche da PDF con GroupDocs.Merger
type: docs
url: /it/net/document-extraction/
weight: 9
---

# Come estrarre pagine specifiche pdf con GroupDocs.Merger

L'estrazione di pagine specifiche pdf è una necessità comune quando è necessario riutilizzare, condividere o archiviare solo una parte di un documento più grande. Con GroupDocs.Merger per .NET è possibile estrarre programmaticamente pagine singole, intervalli di pagine o selezioni personalizzate da file PDF, Word e DOCX senza modifiche manuali. Questo tutorial ti guida attraverso i concetti, i prerequisiti e il flusso di lavoro passo‑passo in modo da poter integrare l'estrazione di pagine in qualsiasi applicazione .NET.

## Risposte rapide
- **Cosa significa “extract specific pages pdf”?** Significa selezionare pagine individuali o intervalli da un PDF (o altro formato supportato) e salvarle come un nuovo documento più piccolo.  
- **Quali formati sono supportati?** GroupDocs.Merger gestisce oltre 50 formati di input e output, inclusi PDF, DOCX, PPTX e immagini.  
- **Ho bisogno di una licenza?** Una licenza temporanea funziona per i test; è necessaria una licenza completa per l'uso in produzione.  
- **Posso elaborare file di grandi dimensioni?** Sì – la libreria elabora file con centinaia di pagine usando lo streaming, mantenendo basso l'uso della memoria.  
- **Il .NET Core è supportato?** Assolutamente – l'API funziona con .NET Framework 4.6+, .NET Core 3.1+ e .NET 6/7.

## Cos'è extract specific pages pdf?
`extract specific pages pdf` si riferisce all'operazione di prendere una o più pagine da un PDF esistente (o documento supportato) e creare un nuovo PDF che contiene solo quelle pagine. Questo consente di condividere solo le sezioni rilevanti mantenendo intatto il file originale.

## Perché estrarre pagine specifiche pdf con GroupDocs.Merger?
GroupDocs.Merger elabora fino a **50+ formati di file** e può estrarre pagine da documenti contenenti **500+ pagine** in meno di **2 secondi** su una tipica CPU di livello server. L'API funziona senza richiedere l'installazione di Microsoft Office o Adobe Acrobat, riducendo la complessità di distribuzione e i costi di licenza.

## Prerequisiti
- .NET 6 SDK (o .NET Core 3.1 / .NET Framework 4.6+) installato sulla tua macchina di sviluppo.  
- Un pacchetto NuGet valido di GroupDocs.Merger per .NET (`GroupDocs.Merger`) aggiunto al tuo progetto.  
- (Opzionale) Un file di licenza temporaneo o completo se prevedi di eseguire il codice oltre il periodo di valutazione.

## Come estrarre pagine specifiche pdf in C# con GroupDocs.Merger

Carica il documento di origine, specifica le pagine necessarie e salva il risultato. La libreria astrae tutti i dettagli specifici del formato, quindi lo stesso codice funziona per PDF, DOCX, PPTX e altri.

Carica il tuo file di origine e chiama il metodo `Extract` con i numeri di pagina desiderati. Il metodo `Extract` crea un nuovo documento contenente solo le pagine specificate. Il metodo restituisce un nuovo oggetto `Document` che puoi salvare immediatamente. Un oggetto `Document` rappresenta una rappresentazione in memoria del file risultante.

### Passo 1: creare un'istanza Merger
La classe `Merger` è il punto di ingresso per caricare e manipolare i documenti. Istanzia la classe `Merger` passando il percorso del file di origine. Questo oggetto rappresenta il documento con cui lavorerai.

### Passo 2: specificare le pagine da estrarre
Fornisci un elenco di indici di pagina (basato su 1) o una stringa di intervallo come `"1-3,5"` per indicare alla libreria quali pagine conservare.

### Passo 3: salvare il documento estratto
Chiama `Save` sull'oggetto `Document`, fornendo il percorso di output e il formato desiderato (ad esempio, `SaveFormat.Pdf`). `SaveFormat` è un'enumerazione che specifica il tipo di file di output, come PDF. L'operazione scrive un nuovo file contenente solo le pagine selezionate.

## Problemi comuni e soluzioni
- **Le pagine sono fuori di uno:** GroupDocs.Merger utilizza la numerazione delle pagine basata su 1. Assicurati che l'elenco inizi da 1, non da 0.  
- **File protetti da password:** Passa la password al costruttore `Merger` o utilizza l'oggetto `LoadOptions`. `LoadOptions` fornisce impostazioni che controllano come viene caricato un documento, ad esempio abilitando la cache in memoria.  
- **File di grandi dimensioni causano timeout:** Abilita lo streaming impostando `LoadOptions.UseMemoryCache = true` per mantenere basso l'uso della memoria.

## Domande frequenti

**Q: Posso estrarre pagine da un documento Word come PDF?**  
A: Sì – la stessa chiamata `Extract` funziona per DOCX, e puoi salvare il risultato direttamente come PDF usando `SaveFormat.Pdf`.

**Q: È possibile estrarre pagine non consecutive?**  
A: Assolutamente. Fornisci un elenco separato da virgole come `"2,4,7"` o un intervallo misto `"1-2,5,8-10"`.

**Q: La libreria supporta PDF crittografati?**  
A: Sì. Fornisci la password quando apri il documento; l'API lo decritterà automaticamente.

**Q: Come gestisce GroupDocs.Merger le immagini all'interno dei PDF?**  
A: Le immagini sono preservate esattamente come appaiono nelle pagine selezionate; non sono necessari passaggi di conversione aggiuntivi.

**Q: Quali versioni .NET sono ufficialmente supportate?**  
A: .NET Framework 4.6+, .NET Core 3.1+ e .NET 5/6/7 sono pienamente supportate.

## Tutorial disponibili

### [Estrai pagine specifiche da documenti con GroupDocs.Merger per .NET](./extract-pages-groupdocs-merger-net/)
Scopri come estrarre in modo efficiente pagine specifiche usando GroupDocs.Merger per .NET. Ideale per gestire Word, PDF e altro in ambienti professionali.

### [Come estrarre pagine specifiche da un documento usando GroupDocs.Merger per .NET in C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Scopri come estrarre pagine specifiche da documenti usando GroupDocs.Merger per .NET con questa guida completa. Semplifica le attività di gestione dei documenti senza sforzo.

## Risorse aggiuntive

- [Documentazione di GroupDocs.Merger per .net](https://docs.groupdocs.com/merger/net/)
- [Riferimento API di GroupDocs.Merger per .net](https://reference.groupdocs.com/merger/net/)
- [Download di GroupDocs.Merger per .net](https://releases.groupdocs.com/merger/net/)
- [Forum di GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Supporto gratuito](https://forum.groupdocs.com/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

---

**Ultimo aggiornamento:** 2026-08-31  
**Testato con:** GroupDocs.Merger 23.9 for .NET  
**Autore:** GroupDocs

## Tutorial correlati

- [Come unire pagine PDF specifiche con GroupDocs.Merger per .NET: Guida completa](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Come unire pagine specifiche da più documenti usando GroupDocs.Merger per .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Ruota pagine PDF in .NET usando GroupDocs.Merger: Guida passo‑passo](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)