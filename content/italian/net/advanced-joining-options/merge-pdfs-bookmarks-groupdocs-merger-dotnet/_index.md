---
date: '2026-08-20'
description: Scopri come unire i pdf con i segnalibri usando GroupDocs.Merger for
  .NET, includendo la configurazione, code examples e best practices per combinare
  PDF documents.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Scopri come unire i pdf con i segnalibri usando GroupDocs.Merger for
  .NET. Segui step‑by‑step code per combinare PDF documents mantenendo la navigazione.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Come unire i pdf con i segnalibri usando GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Come unire i pdf con i segnalibri usando GroupDocs.Merger for .NET
type: docs
url: /it/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Come unire PDF con segnalibri usando GroupDocs.Merger per .NET

Unire diversi file PDF mantenendo intatti i loro segnalibri originali può farti risparmiare ore di riorganizzazione manuale. In questo tutorial imparerai come **unire PDF con segnalibri** usando GroupDocs.Merger per .NET, dalla configurazione del progetto a un esempio di codice completo e pronto per la produzione.

## Risposte rapide
- **Quale libreria supporta le unioni che preservano i segnalibri?** GroupDocs.Merger per .NET.  
- **Posso unire più di due PDF contemporaneamente?** Sì – aggiungi tutti i file sorgente di cui hai bisogno.  
- **È necessaria una licenza per lo sviluppo?** Una prova gratuita è sufficiente per i test; è richiesta una licenza permanente per la produzione.  
- **È supportato .NET Core?** Assolutamente – la libreria funziona con .NET Core, .NET 5/6 e il framework .NET completo.  
- **Qual è la dimensione massima del file che può gestire?** Fino a 2 GB per documento, elaborato senza caricare l'intero file in memoria.

## Cos'è l'unione di PDF con segnalibri?
**Unire PDF con segnalibri** significa prendere diversi documenti PDF e combinarli in un unico file mantenendo intatta la gerarchia dei segnalibri di ciascun documento sorgente. Il PDF risultante conserva la struttura di navigazione originale, consentendo ai lettori di saltare direttamente alle sezioni che provengono da ciascun file individuale, cosa essenziale per report voluminosi o manuali compilati.

## Perché unire PDF con segnalibri?
Mantenere i segnalibri durante l'unione di PDF migliora la navigazione nei documenti consolidati, consentendo agli utenti di individuare rapidamente capitoli o sezioni specifiche senza scorrere l'intero file. GroupDocs.Merger conserva la gerarchia originale del sommario, riduce lo sforzo di riorganizzazione manuale e supporta file di grandi dimensioni fino a 2 GB utilizzando poca memoria, rendendolo ideale per flussi di lavoro su scala aziendale.

## Prerequisiti
- **.NET Core SDK** (3.1 o successivo) o **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** o qualsiasi IDE che supporti lo sviluppo .NET.  
- Conoscenze di base di C# e familiarità con la gestione dei file I/O.  

## Configurare GroupDocs.Merger per .NET

### Installazione
Aggiungi la libreria al tuo progetto con uno dei seguenti comandi:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Cerca “GroupDocs.Merger” e installa l'ultima versione.

### Acquisizione della licenza
- **Prova gratuita:** Scarica dalla pagina [Rilasci GroupDocs](https://releases.groupdocs.com/merger/net/).  
- **Licenza temporanea:** Ottienila tramite la [Pagina Licenza Temporanea GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **Licenza completa:** Acquista nella [Pagina di Acquisto GroupDocs](https://purchase.groupdocs.com/buy).

### Inizializzazione di base
La classe `Merger` è il punto di ingresso per tutte le operazioni di unione.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Questo namespace ti dà accesso all'intero set di funzionalità di manipolazione PDF.

## Come unire PDF con segnalibri in .NET

Carica il tuo PDF principale, configura la gestione dei segnalibri, aggiungi file aggiuntivi e salva il risultato – il tutto in poche righe di codice concise.

**Risposta diretta (40‑70 parole):**  
Crea un'istanza `Merger` con il primo PDF, abilita `PdfJoinOptions.UseBookmarks`, aggiungi ciascun PDF successivo tramite `Join` e chiama `Save` per scrivere il file combinato. Questo approccio preserva ogni gerarchia di segnalibri originale e viene eseguito in un unico passaggio, riducendo al minimo il consumo di memoria.

### Passo 1: definire i percorsi delle directory
Configura le cartelle di origine e di destinazione in modo che il codice possa individuare i PDF da unire.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Passo 2: caricare il PDF principale
`Merger` rappresenta il documento principale a cui aggiungerai gli altri.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Passo 3: configurare le opzioni di preservazione dei segnalibri
`PdfJoinOptions` controlla il comportamento dell'unione; il flag `UseBookmarks` indica al motore di mantenere i segnalibri esistenti.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Passo 4: aggiungere PDF aggiuntivi
Chiama `Join` per ogni file aggiuntivo. La libreria unisce automaticamente i loro alberi di segnalibri sotto il sommario del documento principale.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Passo 5: salvare il PDF unito
Specifica il percorso di output e il formato; la libreria scrive un unico PDF che conserva tutte le voci dei segnalibri.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Problemi comuni e soluzioni
- **Segnalibri mancanti:** Verifica che `UseBookmarks = true` in `PdfJoinOptions`.  
- **Errori di percorso:** Usa `Path.Combine` e verifica l'esistenza dei file prima dell'unione.  
- **File di grandi dimensioni causano picchi di memoria:** Processa i PDF in sequenza e rilascia l'oggetto `Merger` dopo ogni salvataggio.

## Applicazioni pratiche
1. **Consolidare i report finanziari** – mantieni le sezioni trimestrali immediatamente raggiungibili tramite segnalibri.  
2. **Pacchetti di materiale didattico** – unisci i PDF delle lezioni mantenendo la navigazione dei capitoli per gli studenti.  
3. **Raccolte di documentazione di progetto** – combina specifiche di design, piani di test e note di rilascio in un unico file ricercabile.

## Considerazioni sulle prestazioni
- Processa un file alla volta quando unisci più di 20 PDF per mantenere basso l'uso della RAM.  
- Usa l'ultima runtime .NET (ad esempio .NET 6) per una compilazione JIT ottimale e un'efficienza della garbage‑collection.  
- Per PDF più grandi di 500 MB, abilita la modalità streaming tramite `MergerSettings` per evitare di caricare l'intero documento in memoria.

## Domande frequenti

**D: Cos'è GroupDocs.Merger?**  
R: GroupDocs.Merger è una libreria .NET che consente di unire, dividere, ruotare e manipolare programmaticamente PDF e altri formati di documento.

**D: Posso unire più di due file PDF alla volta?**  
R: Sì – chiama `Join` ripetutamente o passa una collezione di percorsi file per unire qualsiasi numero di PDF in un'unica operazione.

**D: Come gestisco la licenza per l'uso in produzione?**  
R: Ottieni una licenza permanente dalla pagina di acquisto GroupDocs; la licenza di prova funziona solo per la valutazione e scade dopo 30 giorni.

**D: Il mio PDF unito non mostra segnalibri—cosa è andato storto?**  
R: Assicurati che `PdfJoinOptions.UseBookmarks` sia impostato su `true` e che ogni PDF sorgente contenga effettivamente segnalibri prima dell'unione.

**D: La libreria è compatibile con .NET Core e .NET Framework?**  
R: Assolutamente – supporta .NET Core 3.1+, .NET 5/6 e il framework .NET completo 4.6.1+.

## Risorse
- [Documentazione](https://docs.groupdocs.com/merger/net/)  
- [Riferimento API](https://reference.groupdocs.com/merger/net/)  
- [Scarica GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Acquista Licenza](https://purchase.groupdocs.com/buy)  
- [Versione di Prova Gratuita](https://releases.groupdocs.com/merger/net/)  
- [Licenza Temporanea](https://purchase.groupdocs.com/temporary-license/)  
- [Forum di Supporto](https://forum.groupdocs.com/c/merger/)  

---

**Ultimo aggiornamento:** 2026-08-20  
**Testato con:** GroupDocs.Merger 23.11 per .NET  
**Autore:** GroupDocs

## Tutorial correlati

- [Come unire pagine PDF specifiche con GroupDocs.Merger per .NET: Guida completa](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Come unire facilmente documenti usando GroupDocs.Merger per .NET: Guida completa](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Aggiungere allegati ai PDF usando GroupDocs.Merger per .NET: Guida passo passo](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)