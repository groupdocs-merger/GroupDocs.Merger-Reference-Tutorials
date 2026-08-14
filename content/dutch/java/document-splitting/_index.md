---
date: 2026-05-22
description: Leer hoe u enkele pagina PDF-bestanden maakt en PDF's splitst met GroupDocs.Merger
  voor Java. Inclusief stapsgewijze handleidingen voor split pdf java en meer.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: Maak een enkele pagina PDF met GroupDocs.Merger Java
type: docs
url: /nl/java/document-splitting/
weight: 12
---

# Maak een Single Page PDF met GroupDocs.Merger Java

Als je **single page PDF** bestanden moet maken van grotere documenten of simpelweg PDFs wilt splitsen in beter hanteerbare stukken, ben je hier aan het juiste adres. Deze gids leidt je door de meest voorkomende splitsingsscenario's—meervoudige pagina‑bestanden, paginabereiken, oneven/even pagina's, DOCX-splitsen en zelfs tekst‑gebaseerde splits—met behulp van de krachtige GroupDocs.Merger bibliotheek voor Java. Aan het einde van deze tutorial weet je precies hoe je deze technieken in je eigen applicaties kunt integreren, de prestaties van documentverwerking kunt verbeteren en je codebase schoon en onderhoudbaar kunt houden.

## Snelle Antwoorden
- **Wat betekent “single page PDF maken”?** Het betekent dat één pagina uit een brondocument wordt geëxtraheerd en opgeslagen als een onafhankelijk PDF‑bestand.  
- **Welke bibliotheek voert de taak uit?** GroupDocs.Merger voor Java biedt een vloeiende API voor alle splitsingsbewerkingen.  
- **Heb ik een licentie nodig?** Een tijdelijke licentie werkt voor ontwikkeling; een volledige licentie is vereist voor productie.  
- **Kan ik PDF oneven en even pagina's splitsen?** Ja—GroupDocs.Merger laat je pagina's filteren op oneven/even nummers.  
- **Wordt DOCX-splitsen ondersteund?** Absoluut; je kunt DOCX‑bestanden pagina‑voor‑pagina of op aangepaste bereiken splitsen.  

## Wat is “single page PDF maken”?
Een single‑page PDF maken houdt in dat je een meer‑pagina brondocument (PDF, DOCX, PPTX, enz.) neemt en slechts één pagina eruit haalt en opslaat als een eigen PDF‑bestand. Dit is handig voor het genereren van facturen, certificaten of voorbeeldafbeeldingen waarbij alleen een specifieke pagina nodig is.

## Waarom GroupDocs.Merger voor Java gebruiken?
GroupDocs.Merger voor Java biedt een enkele, consistente API die veel documentformaten ondersteunt en tegelijkertijd hoge prestaties en een laag geheugenverbruik levert. Het vereenvoudigt ontwikkeling door complexe bestandsafhandeling te abstraheren, zodat je je kunt concentreren op bedrijfslogica in plaats van op details van low‑level verwerking.

- **Unified API** – Werkt met PDF, DOCX, PPTX, afbeeldingen en vele andere formaten.  
- **High performance** – Geoptimaliseerd voor grote bestanden en batch‑bewerkingen; het kan documenten tot 2 GB verwerken zonder het volledige bestand in het geheugen te laden.  
- **Fine‑grained control** – Splits op paginabereik, oneven/even pagina's of aangepaste scheidingstekens.  
- **Stream‑friendly** – Output kan worden opgeslagen naar een bestand of geretourneerd als een stream voor webservices.

## Vereisten
- Java 8 of nieuwer.  
- GroupDocs.Merger voor Java toegevoegd aan je project (Maven/Gradle).  
- Een geldig (tijdelijk of volledig) GroupDocs‑licentiebestand.

## Hoe maak je een single page PDF?
Een single‑page PDF maken met GroupDocs.Merger omvat het laden van het bronbestand, het specificeren van de exacte pagina of het bereik, het aanroepen van de split‑bewerking en uiteindelijk het opslaan van het resultaat. Deze workflow zorgt ervoor dat het originele document onaangeroerd blijft terwijl de geëxtraheerde pagina wordt opgeslagen als een onafhankelijk PDF‑bestand.

De `Merger`‑klasse is de kerncomponent die bron‑documenten laadt en split‑functionaliteit biedt.

### Stap 1: Initialiseer de Merger
De `Merger`‑klasse is de kerncomponent van GroupDocs.Merger die een bron‑document laadt en split‑bewerkingen biedt. Maak een instantie aan door het bestandspad of een invoerstroom door te geven.

### Stap 2: Definieer de split‑criteria
Kies het exacte paginanummer of bereik dat je nodig hebt. Voor een single‑page extractie specificeer je een bereik zoals `1‑1`. Wanneer je **pdf per bereik wilt splitsen**, kun je meerdere bereiken doorgeven, zoals `1‑5, 6‑10`.

### Stap 3: Voer de split uit
Roep de juiste `split`‑methode aan. Bijvoorbeeld, `merger.split(new int[]{1})` extraheert de eerste pagina, terwijl `merger.splitByRange(new int[][]{{1,5},{6,10}})` meerdere bereiken in één oproep verwerkt.

### Stap 4: Sla het resultaat op
Schrijf elke output naar een bestandspad of retourneer het als een `java.io.InputStream`. Dit maakt het eenvoudig om te integreren met web‑API's of het resultaat op te slaan in cloud‑opslag.

> **Pro tip:** Wanneer je met grote PDFs werkt, roep `merger.setOptimizeResources(true)` aan vóór het splitsen om het geheugenverbruik te verminderen.

## Hoe PDF‑java‑bestanden splitsen in meerdere pagina's
De `Merger`‑klasse biedt de primaire API voor het laden en manipuleren van PDF‑bestanden. Om een PDF te verdelen in afzonderlijke één‑pagina bestanden, laad je simpelweg het document met de Merger‑instantie en roep je de split‑methode zonder parameters aan. De bibliotheek maakt automatisch een nieuwe PDF voor elke pagina, behoudt de originele inhoud en metadata, wat ideaal is voor batch‑verwerking van facturen of rapporten.

## Hoe PDF oneven en even pagina's splitsen
De `Merger`‑klasse is de kerncomponent die split‑bewerkingen op documenten uitvoert. Wanneer je alleen oneven of even pagina's van een PDF nodig hebt, geef je een lijst met de gewenste paginanummers door aan de split‑functie. De Merger genereert een nieuw document dat alleen die pagina's bevat, zodat je snel afzonderlijke bestanden kunt maken voor oneven‑genummerde of even‑genummerde inhoud.

## Hoe docx‑bestanden splitsen (hoe docx splitsen)
De `Merger`‑klasse werkt ook met DOCX‑bestanden. Gebruik `splitByPage` om één DOCX (of PDF) per pagina te genereren, of combineer het met `saveAsPdf` als je PDF‑output nodig hebt. Dit omvat de **docx to pdf java** conversieworkflow in één stap.

## Hoe documenten splitsen in multi‑page bestanden
De `Merger`‑klasse behandelt paginering en bestandscreatie voor split‑bewerkingen. Als je een groot document wilt opdelen in stukken van vaste grootte, specificeer dan het aantal pagina's per output‑bestand. De Merger zal door de bron itereren en nieuwe PDF's maken die elk het gedefinieerde aantal pagina's bevatten, wat archivering, distributie en parallelle verwerking van omvangrijke documenten vereenvoudigt.

## Beschikbare Tutorials

### [Documenten splitsen in multi‑page bestanden met GroupDocs.Merger voor Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Leer hoe je efficiënt grote documenten kunt splitsen in kleinere, multi‑page bestanden met GroupDocs.Merger voor Java. Optimaliseer documentbeheer moeiteloos.

### [Hoe een tekstbestand splitsen op lijnintervallen met GroupDocs.Merger voor Java | Document Splitting Guide](./split-text-file-line-intervals-groupdocs-merger-java/)
Leer hoe je tekstbestanden kunt splitsen in beheersbare secties met behulp van lijnintervallen met GroupDocs.Merger voor Java. Een uitgebreide gids voor efficiënt documentbeheer.

### [Documenten splitsen op paginabereik met GroupDocs.Merger voor Java](./split-documents-page-range-groupdocs-merger-java/)
Leer hoe je documenten kunt splitsen in specifieke paginabereiken met GroupDocs.Merger voor Java. Stroomlijn documentbeheer en pas filters toe zoals oneven/even pagina's.

### [Documenten splitsen met GroupDocs.Merger&#58; Een uitgebreide gids](./master-document-splitting-groupdocs-merger-java/)
Leer hoe je efficiënt documenten kunt splitsen in enkele pagina's met GroupDocs.Merger voor Java. Deze gids behandelt installatie, implementatie en praktische toepassingen.

### [Java Document Splitting met GroupDocs.Merger&#58; DOCX-pagina's splitsen in bestanden en streams](./master-java-document-splitting-groupdocs-merger/)
Leer hoe je efficiënt DOCX‑documenten kunt splitsen in afzonderlijke pagina's of streams met GroupDocs.Merger voor Java. Deze gids behandelt installatie, implementatie en praktische toepassingen.

## Aanvullende bronnen

- [GroupDocs.Merger voor Java Documentatie](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger voor Java API-referentie](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger voor Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Gratis ondersteuning](https://forum.groupdocs.com/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

## Veelvoorkomende problemen en oplossingen
| Probleem | Oplossing |
|----------|-----------|
| **Geheugenoverbelasting bij grote PDFs** | Schakel resource‑optimalisatie in: `merger.setOptimizeResources(true);` |
| **Onjuiste paginanummers na het splitsen** | Onthoud dat paginanummering begint bij 1, niet bij 0. |
| **Licentie niet gevonden** | Controleer het pad naar je `GroupDocs.Merger.lic`‑bestand en zorg ervoor dat het in de classpath is opgenomen. |
| **Splitsen van DOCX resulteert in lege pagina's** | Zorg ervoor dat de bron‑DOCX correcte pagina‑breuken heeft; gebruik anders `splitByParagraph` als alternatief. |

## Veelgestelde vragen

**Q: Kan ik een met wachtwoord beveiligde PDF splitsen?**  
A: Ja. Laad het document met de wachtwoordparameter en voer vervolgens elke split‑bewerking uit zoals gewoonlijk.

**Q: Hoe split ik alleen de oneven pagina's van een PDF?**  
A: Geef een paginalijst met alleen oneven nummers (bijv. 1,3,5…) door aan de `split`‑methode.

**Q: Is het mogelijk om een DOCX direct in PDF's te splitsen?**  
A: Absoluut. Na het laden van de DOCX roep je `saveAsPdf` aan voor elk gesplitst segment.

**Q: Welke formaten ondersteunt GroupDocs.Merger voor splitsen?**  
A: PDF, DOCX, PPTX, TXT, HTML en vele afbeeldingsformaten (PNG, JPEG, enz.).

**Q: Heb ik een aparte licentie nodig voor elk bestandstype?**  
A: Nee. Eén GroupDocs.Merger‑licentie dekt alle ondersteunde formaten.

**Laatst bijgewerkt:** 2026-05-22  
**Getest met:** GroupDocs.Merger 23.11 voor Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [split pdf java: Document Splitting met GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Documenten splitsen op paginabereik met GroupDocs.Merger voor Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [PDF's efficiënt samenvoegen met GroupDocs.Merger voor Java: Een stap‑voor‑stap gids](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)