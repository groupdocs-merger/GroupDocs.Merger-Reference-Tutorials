---
date: 2026-09-11
description: Scopri come importare PDF in Word e altri formati utilizzando GroupDocs.Merger
  per .NET, includendo l'incorporamento di PDF in Word e l'aggiunta di allegati PDF
  in pochi semplici passaggi.
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: Scopri come importare PDF in Word e altri formati utilizzando GroupDocs.Merger
  per .NET, coprendo l'incorporamento di PDF in Word, l'aggiunta di allegati PDF e
  l'incorporamento OLE.
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: Come importare PDF in Word con GroupDocs.Merger per .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: Come importare PDF in Word con GroupDocs.Merger per .NET
type: docs
url: /it/net/document-import/
weight: 10
---

# Come importare PDF in Word con GroupDocs.Merger per .NET

In questa guida scoprirai come **importare PDF in Word** e altri tipi di documento usando GroupDocs.Merger per .NET. Che tu debba incorporare un PDF all'interno di un file Word, allegare PDF a documenti esistenti, o spostare contenuti tra diagrammi, presentazioni, fogli di calcolo e file di elaborazione testi, questo tutorial ti accompagna attraverso gli scenari più comuni, spiega perché sono importanti e ti mostra i passaggi esatti per completare il lavoro rapidamente.

## Risposte rapide
- **Posso importare un PDF in un documento Word?** Sì – GroupDocs.Merger consente di incorporare un PDF come oggetto OLE o come contenuto nativo in un file .docx.  
- **Ho bisogno di una libreria PDF separata?** No, l'SDK Merger gestisce l'importazione di PDF senza dipendenze aggiuntive.  
- **Quali versioni di .NET sono supportate?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza commerciale per la produzione; è disponibile una prova gratuita per la valutazione.  
- **Qual è la dimensione massima di un PDF che posso importare?** Sono supportati PDF fino a 500 MB per file senza caricare l'intero documento in memoria.

## Cos'è l'importazione di PDF in Word?
Importare PDF in Word significa prendere il contenuto di un file PDF e inserirlo all'interno di un documento Microsoft Word (.docx), sia come oggetto incorporato sia come elementi nativi convertiti, preservando layout, immagini e formattazione del testo. Il processo può mantenere il flusso del testo, le immagini, le tabelle e la grafica vettoriale, garantendo che il file Word risultante sia il più simile possibile al layout originale del PDF.

## Perché usare GroupDocs.Merger per questo compito?
GroupDocs.Merger supporta **oltre 30 formati di input e output** e può elaborare documenti fino a **500 MB** senza caricarli completamente in RAM, riducendo la pressione sulla memoria nelle applicazioni server‑side. La libreria fornisce anche **incorporamento OLE integrato**, consentendo di allegare PDF direttamente a file Word, Excel o PowerPoint con una singola chiamata API.

## Prerequisiti
- Ambiente di sviluppo .NET (Visual Studio 2022 o successivo).  
- Pacchetto NuGet GroupDocs.Merger per .NET installato (`Install-Package GroupDocs.Merger`).  
- Una licenza valida di GroupDocs.Merger per l'uso in produzione (è disponibile una licenza temporanea per i test).

## Come importare PDF in Word passo dopo passo

### Come incorporare un file PDF in un documento Word?
`Merger` è la classe principale dell'SDK GroupDocs.Merger che fornisce metodi di manipolazione dei documenti.  
`Insert` inserisce un documento o oggetto sorgente in un documento di destinazione in una posizione specificata.  

Carica il PDF sorgente con `Merger` e chiama `Insert` per posizionarlo all'interno del `.docx` di destinazione. L'operazione viene eseguita in due righe di codice e gestisce automaticamente il packaging OLE, così il PDF appare come un oggetto interattivo all'interno di Word.

### Come aggiungere allegati PDF a un file Word esistente?
`AddAttachment` allega un file esterno a un documento contenitore, memorizzandolo all'interno del pacchetto per un successivo recupero.  

Crea un'istanza di `Merger`, apri il documento Word e utilizza il metodo `AddAttachment` per allegare il PDF. L'allegato viene memorizzato all'interno del pacchetto Word e può essere aperto direttamente dalla finestra di dialogo “Insert > Object” del documento.

### Come incorporare oggetti OLE (come PDF) nei fogli di calcolo Excel?
`InsertOleObject` incorpora un oggetto OLE, come un PDF, in una cella del foglio di calcolo, consentendo l'apertura interattiva da Excel.  

Utilizza il metodo `InsertOleObject` su una cartella di lavoro Excel. Il metodo accetta il percorso del file PDF e la posizione della cella, inserendo il PDF come oggetto OLE che può essere aperto con un doppio clic.

## Problemi comuni e soluzioni
- **Il PDF appare solo come icona:** Assicurati che il file Word di destinazione sia salvato con estensione `.docx`; i file `.doc` più vecchi non supportano oggetti OLE incorporati.  
- **I PDF di grandi dimensioni causano importazioni lente:** Chiama `MergerSettings.EnableMemoryOptimization = true` prima dell'importazione per mantenere basso l'uso della memoria.  
- **Il PDF incorporato non è cliccabile:** Verifica che il file PDF non sia protetto da password; Merger non può incorporare PDF crittografati senza fornire la password.

## Domande frequenti

**Q: Posso importare solo pagine selezionate di un PDF in Word?**  
A: Sì – usa l'opzione `PageRange` quando chiami `Insert` per specificare quali pagine incorporare.

**Q: La libreria preserva i collegamenti ipertestuali all'interno del PDF quando viene importato?**  
A: Quando si incorpora come oggetto OLE, i collegamenti ipertestuali rimangono funzionali nel visualizzatore PDF; quando si converte in contenuto Word nativo, la maggior parte dei collegamenti ipertestuali viene mantenuta.

**Q: È possibile importare in batch più PDF in un unico documento Word?**  
A: Assolutamente. Scorri la tua collezione di PDF e chiama `Insert` per ogni file; la libreria li unisce in sequenza.

**Q: Cosa succede se il mio PDF contiene grafica vettoriale?**  
A: La grafica vettoriale viene preservata quando il PDF è incorporato come oggetto OLE; viene visualizzata nitida a qualsiasi livello di zoom.

**Q: GroupDocs.Merger funziona su container Linux?**  
A: Sì – la build .NET Standard funziona su Linux, macOS e Windows senza dipendenze native.

## Tutorial disponibili

### [Aggiungere allegati ai PDF usando GroupDocs.Merger per .NET&#58; Guida passo‑passo](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Scopri come aggiungere allegati ai PDF con GroupDocs.Merger per .NET. Questa guida passo‑passo copre l'installazione, l'implementazione e le applicazioni pratiche.

### [Incorporare PDF come OLE in PowerPoint usando GroupDocs.Merger per .NET&#58; Guida passo‑passo](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Scopri come incorporare senza problemi un file PDF come oggetto OLE nella tua presentazione PowerPoint con GroupDocs.Merger per .NET. Segui questa guida completa.

### [Incorporare PDF in Word usando GroupDocs.Merger per .NET&#58; Guida passo‑passo](./embed-pdf-word-groupdocs-merger-dotnet/)
Scopri come incorporare senza problemi un PDF in un documento Microsoft Word usando GroupDocs.Merger per .NET. Migliora i tuoi documenti con contenuti dinamici in modo efficiente.

### [Come incorporare oggetti OLE nei fogli di calcolo Excel usando GroupDocs.Merger per .NET](./embed-ole-objects-groupdocs-merger-net/)
Scopri come incorporare senza problemi oggetti OLE come PDF nei fogli di calcolo Excel usando GroupDocs.Merger per .NET, migliorando la presentazione dei dati e la funzionalità.

## Risorse aggiuntive

- [Documentazione di GroupDocs.Merger per .net](https://docs.groupdocs.com/merger/net/)
- [Riferimento API di GroupDocs.Merger per .net](https://reference.groupdocs.com/merger/net/)
- [Scarica GroupDocs.Merger per .net](https://releases.groupdocs.com/merger/net/)
- [Forum di GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Supporto gratuito](https://forum.groupdocs.com/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)

---

**Ultimo aggiornamento:** 2026-09-11  
**Testato con:** GroupDocs.Merger 23.12 per .NET  
**Autore:** GroupDocs

## Tutorial correlati

- [Incorporare PDF in Word usando GroupDocs.Merger per .NET: Guida passo‑passo](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Aggiungere allegati ai PDF usando GroupDocs.Merger per .NET: Guida passo‑passo](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [Caricare PDF da URL in .NET usando GroupDocs.Merger: Guida completa](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)