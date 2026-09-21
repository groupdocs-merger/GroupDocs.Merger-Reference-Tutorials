---
date: '2026-09-21'
description: Scopri come incorporare PDF in PowerPoint come oggetto OLE con GroupDocs.Merger
  per .NET. Questa guida passo‑passo ti mostra le chiamate API esatte e le migliori
  pratiche.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: incorpora PDF in PowerPoint usando GroupDocs.Merger per .NET. Segui
  questo tutorial conciso per aggiungere oggetti OLE, configurare le opzioni e evitare
  le insidie più comuni.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: incorpora PDF in PowerPoint – incorpora PDF come OLE con GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: Come incorporare PDF in PowerPoint come OLE usando GroupDocs.Merger per .NET
type: docs
url: /it/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# Incorporare pdf in PowerPoint come OLE usando GroupDocs.Merger per .NET

Incorporare un PDF direttamente in una diapositiva PowerPoint ti consente di mantenere intatto il documento originale offrendo al pubblico un accesso immediato. In questo tutorial imparerai **come incorporare pdf in powerpoint** come oggetto OLE con GroupDocs.Merger per .NET, vedrai le opzioni API necessarie e scoprirai consigli per prestazioni affidabili.

## Risposte rapide
- **Quale libreria gestisce l'incorporamento OLE?** GroupDocs.Merger per .NET fornisce la classe `OlePresentationOptions` per questo scopo.  
- **È necessaria una licenza?** Una licenza di prova funziona per lo sviluppo; è necessaria una licenza completa per l'uso in produzione.  
- **Posso incorporare più di un PDF?** Sì – ripeti il passaggio di importazione per ogni diapositiva di destinazione.  
- **Quali versioni di .NET sono supportate?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Il processo è efficiente in termini di memoria?** L'API trasmette i file in streaming, quindi anche PDF di centinaia di pagine possono essere incorporati senza caricare l'intero file in memoria.

## Che cosa significa incorporare pdf in powerpoint?
**embed pdf in powerpoint** significa inserire un file PDF come oggetto OLE (Object Linking and Embedding) in modo che la diapositiva mostri un'icona o un'anteprima che, al doppio clic, apre il PDF originale nel visualizzatore predefinito. Questo approccio preserva la formattazione, i collegamenti ipertestuali e le impostazioni di sicurezza del documento sorgente.

## Perché usare l'incorporamento OLE invece di convertire il PDF?
L'incorporamento mantiene intatti la dimensione e il layout originali del file, elimina gli errori di conversione e consente di aggiornare il PDF sorgente senza riesportare la presentazione. GroupDocs.Merger supporta **oltre 50 formati di input e output** e può incorporare PDF fino a diverse centinaia di megabyte trasmettendo i dati per mantenere l'uso della memoria inferiore a 100 MB.

## Prerequisiti
- Visual Studio 2022 (o qualsiasi IDE compatibile con .NET)  
- Runtime .NET Framework 4.5+ o .NET Core 3.1+  
- Una licenza valida di GroupDocs.Merger per .NET (di prova o commerciale)  
- Un file PowerPoint (.pptx) e il PDF che desideri incorporare  

## Configurare GroupDocs.Merger per .NET

### Come installo la libreria?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – cerca “GroupDocs.Merger” e fai clic su **Install** per ottenere l'ultima versione.

### Come ottengo una licenza?
- **Prova gratuita** – registrati sul sito GroupDocs per ottenere una chiave di licenza temporanea.  
- **Licenza temporanea** – richiedi una prova estesa se hai bisogno di più di 30 giorni.  
- **Acquisto completo** – acquista una licenza commerciale per uso illimitato in produzione.

### Come inizializzo l'API?
`Merger` è la classe principale che fornisce operazioni di manipolazione dei documenti come import, merge e conversione.  
Aggiungi le direttive `using` richieste all'inizio del tuo file C# e crea un'istanza `Merger` con il percorso del file di licenza:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Guida all'implementazione

### Come incorporare pdf in powerpoint come OLE?
Carica la tua presentazione, configura le opzioni OLE e chiama il metodo di importazione – l'intera operazione si completa in tre passaggi logici.

**Passo 1 – definire le posizioni dei file**  
Specifica i percorsi assoluti o relativi per il PDF sorgente, il file PowerPoint di destinazione e la cartella in cui verrà salvata la presentazione modificata.

**Passo 2 – configurare le opzioni OLE**  
`OlePresentationOptions` è la classe che indica a GroupDocs.Merger quale file incorporare, su quale diapositiva e a quali coordinate. Consente inoltre di impostare larghezza, altezza e modalità di visualizzazione dell'oggetto incorporato.

**Passo 3 – importare il PDF**  
`ImportDocument` è la chiamata API di Merger che inserisce l'oggetto OLE nel file PowerPoint usando le opzioni fornite. Il metodo trasmette il PDF nella diapositiva senza caricare l'intero documento in memoria.

#### Ancore di definizione
- `OlePresentationOptions` è il contenitore delle opzioni che definisce il file incorporato, la sua posizione (X/Y), dimensione e numero della diapositiva di destinazione.  
- `ImportDocument` è la chiamata API di Merger che inserisce l'oggetto OLE nel file PowerPoint usando le opzioni fornite.

## Parametri di configurazione comuni
- **SlideNumber** – l'indice basato su 1 della diapositiva che ospiterà l'oggetto OLE.  
- **XCoordinate / YCoordinate** – posizione misurata in punti dall'angolo in alto a sinistra della diapositiva.  
- **Width / Height** – dimensioni del segnaposto OLE; impostare a 0 per usare la dimensione predefinita.  
- **ObjectName** – nome amichevole opzionale mostrato quando l'oggetto è selezionato in PowerPoint.

## Applicazioni pratiche
Incorporare un PDF come oggetto OLE è utile in molti scenari reali:

1. **Briefing aziendali** – allega l'ultimo rapporto finanziario senza aumentare le dimensioni della presentazione.  
2. **Lezioni accademiche** – fornisci articoli di ricerca completi insieme ai riassunti delle diapositive.  
3. **Aggiornamenti di stato del progetto** – incorpora un piano di progetto live che gli stakeholder possono aprire per i dettagli.  
4. **Presentazioni di vendita** – includi schede tecniche del prodotto che i rappresentanti possono aprire su richiesta.  
5. **Workshop tecnici** – presenta schemi o schede tecniche che gli ingegneri possono ispezionare immediatamente.

## Considerazioni sulle prestazioni
Per mantenere il processo di incorporamento veloce e a basso consumo di memoria:

- **Trasmettere i file** – GroupDocs.Merger legge e scrive in streaming, quindi anche un PDF di 200 pagine utilizza meno di 100 MB di RAM.  
- **Processo batch** – quando si aggiornano molte presentazioni, riutilizza una singola istanza `Merger` e chiudi rapidamente gli stream.  
- **Ridimensionare PDF di grandi dimensioni** – comprimi o riduci la risoluzione delle immagini nel PDF sorgente se noti tempi di caricamento lenti.

## Domande frequenti

**Q: Posso incorporare più PDF in una singola presentazione?**  
A: Sì. Chiama `ImportDocument` per ogni PDF, specificando un `SlideNumber` diverso o una posizione diversa sulla stessa diapositiva.

**Q: Quanto grande può essere un PDF da incorporare?**  
A: Il limite pratico è determinato dalla memoria del tuo server; sono stati testati incorporamenti fino a 500 MB senza problemi grazie allo streaming.

**Q: L'oggetto OLE conserva elementi interattivi come i collegamenti ipertestuali?**  
A: Assolutamente. Il PDF incorporato si apre nel visualizzatore predefinito, preservando tutti i collegamenti interni e i segnalibri.

**Q: E se il PDF è protetto da password?**  
A: Fornisci la password tramite la proprietà `Password` di `OlePresentationOptions` prima di chiamare `ImportDocument`.

**Q: L'oggetto incorporato funzionerà su tutte le versioni di PowerPoint?**  
A: Il formato OLE è supportato da PowerPoint 2007 e versioni successive, inclusi Office 365.

## Conclusione
Ora disponi di un flusso di lavoro completo e pronto per la produzione per **embed pdf in powerpoint** come oggetto OLE usando GroupDocs.Merger per .NET. Trasmettendo i file, configurando `OlePresentationOptions` e chiamando `ImportDocument`, puoi arricchire le presentazioni con PDF originali mantenendo basso l'uso della memoria e preservando tutte le funzionalità interattive. Esplora ulteriori capacità di Merger come l'unione di diapositive, la conversione di formati e il watermarking per automatizzare ulteriormente i tuoi flussi di documenti.

---

**Ultimo aggiornamento:** 2026-09-21  
**Testato con:** GroupDocs.Merger 23.12 per .NET  
**Autore:** GroupDocs  

## Risorse
- **Documentazione:** [Documentazione GroupDocs.Merger per .NET](https://docs.groupdocs.com/merger/net/)  
- **Riferimento API:** [Riferimento API GroupDocs.Merger](https://reference.groupdocs.com/merger/net/)  
- **Download:** [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- **Acquisto:** [Acquista licenza GroupDocs](https://purchase.groupdocs.com/buy)  
- **Prova gratuita:** [Prova gratuita GroupDocs](https://releases.groupdocs.com/merger/net/)  
- **Licenza temporanea:** [Ottieni una licenza temporanea](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## Tutorial correlati

- [Incorporare PDF in Word usando GroupDocs.Merger per .NET: Guida passo passo](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Caricare PDF da URL in .NET usando GroupDocs.Merger: Guida completa](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [Come recuperare le informazioni del documento usando GroupDocs.Merger per .NET: Guida completa](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)