---
date: '2026-09-26'
description: Leer hoe u specifieke PDF-pagina's kunt extraheren met GroupDocs.Merger
  for .NET, inclusief het extraheren van pagina's uit Word en het efficiënt verwerken
  van grote documenten.
keywords:
- extract specific pages pdf
- extract pages from word
- extract pages from large document
lastmod: '2026-09-26'
og_description: Leer hoe u specifieke PDF-pagina's kunt extraheren met GroupDocs.Merger
  for .NET. Deze gids toont een stap‑voor‑stap installatie, code‑vrije configuratie
  en prestatie‑tips voor Word, PDF en grote documenten.
og_image_alt: Guide showing how to extract specific pages pdf using GroupDocs.Merger
  for .NET
og_title: Specifieke PDF-pagina's extraheren met GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  headline: Extract specific pages pdf with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  name: Extract specific pages pdf with GroupDocs.Merger for .NET
  steps:
  - name: install the NuGet package
    text: 'Open a terminal in your project folder and run one of the following commands:
      **.NET CLI** **Package Manager Console** **NuGet Package Manager UI** – use
      the UI to search for “GroupDocs.Merger” and click **Install**.'
  - name: define file paths
    text: Specify absolute or relative paths for the input and the output document
      you want to create. **Definition anchor** `ExtractOptions` is the configuration
      object that tells the library which pages to pull out and how to treat them.
  - name: set extraction options
    text: Create an `ExtractOptions` instance, set `StartPageNumber`, `EndPageNumber`,
      and choose `RangeMode` (e.g., `Even`). This tells the engine to pick every second
      page within the range. **Definition anchor** `Merger` is the core class that
      orchestrates all document‑manipulation operations, including ext
  - name: extract and save
    text: Invoke the `Extract` method on the `Merger` instance, passing the options
      and the output path. The library writes the new file without loading the whole
      source into memory, which is ideal for large documents.
  type: HowTo
- questions:
  - answer: GroupDocs.Merger supports more than 30 formats, including PDF, DOCX, XLSX,
      PPTX, HTML, and image types like PNG and JPEG.
    question: What file formats can I extract pages from?
  - answer: Yes, you can pass a list of individual page numbers or multiple ranges
      to `ExtractOptions`.
    question: Can I extract non‑contiguous pages (e.g., 1, 3, 5)?
  - answer: Provide the password through `LoadOptions` when constructing the `Merger`
      instance; the extraction will then proceed normally.
    question: How do I work with password‑protected PDFs?
  - answer: No hard limit; the only practical constraint is the available memory,
      which remains low thanks to streaming.
    question: Is there a limit on the number of pages I can extract in one call?
  - answer: No external applications are needed; all processing happens inside the
      .NET runtime.
    question: Does the library require Microsoft Office or Adobe Acrobat to be installed?
  type: FAQPage
tags:
- extract specific pages pdf
- GroupDocs.Merger
- .NET document processing
title: Specifieke PDF-pagina's extraheren met GroupDocs.Merger for .NET
type: docs
url: /nl/net/document-extraction/extract-pages-groupdocs-merger-net/
weight: 1
---

# Specifieke pagina's pdf extraheren met GroupDocs.Merger voor .NET

Het extraheren van specifieke pagina's pdf uit een meer‑pagina document is een veelvoorkomende vereiste wanneer je alleen relevante secties wilt delen, de bestandsgrootte wilt verkleinen, of review‑workflows wilt automatiseren. In deze tutorial ontdek je hoe GroupDocs.Merger voor .NET je in staat stelt exacte pagina's te halen—of ze nu uit een PDF, Word‑bestand of een van de meer dan 30 ondersteunde formaten komen—met een duidelijke, programmeerbare aanpak.

## Snelle antwoorden
- **Kan GroupDocs.Merger pagina's extraheren uit Word‑documenten?** Ja, het werkt met DOCX, DOC en andere Office‑formaten.
- **Is er een bestandsgrootte‑limiet?** De bibliotheek kan bestanden tot 2 GB verwerken zonder het volledige document in het geheugen te laden.
- **Heb ik een licentie nodig voor ontwikkeling?** Er is een gratis proefversie beschikbaar; een licentie is vereist voor productiegebruik.
- **Werkt het op .NET 6?** Absoluut—GroupDocs.Merger ondersteunt .NET Framework 4.5+, .NET Core 3.1+ en .NET 5/6+.
- **Hoeveel pagina's kan ik in één keer extraheren?** Je kunt enkele pagina's, bereiken of even‑oneven selecties specificeren in één oproep.

## Wat is GroupDocs.Merger voor .NET?
GroupDocs.Merger voor .NET is een server‑side bibliotheek die het samenvoegen, splitsen, roteren en extraheren van pagina's uit meer dan 30 documentformaten mogelijk maakt zonder dat Microsoft Office of Adobe Acrobat nodig is. Het verwerkt bestanden op een streaming‑manier, waardoor het geheugenverbruik laag blijft, zelfs bij PDF's met honderden pagina's.

## Waarom specifieke pagina's pdf extraheren?
Het extraheren van specifieke pagina's pdf vermindert de bandbreedte, versnelt de samenwerking en zorgt ervoor dat vertrouwelijke secties verborgen blijven. Kwantificeerbaar voordeel: organisaties melden tot 40 % snellere document‑reviewcycli wanneer ze alleen de benodigde pagina's delen in plaats van volledige bestanden. Bovendien verbeteren kleinere bestanden de laadtijden voor web‑viewers en verlagen ze de opslagkosten.

## Voorvereisten
- Visual Studio 2022 of een .NET‑compatibele IDE.
- .NET 6 SDK (of .NET Framework 4.7.2+).
- Toegang tot een NuGet‑feed om **GroupDocs.Merger** te installeren.
- Basiskennis van C# en bestands‑systeemrechten.

## Hoe specifieke pagina's pdf stap voor stap extraheren

Laad je bronbestand, definieer de benodigde pagina's, en sla het resultaat op—alles in een paar regels code.

### Direct antwoord
`Merger` is de kernklasse die documentmanipulatie‑operaties coördineert. `ExtractOptions` specificeert welke pagina's moeten worden geëxtraheerd en hoe ze moeten worden verwerkt. `Extract` voert de extractie uit op basis van de opgegeven opties en schrijft het resultaat naar een nieuw bestand. Om specifieke pagina's pdf te extraheren, maak je een `Merger`‑instantie met het bronbestand, configureer je een `ExtractOptions`‑object dat het paginabereik en de modus (even, odd, of custom) definieert, roep je vervolgens `Extract` aan en sla je het uitvoerbestand op. Deze volledige workflow draait in minder dan een seconde voor typische 100‑pagina PDF's op een standaard server.

### Stap 1: installeer het NuGet‑pakket
Open een terminal in je projectmap en voer een van de volgende commando's uit:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager Console**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – gebruik de UI om te zoeken naar “GroupDocs.Merger” en klik op **Install**.

### Stap 2: definieer bestandspaden
Geef absolute of relatieve paden op voor het invoer‑ en uitvoerdocument dat je wilt maken.

**Definitie‑anker**  
`ExtractOptions` is the configuration object that tells the library which pages to pull out and how to treat them.  
```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY\\Sample.docx"; // Input document path
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "ExtractedPages.docx"); // Output document path
```  

### Stap 3: stel extractie‑opties in
Maak een `ExtractOptions`‑instantie, stel `StartPageNumber`, `EndPageNumber` in, en kies `RangeMode` (bijv. `Even`). Dit vertelt de engine om elke tweede pagina binnen het bereik te selecteren.

**Definitie‑anker**  
`Merger` is the core class that orchestrates all document‑manipulation operations, including extraction, merging, and page rotation.  
```csharp
ExtractOptions extractOptions = new ExtractOptions(1, 3, RangeMode.EvenPages);
```  

### Stap 4: extraheren en opslaan
Roep de `Extract`‑methode aan op de `Merger`‑instantie, waarbij je de opties en het uitvoerpad doorgeeft. De bibliotheek schrijft het nieuwe bestand zonder de volledige bron in het geheugen te laden, wat ideaal is voor grote documenten.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ExtractPages(extractOptions);
    merger.Save(filePathOut); // Save the result to a specified path
}
```  

## Veelvoorkomende problemen en oplossingen
- **Pagina's niet geëxtraheerd** – controleer of `StartPageNumber` en `EndPageNumber` 1‑gebaseerd zijn en of het bronbestand daadwerkelijk het gevraagde bereik bevat.
- **Out‑of‑memory‑fouten bij enorme bestanden** – zorg ervoor dat je de streaming‑API (de standaard) gebruikt en dat je proces voldoende virtueel geheugen heeft; overweeg de `maxMemory`‑instelling in de bibliotheekconfiguratie te verhogen.
- **Wachtwoord‑beveiligde bestanden** – `LoadOptions` stelt je in staat parameters zoals wachtwoorden in te stellen bij het laden van een beschermd document. Geef het wachtwoord door via `LoadOptions` voordat je de `Merger`‑instantie maakt.

## Praktische toepassingen
1. **Documentreview** – haal alleen de clausules die een reviewer nodig heeft, en houd de rest vertrouwelijk.  
2. **Onderwijs** – genereer aangepaste hand-outs door college‑slides of hoofdstukken uit een leerboek te extraheren.  
3. **Juridische workflows** – isoleer expositie‑pagina's voor gerechtelijke indieningen zonder volledige dossiers bloot te stellen.

## Prestatieoverwegingen
GroupDocs.Merger verwerkt documenten op een streaming‑manier, waardoor het bestanden tot **2 GB** kan verwerken terwijl het piekgeheugen onder **150 MB** blijft. Voor optimale resultaten, wikkel je het `Merger`‑object in een `using`‑statement om gegarandeerde opruiming te verzekeren, en hergebruik je één instantie bij het extraheren van meerdere bereiken uit dezelfde bron.

## Conclusie
Je hebt nu een volledige, productie‑klare methode om specifieke pagina's pdf te extraheren met GroupDocs.Merger voor .NET. Door `ExtractOptions` te configureren en de streaming‑engine van de bibliotheek te benutten, kun je document‑slicing automatiseren voor elk ondersteund formaat, de samenwerking versnellen en gevoelige informatie onder controle houden.

**Volgende stappen** – verken de andere mogelijkheden van de bibliotheek, zoals het samenvoegen van documenten, het roteren van pagina's en het toepassen van watermerken om volledig geautomatiseerde document‑pijplijnen te creëren.

## Veelgestelde vragen

**Q: Welke bestandsformaten kan ik pagina's uit extraheren?**  
A: GroupDocs.Merger ondersteunt meer dan 30 formaten, waaronder PDF, DOCX, XLSX, PPTX, HTML en afbeeldingsformaten zoals PNG en JPEG.

**Q: Kan ik niet‑aaneengesloten pagina's extraheren (bijv. 1, 3, 5)?**  
A: Ja, je kunt een lijst met individuele paginanummers of meerdere bereiken doorgeven aan `ExtractOptions`.

**Q: Hoe werk ik met wachtwoord‑beveiligde PDF's?**  
A: Geef het wachtwoord door via `LoadOptions` bij het construeren van de `Merger`‑instantie; de extractie zal dan normaal verlopen.

**Q: Is er een limiet aan het aantal pagina's dat ik in één oproep kan extraheren?**  
A: Geen harde limiet; de enige praktische beperking is het beschikbare geheugen, dat laag blijft dankzij streaming.

**Q: Vereist de bibliotheek dat Microsoft Office of Adobe Acrobat geïnstalleerd is?**  
A: Geen externe applicaties nodig; alle verwerking gebeurt binnen de .NET runtime.

## Bronnen
- [Documentatie](https://docs.groupdocs.com/merger/net/)
- [API‑referentie](https://reference.groupdocs.com/merger/net/)
- [Download GroupDocs.Merger voor .NET](https://releases.groupdocs.com/merger/net/)
- [Koop een licentie](https://purchase.groupdocs.com/buy)
- [Gratis proefversie](https://releases.groupdocs.com/merger/net/)
- [Tijdelijke licentie‑verzoek](https://purchase.groupdocs.com/temporary-license/)
- [Supportforum](https://forum.groupdocs.com/c/merger/)

---

**Laatst bijgewerkt:** 2026-09-26  
**Getest met:** GroupDocs.Merger 23.11 for .NET  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Hoe specifieke PDF-pagina's samenvoegen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Hoe pagina's uit documenten verwijderen met GroupDocs.Merger voor .NET: Een stapsgewijze gids](/merger/net/page-operations/groupdocs-merger-remove-pages-net-tutorial/)
- [Hoe pagina's binnen een document verplaatsen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/page-operations/move-pages-groupdocs-merger-dotnet/)