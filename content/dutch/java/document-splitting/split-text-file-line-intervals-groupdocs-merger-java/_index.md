---
date: '2026-07-25'
description: Leer hoe u een bestand per regel kunt splitsen met GroupDocs.Merger voor
  Java – een stapsgewijze handleiding voor efficiënt documentensplitsen in Java‑projecten.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Splits een bestand per regel met GroupDocs.Merger voor Java. Deze
  handleiding laat zien hoe u grote tekstbestanden snel in delen kunt opsplitsen,
  met codevoorbeelden en best‑practice‑tips.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Bestand per regel splitsen met GroupDocs.Merger voor Java – Snel & Eenvoudig
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: Hoe een bestand per regel splitsen met GroupDocs.Merger voor Java
type: docs
url: /nl/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Hoe een bestand te splitsen per regels met GroupDocs.Merger voor Java

Als je **bestand per regels moet splitsen**—bijvoorbeeld om een enorm logbestand op te delen in hapklare brokken, batches met gegevens in een pipeline te voeren, of een lang rapport om te zetten in afzonderlijke hoofdstukbestanden—laat deze tutorial je precies zien hoe je dit doet met GroupDocs.Merger voor Java. Je ziet waarom de bibliotheek tijd bespaart, krijgt een kant‑klaar implementatie, en leert praktische tips die je applicatie snel en betrouwbaar houden.

## Snelle antwoorden
- **Wat betekent “bestand per regels splitsen”?** Het maakt afzonderlijke tekstbestanden die elk een gedefinieerd bereik van regelnummers uit het oorspronkelijke document bevatten.  
- **Welke bibliotheek voert de splitsing uit?** GroupDocs.Merger voor Java biedt een eenvoudige API voor splitsen op basis van regelintervallen.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een permanente licentie is vereist voor productiegebruik.  
- **Kan ik in plaats daarvan splitsen op tekenaantal?** Niet direct—gebruik een pre‑processing stap om het bestand te herschikken vóór het splitsen.  
- **Welke Java‑versie wordt ondersteund?** Elke Java 8+ runtime is compatibel.

## Wat is “bestand per regels splitsen”?
**Bestand per regels splitsen** betekent dat je een enkel tekstdocument neemt en opdeelt in meerdere bestanden, elk met een specifiek bereik van opeenvolgende regels (bijvoorbeeld regels 1‑3, 4‑6, enz.). Deze aanpak is ideaal wanneer je gegevens parallel wilt verwerken, geheugenbelasting wilt verminderen, of simpelweg lange bestanden makkelijker wilt doorbladeren.

## Waarom GroupDocs.Merger voor Java gebruiken?
GroupDocs.Merger abstraheert low‑level bestand‑I/O, zodat je je kunt concentreren op de bedrijfslogica. Het verwerkt efficiënt bestanden tot 2 GB zonder het volledige document in het geheugen te laden, ondersteunt **70+** invoer‑ en uitvoerformaten, en biedt een vloeiende API die naadloos integreert met Maven‑ of Gradle‑builds. Het gebruik van deze bibliotheek verkort de ontwikkelingstijd tot wel **80 %** in vergelijking met handmatig geschreven I/O‑lussen.

## Voorvereisten
- **Java Development Kit (JDK) 8 of hoger** – zorg ervoor dat `java` en `javac` in je PATH staan.  
- **GroupDocs.Merger voor Java** – voeg de bibliotheek toe via Maven, Gradle, of een directe download.  
- **Basiskennis van Java** – je moet vertrouwd zijn met klassen, methoden en foutafhandeling.

## GroupDocs.Merger voor Java instellen
Voeg de bibliotheek toe aan je project met een van de onderstaande methoden.

**Maven** – plak deze afhankelijkheid in je `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – voeg de volgende regel toe in `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Directe download** – je kunt de JAR ook ophalen van de officiële release‑pagina: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Licentie‑acquisitie
Begin met een gratis proefversie om de API te verkennen. Voor productie‑workloads, verkrijg een tijdelijke of volledige licentie via het GroupDocs‑portaal.

## Hoe een tekstbestand per regels te splitsen (Java‑implementatie)

Hieronder vind je een beknopte, stap‑voor‑stap walkthrough. Elke stap wordt in eenvoudige taal uitgelegd vóór de placeholder die aangeeft waar de daadwerkelijke code staat, zodat je precies weet wat er gebeurt.

### Stap 1: Definieer bron‑ en uitvoer‑paden
Geef eerst de bibliotheek aan waar je oorspronkelijke bestand zich bevindt en waar de gesplitste fragmenten moeten worden weggeschreven.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Stap 2: Configureer de split‑opties
Maak een `TextSplitOptions`‑instantie aan die de gewenste regelintervallen beschrijft. De `new int[] { 3, 6 }` array vertelt de API om te knippen na regel 3 en regel 6, waardoor twee delen ontstaan: regels 1‑3 en regels 4‑6.  
**Definitie:** `TextSplitOptions` is een configuratie‑object dat de regel‑interval array en optionele naamgevingsregels voor de uitvoer bevat.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Stap 3: Initialiseert de Merger en voert de splitsing uit
Instantieer tenslotte `Merger` met het bronbestand en roep `split()` aan met de opties die je zojuist hebt gemaakt.  
**Definitie:** `Merger` is de kernklasse in GroupDocs.Merger die documentbewerkingsoperaties coördineert, zoals splitsen, samenvoegen en pagina's extraheren.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Wanneer de `split()`‑aanroep voltooid is, vind je twee nieuwe bestanden in `YOUR_OUTPUT_DIRECTORY`, elk met de opgegeven regelbereiken.

## Praktische toepassingen (Waarom dit belangrijk is)
1. **Data‑verwerkings‑pipelines** – Splits enorme logbestanden in kleinere delen voor parallelle parsing, waardoor de totale verwerkingstijd drastisch wordt verkort.  
2. **Documentbeheer** – Zet een enkel rapport om in hoofdstuk‑bestanden, waardoor distributie naar verschillende teams eenvoudiger wordt.  
3. **Inhoudssegmentatie** – Bereid secties van een groot artikel voor op gerichte publicatieplatformen, wat SEO en leesbaarheid verbetert.

## Prestatie‑tips
- **Stream‑line I/O** – Geef de voorkeur aan `Files.newBufferedReader` bij het verwerken van zeer grote bestanden om het geheugengebruik laag te houden.  
- **Resources sluiten** – Hoewel GroupDocs.Merger het meeste opruimt, voorkomt het expliciet sluiten van aangepaste streams lekken.  
- **Geheugen monitoren** – Het splitsen van bestanden van gigabyte‑grootte kan veel geheugen verbruiken; wijs voldoende heap toe (`-Xmx2g` of hoger) indien nodig.  
- **Batch‑verwerking** – Bij het splitsen van veel bestanden, hergebruik een enkele `Merger`‑instantie om overhead van objectcreatie te verminderen.

## Veelvoorkomende problemen en oplossingen
| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| `OutOfMemoryError` | Groot bronbestand overschrijdt de heap. | Verhoog de JVM‑heap of splits met kleinere intervallen. |
| `FileNotFoundException` | Onjuist pad of ontbrekende rechten. | Controleer of `filePath` en `filePathOut` absoluut en schrijfbaar zijn. |
| Lege uitvoerbestanden | Intervalarray dekt het volledige document niet. | Zorg ervoor dat het laatste interval eindigt op of voorbij het totale aantal regels. |

## Veelgestelde vragen

**Q: Kan ik bestanden splitsen op basis van tekenaantal in plaats van regelnummers?**  
A: Momenteel richt GroupDocs.Merger voor Java zich op regelintervallen. Je kunt echter je tekst vooraf verwerken zodat het gewenste tekenaantal per regel wordt bereikt voordat je deze functie gebruikt.

**Q: Is er een limiet aan het aantal intervallen dat ik kan opgeven voor het splitsen?**  
A: Er is geen harde limiet in de bibliotheek; de prestaties kunnen afnemen als je duizenden kleine splitsingen vraagt, omdat elke split I/O‑overhead veroorzaakt.

**Q: Hoe ga ik om met fouten tijdens het splitsen van bestanden?**  
A: Plaats de splitsingslogica in een try‑catch‑blok en log de details van `MergerException`. De API geeft duidelijke berichten die het falenpunt aanwijzen.

**Q: Ondersteunt de bibliotheek andere tekst‑gebaseerde formaten zoals CSV of TSV?**  
A: Ja, omdat CSV en TSV platte tekstbestanden zijn, geldt dezelfde regel‑intervallogica. Behandel ze als `.txt`‑bestanden bij het aanroepen van de API.

**Q: Kan ik het splitsen automatiseren voor meerdere bestanden in een map?**  
A: Zeker. Iterate over `Files.list(Paths.get("folder"))`, pas dezelfde `TextSplitOptions` toe op elk bestand, en verzamel de gegenereerde delen.

## Aanvullende bronnen
- [GroupDocs.Merger voor Java releases](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger voor Java documentatie](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API-referentie](https://reference.groupdocs.com/merger/java/)
- [Laatste releases](https://releases.groupdocs.com/merger/java/)
- [GroupDocs kopen](https://purchase.groupdocs.com/buy)
- [GroupDocs gratis proefversie](https://releases.groupdocs.com/merger/java/)
- [Tijdelijke licentie verkrijgen](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs support](https://forum.groupdocs.com/c/merger)

---

**Laatst bijgewerkt:** 2026-07-25  
**Getest met:** GroupDocs.Merger 23.12 for Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Hoe een tekstbestand te splitsen in afzonderlijke regel‑documenten met GroupDocs.Merger voor Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [pdf splitsen java: Document splitsen met GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Lokaal document laden Java met GroupDocs.Merger – Gids](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)