---
date: '2026-09-21'
description: Leer hoe je pdf in PowerPoint als OLE‑object kunt insluiten met GroupDocs.Merger
  voor .NET. Deze stapsgewijze gids toont de exacte API‑aanroepen en best practices.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: pdf in PowerPoint insluiten met GroupDocs.Merger voor .NET. Volg deze
  beknopte tutorial om OLE‑objecten toe te voegen, opties te configureren en veelvoorkomende
  valkuilen te vermijden.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: pdf in PowerPoint insluiten – PDF als OLE insluiten met GroupDocs.Merger
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
title: Hoe pdf in PowerPoint in te sluiten als OLE met GroupDocs.Merger voor .NET
type: docs
url: /nl/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# PDF insluiten in PowerPoint als OLE met GroupDocs.Merger voor .NET

Een PDF direct in een PowerPoint‑dia insluiten laat je het originele document ongewijzigd houden terwijl je publiek directe toegang krijgt. In deze tutorial leer je **hoe je pdf in powerpoint kunt insluiten** als een OLE‑object met GroupDocs.Merger voor .NET, zie de vereiste API‑opties, en ontdek tips voor betrouwbare prestaties.

## Snelle antwoorden
- **Welke bibliotheek behandelt OLE‑insluiting?** GroupDocs.Merger voor .NET biedt de `OlePresentationOptions`‑klasse voor dit doel.  
- **Heb ik een licentie nodig?** Een proeflicentie werkt voor ontwikkeling; een volledige licentie is vereist voor productiegebruik.  
- **Kan ik meer dan één PDF insluiten?** Ja – herhaal de importstap voor elke dia die je wilt targeten.  
- **Welke .NET‑versies worden ondersteund?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Is het proces geheugen‑efficiënt?** De API streamt bestanden, zodat zelfs PDF’s van meerdere honderden pagina’s kunnen worden ingesloten zonder het volledige bestand in het geheugen te laden.

## Wat is pdf insluiten in powerpoint?
**embed pdf in powerpoint** betekent het invoegen van een PDF‑bestand als een OLE (Object Linking and Embedding)‑object zodat de dia een pictogram of voorbeeld toont dat, bij dubbelklikken, de originele PDF opent in de standaardviewer. Deze aanpak behoudt de opmaak, hyperlinks en beveiligingsinstellingen van het bron‑document.

## Waarom OLE‑insluiting gebruiken in plaats van de PDF te converteren?
Insluiten behoudt de oorspronkelijke bestandsgrootte en lay‑out, elimineert conversiefouten, en stelt je in staat de bron‑PDF bij te werken zonder de presentatie opnieuw te exporteren. GroupDocs.Merger ondersteunt **50+ invoer‑ en uitvoerformaten** en kan PDF‑s tot enkele honderden megabytes insluiten terwijl data gestreamd wordt om het geheugenverbruik onder 100 MB te houden.

## Vereisten
- Visual Studio 2022 (of een andere .NET‑compatibele IDE)  
- .NET Framework 4.5+ of .NET Core 3.1+ runtime  
- Een geldige GroupDocs.Merger voor .NET‑licentie (proef of commercieel)  
- Een PowerPoint‑bestand (.pptx) en de PDF die je wilt insluiten  

## GroupDocs.Merger voor .NET instellen

### Hoe installeer ik de bibliotheek?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – zoek naar “GroupDocs.Merger” en klik op **Install** om de nieuwste versie te krijgen.

### Hoe verkrijg ik een licentie?
- **Gratis proefversie** – meld je aan op de GroupDocs‑website voor een tijdelijke licentiesleutel.  
- **Tijdelijke licentie** – vraag een verlengde proefperiode aan als je meer dan 30 dagen nodig hebt.  
- **Volledige aankoop** – koop een commerciële licentie voor onbeperkt productiegebruik.

### Hoe initialiseert ik de API?
`Merger` is de primaire klasse die documentbewerkingsbewerkingen biedt zoals import, samenvoegen en conversie.  
Voeg de vereiste `using`‑directieven toe aan de bovenkant van je C#‑bestand en maak een `Merger`‑instantie aan met het pad naar het licentiebestand:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Implementatie‑gids

### Hoe pdf in powerpoint als OLE insluiten?
Laad je presentatie, configureer de OLE‑opties, en roep de import‑methode aan – de volledige bewerking voltooit zich in drie logische stappen.

**Stap 1 – bestandslocaties definiëren**  
Geef de absolute of relatieve paden op voor de bron‑PDF, het doel‑PowerPoint‑bestand, en de map waar de aangepaste presentatie wordt opgeslagen.

**Stap 2 – de OLE‑opties configureren**  
`OlePresentationOptions` is de klasse die GroupDocs.Merger vertelt welk bestand moet worden ingesloten, op welke dia, en op welke coördinaten. Het laat je ook de breedte, hoogte en weergavemodus van het ingesloten object instellen.

**Stap 3 – de PDF importeren**  
`ImportDocument` is de Merger‑API‑aanroep die het OLE‑object in het PowerPoint‑bestand invoegt met behulp van de opgegeven opties. De methode streamt de PDF naar de dia zonder het volledige document in het geheugen te laden.

#### Definitie‑ankers
- `OlePresentationOptions` is de opti​econtainer die het ingesloten bestand, de positie (X/Y), grootte en doel‑dianummer definieert.  
- `ImportDocument` is de Merger‑API‑aanroep die het OLE‑object in het PowerPoint‑bestand invoegt met de opgegeven opties.

## Veelvoorkomende configuratie‑parameters
- **SlideNumber** – de 1‑gebaseerde index van de dia die het OLE‑object zal bevatten.  
- **XCoordinate / YCoordinate** – positie gemeten in punten vanaf de linkerbovenhoek van de dia.  
- **Width / Height** – afmetingen van de OLE‑placeholder; stel in op 0 om de standaardgrootte te gebruiken.  
- **ObjectName** – optionele vriendelijke naam die wordt weergegeven wanneer het object in PowerPoint is geselecteerd.

## Praktische toepassingen
Het insluiten van een PDF als OLE‑object blinkt uit in vele praktijkscenario's:

1. **Bedrijfsbriefings** – voeg het nieuwste financiële rapport toe zonder de presentatiedimensie te vergroten.  
2. **Academische lezingen** – lever volledige onderzoeksartikelen naast diavoorstellingen.  
3. **Projectstatusupdates** – sluit een live projectplan in dat belanghebbenden kunnen openen voor details.  
4. **Verkooppresentaties** – voeg productspecificaties toe die verkopers op aanvraag kunnen openen.  
5. **Technische workshops** – presenteer schema's of datasheets die ingenieurs direct kunnen inspecteren.

## Prestatie‑overwegingen
Om het insluitingsproces snel en geheugen‑vriendelijk te houden:

- **Bestanden streamen** – GroupDocs.Merger leest en schrijft streams, dus zelfs een PDF van 200 pagina’s gebruikt minder dan 100 MB RAM.  
- **Batch‑verwerking** – bij het bijwerken van veel presentaties, hergebruik een enkele `Merger`‑instantie en sluit streams direct.  
- **Grote PDF’s verkleinen** – comprimeer of verlaag de resolutie van afbeeldingen in de bron‑PDF als je trage laadtijden opmerkt.

## Veelgestelde vragen

**Q: Kan ik meerdere PDF’s in één presentatie insluiten?**  
A: Ja. Roep `ImportDocument` aan voor elke PDF, met een andere `SlideNumber` of positie op dezelfde dia.

**Q: Hoe groot mag een PDF zijn die ik kan insluiten?**  
A: De praktische limiet wordt bepaald door het geheugen van je server; insluitingen tot 500 MB zijn getest zonder problemen bij streaming.

**Q: Behoudt het OLE‑object interactieve elementen zoals hyperlinks?**  
A: Absoluut. De ingesloten PDF opent in de standaardviewer, waarbij alle interne links en bladwijzers behouden blijven.

**Q: Wat als de PDF met een wachtwoord is beveiligd?**  
A: Geef het wachtwoord via de `Password`‑eigenschap van `OlePresentationOptions` voordat je `ImportDocument` aanroept.

**Q: Werkt het ingesloten object op alle versies van PowerPoint?**  
A: Het OLE‑formaat wordt ondersteund door PowerPoint 2007 en later, inclusief Office 365.

## Conclusie
Je hebt nu een volledige, productie‑klare workflow voor **embed pdf in powerpoint** als OLE‑object met GroupDocs.Merger voor .NET. Door bestanden te streamen, `OlePresentationOptions` te configureren en `ImportDocument` aan te roepen, kun je presentaties verrijken met originele PDF’s terwijl je het geheugenverbruik laag houdt en alle interactieve functies behoudt. Ontdek extra Merger‑mogelijkheden zoals het samenvoegen van dia’s, het converteren van formaten en watermerken om je document‑pijplijnen verder te automatiseren.

---

**Laatst bijgewerkt:** 2026-09-21  
**Getest met:** GroupDocs.Merger 23.12 for .NET  
**Auteur:** GroupDocs  

## Bronnen
- **Documentatie:** [GroupDocs.Merger voor .NET Documentatie](https://docs.groupdocs.com/merger/net/)  
- **API‑referentie:** [GroupDocs.Merger API‑referentie](https://reference.groupdocs.com/merger/net/)  
- **Download:** [GroupDocs.Merger downloads](https://releases.groupdocs.com/merger/net/)  
- **Aankoop:** [Koop GroupDocs‑licentie](https://purchase.groupdocs.com/buy)  
- **Gratis proefversie:** [GroupDocs gratis proefversie](https://releases.groupdocs.com/merger/net/)  
- **Tijdelijke licentie:** [Vraag een tijdelijke licentie aan](https://purchase.groupdocs.com/temporary-license)

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

## Gerelateerde tutorials

- [PDF in Word insluiten met GroupDocs.Merger voor .NET: Een stapsgewijze handleiding](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [PDF laden vanaf URL in .NET met GroupDocs.Merger: Een uitgebreide gids](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [Documentinformatie ophalen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)