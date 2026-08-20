---
date: '2026-08-20'
description: Leer hoe je pdf's kunt samenvoegen met bladwijzers met GroupDocs.Merger
  for .NET, inclusief installatie, codevoorbeelden en best practices voor het combineren
  van PDF‑documenten.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Leer hoe je pdf's kunt samenvoegen met bladwijzers met GroupDocs.Merger
  for .NET. Volg stap‑voor‑stap code om PDF‑documenten te combineren terwijl de navigatie
  behouden blijft.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Hoe pdf's samenvoegen met bladwijzers met GroupDocs.Merger for .NET
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
title: Hoe pdf's samenvoegen met bladwijzers met GroupDocs.Merger for .NET
type: docs
url: /nl/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Hoe PDF's samenvoegen met bladwijzers met GroupDocs.Merger voor .NET

Het samenvoegen van meerdere PDF‑bestanden terwijl hun oorspronkelijke bladwijzers behouden blijven, kan je uren handmatige herorganisatie besparen. In deze tutorial leer je hoe je **PDF's samenvoegt met bladwijzers** met GroupDocs.Merger voor .NET, van projectconfiguratie tot een compleet, productie‑klaar code‑voorbeeld.

## Snelle antwoorden
- **Welke bibliotheek ondersteunt merges die bladwijzers behouden?** GroupDocs.Merger voor .NET.  
- **Kan ik meer dan twee PDF's tegelijk samenvoegen?** Ja – voeg zoveel bronbestanden toe als je nodig hebt.  
- **Heb ik een licentie nodig voor ontwikkeling?** Een gratis proefversie werkt voor testen; een permanente licentie is vereist voor productie.  
- **Wordt .NET Core ondersteund?** Absoluut – de bibliotheek werkt met .NET Core, .NET 5/6 en het volledige .NET Framework.  
- **Wat is de maximale bestandsgrootte die het aankan?** Tot 2 GB per document, verwerkt zonder het volledige bestand in het geheugen te laden.

## Wat is PDF's samenvoegen met bladwijzers?
**PDF's samenvoegen met bladwijzers** betekent dat je meerdere PDF‑documenten neemt en combineert tot één bestand, terwijl de bladwijzerhiërarchie van elk bronbestand behouden blijft. Het resulterende PDF behoudt de oorspronkelijke navigatiestructuur, waardoor lezers direct kunnen springen naar de secties die uit elk individueel bestand komen, wat essentieel is voor grote rapporten of samengestelde handleidingen.

## Waarom PDF's samenvoegen met bladwijzers?
Het behouden van bladwijzers bij het samenvoegen van PDF's verbetert de navigatie in geconsolideerde documenten, waardoor gebruikers snel specifieke hoofdstukken of secties kunnen vinden zonder door het hele bestand te scrollen. GroupDocs.Merger behoudt de oorspronkelijke outline‑hiërarchie, vermindert handmatige herorganisatie‑inspanning, en ondersteunt grote bestanden tot 2 GB met minimaal geheugenverbruik, waardoor het ideaal is voor workflows op ondernemingsniveau.

## Vereisten
- **.NET Core SDK** (3.1 of later) of **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** of een IDE die .NET‑ontwikkeling ondersteunt.  
- Basiskennis van C# en vertrouwdheid met bestands‑I/O.  

## GroupDocs.Merger voor .NET instellen

### Installatie
Voeg de bibliotheek toe aan je project met een van de volgende commando's:

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
- Zoek naar “GroupDocs.Merger” en installeer de nieuwste versie.

### Licentie verkrijgen
- **Gratis proefversie:** Download van de [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) pagina.  
- **Tijdelijke licentie:** Verkrijg er een via de [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Volledige licentie:** Aankoop op de [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).  

### Basisinitialisatie
De `Merger`‑klasse is het toegangspunt voor alle samenvoeg‑operaties.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Deze namespace geeft je toegang tot de volledige set PDF‑bewerkingsfuncties.

## Hoe PDF's samenvoegen met bladwijzers in .NET

Laad je primaire PDF, configureer de bladwijzerafhandeling, voeg extra bestanden toe, en sla het resultaat op – allemaal in een paar beknopte code‑regels.

**Direct antwoord (40‑70 woorden):**  
Maak een `Merger`‑instantie met de eerste PDF, schakel `PdfJoinOptions.UseBookmarks` in, voeg elke volgende PDF toe via `Join`, en roep `Save` aan om het gecombineerde bestand te schrijven. Deze aanpak behoudt elke oorspronkelijke bladwijzerhiërarchie en wordt in één doorloop uitgevoerd, waardoor het geheugenverbruik tot een minimum wordt beperkt.

### Stap 1: map paden definiëren
Stel bron- en uitvoermappen in zodat de code de PDF's die je wilt samenvoegen kan vinden.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Stap 2: laad de primaire PDF
`Merger` vertegenwoordigt het hoofd‑document waaraan je andere zult toevoegen.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Stap 3: configureer bladwijzer‑behoudopties
`PdfJoinOptions` bepaalt hoe de samenvoeging zich gedraagt; de `UseBookmarks`‑vlag vertelt de engine om bestaande bladwijzers te behouden.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Stap 4: voeg extra PDF's toe
Roep `Join` aan voor elk extra bestand. De bibliotheek voegt automatisch hun bladwijzer‑bomen samen onder de outline van het hoofd‑document.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Stap 5: sla de samengevoegde PDF op
Geef het uitvoerpad en -formaat op; de bibliotheek schrijft één PDF die alle bladwijzer‑items behoudt.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Veelvoorkomende problemen en oplossingen
- **Ontbrekende bladwijzers:** Controleer `UseBookmarks = true` in `PdfJoinOptions`.  
- **Pad‑fouten:** Gebruik `Path.Combine` en controleer de bestands‑existentie vóór het samenvoegen.  
- **Grote bestanden veroorzaken geheugenpieken:** Verwerk PDF's opeenvolgend en maak het `Merger`‑object vrij na elke opslaan.

## Praktische toepassingen
1. **Financiële rapporten consolideren** – houd kwartaal‑secties direct bereikbaar via bladwijzers.  
2. **Cursusmateriaalpakketten** – voeg college‑PDF's samen terwijl je hoofdstuk‑navigatie voor studenten behoudt.  
3. **Projectdocumentatiebundels** – combineer ontwerpspecificaties, testplannen en release‑notities tot één doorzoekbaar bestand.

## Prestatieoverwegingen
- Verwerk één bestand tegelijk bij het samenvoegen van meer dan 20 PDF's om het RAM‑gebruik laag te houden.  
- Gebruik de nieuwste .NET‑runtime (bijv. .NET 6) voor optimale JIT‑compilatie en garbage‑collection efficiëntie.  
- Voor PDF's groter dan 500 MB, schakel streaming‑modus in via `MergerSettings` om te voorkomen dat het hele document in het geheugen wordt geladen.

## Veelgestelde vragen

**Q: Wat is GroupDocs.Merger?**  
A: GroupDocs.Merger is een .NET‑bibliotheek die je in staat stelt PDF's en andere documentformaten programmatically te samenvoegen, splitsen, roteren en anderszins te manipuleren.

**Q: Kan ik meer dan twee PDF‑bestanden tegelijk samenvoegen?**  
A: Ja – roep `Join` herhaaldelijk aan of geef een collectie van bestandspaden door om een willekeurig aantal PDF's in één bewerking samen te voegen.

**Q: Hoe regel ik licenties voor productiegebruik?**  
A: Verkrijg een permanente licentie via de GroupDocs‑aankooppagina; de proeflicentie werkt alleen voor evaluatie en verloopt na 30 dagen.

**Q: Mijn samengevoegde PDF toont geen bladwijzers—wat ging er mis?**  
A: Zorg ervoor dat `PdfJoinOptions.UseBookmarks` is ingesteld op `true` en dat elk bron‑PDF daadwerkelijk bladwijzers bevat vóór het samenvoegen.

**Q: Is de bibliotheek compatibel met .NET Core en .NET Framework?**  
A: Absoluut – het ondersteunt .NET Core 3.1+, .NET 5/6, en het volledige .NET Framework 4.6.1+.

## Bronnen
- [Documentatie](https://docs.groupdocs.com/merger/net/)  
- [API‑referentie](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Licentie kopen](https://purchase.groupdocs.com/buy)  
- [Gratis proefversie](https://releases.groupdocs.com/merger/net/)  
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)  
- [Supportforum](https://forum.groupdocs.com/c/merger/)  

---

**Laatst bijgewerkt:** 2026-08-20  
**Getest met:** GroupDocs.Merger 23.11 for .NET  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Hoe specifieke PDF‑pagina's samenvoegen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Hoe documenten eenvoudig samenvoegen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Bijlagen toevoegen aan PDF's met GroupDocs.Merger voor .NET: Een stapsgewijze gids](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)