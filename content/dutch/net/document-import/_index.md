---
date: 2026-09-11
description: Leer hoe u PDF kunt importeren in Word en andere formaten met GroupDocs.Merger
  for .NET, inclusief embed PDF Word en PDF-bijlagen toevoegen in een paar eenvoudige
  stappen.
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: Leer hoe u PDF kunt importeren in Word en andere formaten met GroupDocs.Merger
  for .NET, met inbegrip van embed PDF Word, PDF-bijlagen toevoegen en OLE-embedding.
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: Hoe PDF te importeren in Word met GroupDocs.Merger for .NET
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
title: Hoe PDF te importeren in Word met GroupDocs.Merger for .NET
type: docs
url: /nl/net/document-import/
weight: 10
---

# Hoe PDF te importeren in Word met GroupDocs.Merger voor .NET

In deze gids ontdek je hoe je **PDF importeren in Word** en andere documenttypen kunt uitvoeren met GroupDocs.Merger voor .NET. Of je nu een PDF in een Word‑bestand wilt insluiten, PDF‑s wilt bijvoegen aan bestaande documenten, of inhoud wilt verplaatsen tussen diagrammen, presentaties, spreadsheets en tekstverwerkingsbestanden, deze tutorial leidt je door de meest voorkomende scenario’s, legt uit waarom ze belangrijk zijn, en toont je de exacte stappen om het snel te voltooien.

## Snelle antwoorden
- **Kan ik een PDF importeren in een Word‑document?** Ja – GroupDocs.Merger laat je een PDF insluiten als OLE‑object of als native content in een .docx‑bestand.  
- **Heb ik een aparte PDF‑bibliotheek nodig?** Nee, de Merger‑SDK verwerkt PDF‑import zonder extra afhankelijkheden.  
- **Welke .NET‑versies worden ondersteund?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Is een licentie vereist voor productie?** Een commerciële licentie is vereist voor productie; een gratis proefversie is beschikbaar voor evaluatie.  
- **Hoe groot mag een PDF zijn die ik kan importeren?** Tot 500 MB per bestand wordt ondersteund zonder het volledige document in het geheugen te laden.

## Wat is PDF importeren in Word?
PDF importeren in Word betekent dat je de inhoud van een PDF‑bestand neemt en deze plaatst in een Microsoft Word (.docx) document, hetzij als een ingebed object of als geconverteerde native elementen, terwijl de lay-out, afbeeldingen en tekstopmaak behouden blijven. Het proces kan tekststroom, afbeeldingen, tabellen en vector‑graphics behouden, zodat het resulterende Word‑bestand er zo dicht mogelijk bij de oorspronkelijke PDF‑lay-out uitziet.

## Waarom GroupDocs.Merger voor deze taak gebruiken?
GroupDocs.Merger ondersteunt **30+ invoer‑ en uitvoerformaten** en kan documenten verwerken tot **500 MB** zonder ze volledig in RAM te laden, waardoor de geheugenbelasting op server‑side applicaties wordt verminderd. De bibliotheek biedt bovendien **ingebouwde OLE‑insluiting**, waardoor je PDF‑s direct kunt bijvoegen aan Word-, Excel‑ of PowerPoint‑bestanden met één API‑aanroep.

## Vereisten
- .NET‑ontwikkelomgeving (Visual Studio 2022 of later).  
- GroupDocs.Merger for .NET NuGet‑pakket geïnstalleerd (`Install-Package GroupDocs.Merger`).  
- Een geldige GroupDocs.Merger‑licentie voor productiegebruik (een tijdelijke licentie is beschikbaar voor testen).

## Hoe PDF te importeren in Word stap voor stap

### Hoe embed ik een PDF‑bestand in een Word‑document?
`Merger` is de kernklasse van de GroupDocs.Merger SDK die methoden voor documentmanipulatie biedt.  
`Insert` voegt een bron‑document of object in een doel‑document in op een opgegeven positie.  

Laad de bron‑PDF met `Merger` en roep `Insert` aan om deze in het doel‑`.docx` te plaatsen. De bewerking wordt uitgevoerd in twee regels code en behandelt automatisch OLE‑verpakking, zodat de PDF verschijnt als een interactief object in Word.

### Hoe voeg ik PDF‑bijlagen toe aan een bestaand Word‑bestand?
`AddAttachment` voegt een extern bestand toe aan een container‑document en slaat het op in het pakket voor later gebruik.  

Maak een `Merger`‑instantie, open het Word‑document en gebruik de `AddAttachment`‑methode om de PDF toe te voegen. De bijlage wordt opgeslagen in het Word‑pakket en kan rechtstreeks worden geopend vanuit het “Insert > Object”‑dialoogvenster van het document.

### Hoe embed ik OLE‑objecten (zoals PDF's) in Excel‑werkbladen?
`InsertOleObject` embedt een OLE‑object, zoals een PDF, in een spreadsheet‑cel, waardoor interactief openen vanuit Excel mogelijk is.  

Gebruik de `InsertOleObject`‑methode op een Excel‑werkmap. De methode accepteert het PDF‑bestandspad en de cel‑locatie, en voegt de PDF in als een OLE‑object dat door dubbelklikken kan worden geopend.

## Veelvoorkomende problemen en oplossingen
- **PDF verschijnt alleen als een pictogram:** Zorg ervoor dat het doel‑Word‑bestand is opgeslagen met de `.docx`‑extensie; oudere `.doc`‑bestanden ondersteunen geen ingebedde OLE‑objecten.  
- **Grote PDF‑s veroorzaken trage import:** Roep `MergerSettings.EnableMemoryOptimization = true` aan vóór het importeren om het geheugenverbruik laag te houden.  
- **Ingebedde PDF is niet klikbaar:** Controleer of het PDF‑bestand niet met een wachtwoord is beveiligd; Merger kan geen versleutelde PDF‑s embedden zonder het wachtwoord te verstrekken.

## Veelgestelde vragen

**Q: Kan ik alleen geselecteerde pagina's van een PDF importeren in Word?**  
A: Ja – gebruik de `PageRange`‑optie bij het aanroepen van `Insert` om aan te geven welke pagina's moeten worden ingesloten.

**Q: Behoudt de bibliotheek hyperlinks in de PDF bij het importeren?**  
A: Bij insluiting als OLE‑object blijven hyperlinks functioneel in de PDF‑viewer; bij conversie naar native Word‑content worden de meeste hyperlinks behouden.

**Q: Is het mogelijk om meerdere PDF‑s in één Word‑document batch‑te importeren?**  
A: Absoluut. Loop door je PDF‑collectie en roep `Insert` aan voor elk bestand; de bibliotheek voegt ze opeenvolgend samen.

**Q: Wat als mijn PDF vector‑graphics bevat?**  
A: Vector‑graphics worden behouden wanneer de PDF wordt ingesloten als OLE‑object; ze renderen scherp op elk zoomniveau.

**Q: Werkt GroupDocs.Merger op Linux‑containers?**  
A: Ja – de .NET Standard‑build draait op Linux, macOS en Windows zonder native afhankelijkheden.

## Beschikbare tutorials

### [Bijlagen toevoegen aan PDF's met GroupDocs.Merger voor .NET&#58; Een stapsgewijze handleiding](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Leer hoe je bijlagen toevoegt aan PDF‑s met GroupDocs.Merger voor .NET. Deze stapsgewijze handleiding behandelt installatie, implementatie en praktische toepassingen.

### [PDF embedden als OLE in PowerPoint met GroupDocs.Merger voor .NET&#58; Een stapsgewijze handleiding](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Leer hoe je naadloos een PDF‑bestand als OLE‑object in je PowerPoint‑presentatie embedt met GroupDocs.Merger voor .NET. Volg deze uitgebreide gids.

### [PDF embedden in Word met GroupDocs.Merger voor .NET&#58; Een stapsgewijze handleiding](./embed-pdf-word-groupdocs-merger-dotnet/)
Leer hoe je naadloos een PDF embedt in een Microsoft Word‑document met GroupDocs.Merger voor .NET. Verhoog je documenten met dynamische inhoud efficiënt.

### [Hoe OLE‑objecten embedden in Excel‑werkbladen met GroupDocs.Merger voor .NET](./embed-ole-objects-groupdocs-merger-net/)
Leer hoe je naadloos OLE‑objecten zoals PDF‑s embedt in Excel‑werkbladen met GroupDocs.Merger voor .NET, waardoor de presentatie en functionaliteit van gegevens wordt verbeterd.

## Aanvullende bronnen

- [GroupDocs.Merger voor .net Documentatie](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger voor .net API‑referentie](https://reference.groupdocs.com/merger/net/)
- [Download GroupDocs.Merger voor .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Gratis ondersteuning](https://forum.groupdocs.com/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

---

**Laatst bijgewerkt:** 2026-09-11  
**Getest met:** GroupDocs.Merger 23.12 for .NET  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [PDF embedden in Word met GroupDocs.Merger voor .NET: Een stapsgewijze handleiding](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Bijlagen toevoegen aan PDF's met GroupDocs.Merger voor .NET: Een stapsgewijze handleiding](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [PDF laden vanaf URL in .NET met GroupDocs.Merger: Een uitgebreide handleiding](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)