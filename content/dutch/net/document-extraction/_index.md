---
date: 2026-08-31
description: Leer hoe je specifieke PDF-pagina's kunt extraheren met GroupDocs.Merger
  voor .NET. Stapsgewijze handleidingen behandelen extractiescenario's voor Word,
  PDF en DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Leer hoe je specifieke PDF-pagina's kunt extraheren met GroupDocs.Merger
  voor .NET. Gedetailleerde handleidingen helpen je efficiënt pagina's uit PDF-, Word-
  en DOCX-bestanden te halen.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Hoe specifieke PDF-pagina's te extraheren met GroupDocs.Merger
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
title: Hoe specifieke PDF-pagina's te extraheren met GroupDocs.Merger
type: docs
url: /nl/net/document-extraction/
weight: 9
---

# Hoe specifieke pagina's uit PDF te extraheren met GroupDocs.Merger

Het extraheren van specifieke PDF-pagina's is een veelvoorkomende eis wanneer je een deel van een groter document opnieuw wilt gebruiken, delen of archiveren. Met GroupDocs.Merger voor .NET kun je programmatisch individuele pagina's, paginabereiken of aangepaste selecties uit PDF-, Word- en DOCX-bestanden halen zonder handmatige bewerking. Deze tutorial leidt je door de concepten, vereisten en stapsgewijze workflow zodat je paginavergaring kunt integreren in elke .NET‑applicatie.

## Snelle antwoorden
- **Wat betekent “extract specific pages pdf”?** Het betekent het selecteren van individuele pagina's of bereiken uit een PDF (of ander ondersteund formaat) en deze opslaan als een nieuw, kleiner document.  
- **Welke formaten worden ondersteund?** GroupDocs.Merger ondersteunt meer dan 50 invoer‑ en uitvoerformaten, waaronder PDF, DOCX, PPTX en afbeeldingen.  
- **Heb ik een licentie nodig?** Een tijdelijke licentie werkt voor testen; een volledige licentie is vereist voor productiegebruik.  
- **Kan ik grote bestanden verwerken?** Ja – de bibliotheek verwerkt bestanden met honderden pagina's via streaming, waardoor het geheugenverbruik laag blijft.  
- **Wordt .NET Core ondersteund?** Absoluut – de API werkt met .NET Framework 4.6+, .NET Core 3.1+ en .NET 6/7.

## Wat is extract specific pages pdf?
`extract specific pages pdf` verwijst naar de handeling waarbij één of meer pagina's uit een bestaande PDF (of ondersteund document) worden genomen en een nieuwe PDF wordt gemaakt die alleen die pagina's bevat. Hiermee kun je alleen de relevante secties delen terwijl het originele bestand ongewijzigd blijft.

## Waarom extract specific pages pdf met GroupDocs.Merger?
GroupDocs.Merger verwerkt meer dan **50+ bestandsformaten** en kan pagina's extraheren uit documenten met **500+ pagina's** in minder dan **2 seconden** op een typische server‑grade CPU. De API werkt zonder dat Microsoft Office of Adobe Acrobat geïnstalleerd hoeft te zijn, waardoor de implementatie‑complexiteit en licentiekosten worden verminderd.

## Vereisten
- .NET 6 SDK (of .NET Core 3.1 / .NET Framework 4.6+) geïnstalleerd op je ontwikkelmachine.  
- Een geldig GroupDocs.Merger for .NET NuGet‑pakket (`GroupDocs.Merger`) toegevoegd aan je project.  
- (Optioneel) Een tijdelijk of volledig licentiebestand als je de code wilt uitvoeren na de evaluatieperiode.

## Hoe specifieke pagina's uit PDF te extraheren in C# met GroupDocs.Merger

Laad het bronbestand, specificeer de gewenste pagina's en sla het resultaat op. De bibliotheek abstraheert alle formaat‑specifieke details, zodat dezelfde code werkt voor PDF, DOCX, PPTX en meer.

Laad je bronbestand en roep de `Extract`‑methode aan met de gewenste paginanummers. De `Extract`‑methode maakt een nieuw document aan dat alleen de opgegeven pagina's bevat. De methode retourneert een nieuw `Document`‑object dat je direct kunt opslaan. Een `Document`‑object vertegenwoordigt een in‑memory weergave van het resulterende bestand.

### Stap 1: maak een merger‑instantie
De `Merger`‑klasse is het toegangspunt voor het laden en manipuleren van documenten. Instantieer de `Merger`‑klasse door het pad van het bronbestand door te geven. Dit object vertegenwoordigt het document waarmee je werkt.

### Stap 2: specificeer pagina's om te extraheren
Geef een lijst met paginanummers (1‑gebaseerd) of een bereik‑string zoals "1-3,5" op om de bibliotheek te laten weten welke pagina's behouden moeten blijven.

### Stap 3: sla het geëxtraheerde document op
Roep `Save` aan op het `Document`‑object, waarbij je het uitvoerpad en het gewenste formaat opgeeft (bijv. `SaveFormat.Pdf`). `SaveFormat` is een enumeratie die het type uitvoerbestand specificeert, zoals PDF. De bewerking schrijft een nieuw bestand dat alleen de geselecteerde pagina's bevat.

## Veelvoorkomende problemen en oplossingen
- **Pagina's zijn één verschoven:** GroupDocs.Merger gebruikt 1‑gebaseerde paginanummering. Zorg ervoor dat je lijst begint bij 1, niet bij 0.  
- **Wachtwoord‑beveiligde bestanden:** Geef het wachtwoord door aan de `Merger`‑constructor of gebruik het `LoadOptions`‑object. `LoadOptions` biedt instellingen die bepalen hoe een document wordt geladen, bijv. het inschakelen van geheugen‑caching.  
- **Grote bestanden veroorzaken time‑outs:** Schakel streaming in door `LoadOptions.UseMemoryCache = true` in te stellen om het geheugenverbruik laag te houden.

## Veelgestelde vragen

**V: Kan ik pagina's uit een Word‑document extraheren als PDF?**  
A: Ja – dezelfde `Extract`‑aanroep werkt voor DOCX, en je kunt het resultaat direct opslaan als PDF met `SaveFormat.Pdf`.

**V: Is het mogelijk om niet‑opeenvolgende pagina's te extraheren?**  
A: Absoluut. Geef een door komma's gescheiden lijst op zoals "2,4,7" of een gemengd bereik "1-2,5,8-10".

**V: Ondersteunt de bibliotheek versleutelde PDF's?**  
A: Ja. Geef het wachtwoord op bij het openen van het document; de API zal het automatisch ontsleutelen.

**V: Hoe gaat GroupDocs.Merger om met afbeeldingen in PDF's?**  
A: Afbeeldingen worden exact behouden zoals ze op de geselecteerde pagina's verschijnen; er zijn geen extra conversiestappen nodig.

**V: Welke .NET‑versies worden officieel ondersteund?**  
A: .NET Framework 4.6+, .NET Core 3.1+ en .NET 5/6/7 worden volledig ondersteund.

## Beschikbare tutorials

### [Specifieke pagina's extraheren uit documenten met GroupDocs.Merger voor .NET](./extract-pages-groupdocs-merger-net/)
Leer hoe je efficiënt specifieke pagina's kunt extraheren met GroupDocs.Merger voor .NET. Ideaal voor het beheren van Word, PDF en meer in professionele omgevingen.

### [Hoe specifieke pagina's uit een document te extraheren met GroupDocs.Merger voor .NET in C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Leer hoe je specifieke pagina's uit documenten kunt extraheren met GroupDocs.Merger voor .NET met deze uitgebreide gids. Vereenvoudig je documentbeheer taken moeiteloos.

## Aanvullende bronnen

- [GroupDocs.Merger voor .net Documentatie](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger voor .net API‑referentie](https://reference.groupdocs.com/merger/net/)
- [Download GroupDocs.Merger voor .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Gratis ondersteuning](https://forum.groupdocs.com/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-08-31  
**Tested with:** GroupDocs.Merger 23.9 for .NET  
**Author:** GroupDocs

## Gerelateerde tutorials

- [Hoe specifieke PDF-pagina's samenvoegen met GroupDocs.Merger voor .NET: Een uitgebreide gids](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Hoe specifieke pagina's uit meerdere documenten samenvoegen met GroupDocs.Merger voor .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [PDF-pagina's roteren in .NET met GroupDocs.Merger: Een stapsgewijze gids](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)