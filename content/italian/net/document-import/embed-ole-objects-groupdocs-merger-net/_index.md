---
date: '2026-09-21'
description: Scopri come incorporare PDF nei fogli di calcolo Excel con GroupDocs.Merger
  per .NET, migliorando la presentazione dei dati e la funzionalità.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Scopri come incorporare PDF in Excel con GroupDocs.Merger per .NET.
  Segui le istruzioni passo‑passo, consulta le risposte rapide e evita gli errori
  più comuni.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Come incorporare PDF in Excel usando GroupDocs.Merger per .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: Come incorporare PDF in Excel usando GroupDocs.Merger per .NET
type: docs
url: /it/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Come incorporare PDF in Excel usando GroupDocs.Merger per .NET

## Introduzione

Incorporare PDF in Excel ti consente di mantenere i documenti di supporto — come contratti, report o specifiche — proprio dove vivono i dati. Con **GroupDocs.Merger for .NET**, puoi aggiungere oggetti OLE alle celle in poche righe di codice, trasformando un semplice foglio di calcolo in una cartella di lavoro interattiva e autonoma. Questo tutorial ti guida attraverso tutto ciò che devi sapere, dall'installazione alla risoluzione dei problemi.

**Cosa imparerai**

- Come configurare GroupDocs.Merger per .NET in un progetto C#  
- I passaggi esatti per incorporare un PDF (o qualsiasi file compatibile OLE) in una cella di Excel  
- Opzioni di configurazione, consigli sulle prestazioni e problemi comuni  

Confermiamo di avere tutto pronto prima di iniziare.

## Risposte rapide
- **Posso incorporare qualsiasi tipo di file?** Sì — qualsiasi formato supportato come oggetto OLE (PDF, Word, immagine, ecc.).  
- **Ho bisogno di una licenza per lo sviluppo?** Una prova gratuita funziona per i test; è necessaria una licenza permanente per la produzione.  
- **Quali versioni .NET sono supportate?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **Il file Excel aumenterà di dimensioni in modo significativo?** Solo della dimensione del documento incorporato; mantieni i file sotto qualche MB per le migliori prestazioni.  
- **Esiste un limite al numero di oggetti OLE?** Praticamente nessuno, ma cartelle di lavoro molto grandi possono influire sui tempi di caricamento.

## Cos'è l'incorporamento di PDF in Excel?

Incorporare PDF in Excel inserisce l'intero PDF come oggetto OLE che può essere aperto direttamente dal foglio di calcolo. Gli utenti cliccano sull'icona e visualizzano il documento originale senza uscire da Excel. Questo approccio preserva il layout originale, consente un rapido riferimento e elimina la necessità di gestire file separati. Il PDF incorporato si comporta come qualsiasi altro oggetto OLE, permettendo agli utenti di fare doppio clic sull'icona per avviare il visualizzatore PDF rimanendo nell'ambiente Excel.

## Perché incorporare oggetti OLE in Excel?

GroupDocs.Merger supporta **120+ formati di input e output** e può incorporare oggetti senza caricare l'intero file in memoria, consentendo una rapida elaborazione di PDF di centinaia di pagine. Questo riduce la necessità di repository di file separati e mantiene i dati correlati insieme. Semplifica anche il controllo delle versioni e garantisce che tutta la documentazione pertinente viaggi con la cartella di lavoro, migliorando la collaborazione tra i team.

## Prerequisiti

- **GroupDocs.Merger for .NET** (ultimo pacchetto NuGet)  
- **.NET Framework** 4.5+ **o** **.NET Core/5+/6+**  
- Visual Studio 2022 o successivo  
- Conoscenza di base di C# e familiarità con I/O di file  

## Configurazione di GroupDocs.Merger per .NET

### Installazione

Aggiungi il pacchetto usando uno dei seguenti metodi:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Cerca “GroupDocs.Merger” e installa l'ultima versione.

### Acquisizione della licenza

1. **Prova gratuita** – testare la libreria senza costi.  
2. **Licenza temporanea** – richiedi una licenza temporanea nella [temporary‑license page](https://purchase.groupdocs.com/temporary-license/).  
3. **Acquisto** – considera l'acquisto di una licenza nella [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

### Inizializzazione di base

`Merger` è il punto di ingresso per tutte le operazioni.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Come incorporare oggetti OLE in Excel?

Carica la cartella di lavoro di origine, configura le opzioni OLE e lascia che `Merger` inserisca l'oggetto. Le sezioni seguenti ti forniscono un flusso di lavoro conciso, pronto all'uso.

### Panoramica della funzionalità
Incorporare oggetti OLE ti consente di memorizzare un PDF completo all'interno di una cella, preservando il layout originale e consentendo l'accesso con un solo clic da Excel.

### Implementazione passo‑passo

#### 1. Impostare percorsi e numero di pagina
Specifica il foglio di calcolo, il file da incorporare e l'indirizzo della cella di destinazione.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Configurare OleSpreadsheetOptions
`OleSpreadsheetOptions` definisce dove l'oggetto OLE sarà posizionato nel foglio di lavoro e come appare la sua icona.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Inizializzare Merger ed eseguire l'incorporamento
La classe `Merger` gestisce l'inserimento effettivo. Dopo la chiamata, la cartella di lavoro contiene l'icona OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Suggerimenti comuni per la risoluzione dei problemi
- Verifica che tutti i percorsi dei file siano assoluti o correttamente risolti rispetto all'eseguibile.  
- Assicurati che il numero di pagina specificato esista nel PDF di origine; altrimenti viene sollevata un'eccezione.  
- Se l'oggetto incorporato non viene visualizzato, conferma che la versione di Excel di destinazione supporti OLE (la maggior parte delle versioni moderne lo fa).

## Applicazioni pratiche

Incorporare PDF in Excel è utile per:

1. **Report finanziari** – allegare dichiarazioni verificate direttamente accanto alle tabelle riassuntive.  
2. **Documentazione di progetto** – mantenere specifiche di design, analisi dei rischi o contratti all'interno di un tracker principale.  
3. **Dashboard di formazione** – incorporare manuali utente o PDF di policy per un rapido riferimento da parte del personale.

## Considerazioni sulle prestazioni

- **Dimensione del file** – mantieni i PDF incorporati sotto 5 MB per evitare di gonfiare la cartella di lavoro.  
- **Utilizzo della memoria** – `GroupDocs.Merger` trasmette i dati, quindi il consumo di memoria rimane basso anche con file di origine di grandi dimensioni.  
- **Rilascio degli oggetti** – chiama sempre `Dispose()` sulle istanze di `Merger` per rilasciare rapidamente i handle dei file.

## Domande frequenti

**D: Cos'è un oggetto OLE?**  
R: Un oggetto OLE (Object Linking and Embedding) memorizza un altro file (PDF, Word, immagine, ecc.) all'interno di un documento host, consentendo la modifica in loco o l'apertura.

**D: Posso incorporare oggetti OLE in altri formati Office?**  
R: Sì — GroupDocs.Merger supporta anche file Word, PowerPoint e Visio.

**D: Come gestisco PDF protetti da password?**  
R: Fornisci la password quando crei l'istanza `OleSpreadsheetOptions`; la libreria decritterà automaticamente il file.

**D: Esiste un limite di dimensione per i PDF incorporati?**  
R: Tecnically non c'è un limite rigido, ma file superiori a 10 MB possono aumentare notevolmente i tempi di caricamento della cartella di lavoro.

**D: Dove posso trovare altri esempi?**  
R: Visita la documentazione ufficiale su [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) per ulteriori esempi di codice e riferimenti API.

## Risorse aggiuntive
- **Documentazione**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **Riferimento API**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Download**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Acquisto licenza**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Prova gratuita**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Licenza temporanea**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Forum di supporto**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Ultimo aggiornamento:** 2026-09-21  
**Testato con:** GroupDocs.Merger 23.12 per .NET  
**Autore:** GroupDocs

## Tutorial correlati

- [Incorpora PDF come OLE in PowerPoint usando GroupDocs.Merger per .NET: Guida passo‑passo](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Incorpora PDF in Word usando GroupDocs.Merger per .NET: Guida passo‑passo](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Caricamento PDF da URL in .NET usando GroupDocs.Merger: Guida completa](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)