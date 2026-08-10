---
date: '2026-07-06'
description: Leer hoe u ondersteunde bestandstypen kunt ophalen met GroupDocs.Merger
  voor Java, controleer ondersteunde extensies voor Java, en integreer de lijst in
  uw workflow.
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: GroupDocs.Merger ondersteunde formaten – Types ophalen in Java
type: docs
url: /nl/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger ondersteunde formaten – Types ophalen in Java

Werken met een breed scala aan documentformaten in Java kan snel een hoofdpijn worden als je niet weet welke formaten je bibliotheek daadwerkelijk ondersteunt. **GroupDocs.Merger supported formats** bieden een betrouwbaar referentiepunt, waardoor je uploads kunt valideren, runtime‑fouten kunt vermijden en slimmere document‑management‑pijplijnen kunt ontwerpen. In deze tutorial zie je precies hoe je de lijst met ondersteunde bestandstypen kunt ophalen met GroupDocs.Merger voor Java, waarom dit belangrijk is en hoe je de informatie kunt integreren in real‑world toepassingen.

### Snelle antwoorden
- **Wat doet “retrieve supported file types”?**  
  Het retourneert een lijst van elk documentformaat dat GroupDocs.Merger kan verwerken.
- **Welke methode levert de lijst?**  
  `FileType.getSupportedFileTypes()` from the `com.groupdocs.merger.domain` package.
- **Heb ik een licentie nodig om deze methode aan te roepen?**  
  Een proef‑ of volledige licentie is vereist voor productiegebruik; de methode werkt in evaluatiemodus.
- **Kan ik de lijst filteren op alleen de extensies die ik nodig heb?**  
  Ja – doorloop de geretourneerde lijst en houd de extensies die je nodig hebt.
- **Is deze bewerking prestatie‑intensief?**  
  Nee, het leest simpelweg een statische collectie, dus het wordt onmiddellijk uitgevoerd.

## Wat zijn de ondersteunde formaten van GroupDocs.Merger?

GroupDocs.Merger ondersteunt **70+** invoer‑ en uitvoerformaten — waaronder PDF, DOCX, PPTX, XLSX, HTML en veelvoorkomende afbeeldingsformaten — waardoor je met praktisch elk zakelijk document kunt werken. De formatentabel van de bibliotheek wordt intern opgeslagen als een statische collectie, dus het ophalen ervan is een O(1)-bewerking die in enkele milliseconden voltooid is, zelfs op bescheiden hardware.

## Hoe kan ik ondersteunde extensies in Java controleren?

Roep de statische `FileType.getSupportedFileTypes()`‑methode aan en loop vervolgens door de geretourneerde collectie om elke extensie te lezen. Deze één‑regelige oproep geeft je een kant‑klaar `List<FileType>` dat je kunt filteren, weergeven of opslaan voor latere validatie.

## Waarom zou ik ondersteunde bestandstypen ophalen vóór verwerking?

Het kennen van de exacte lijst met formaten voorkomt vermijdbare uitzonderingen, vermindert de noodzaak voor defensieve code en stelt je in staat gebruikers een duidelijke “toegestane bestandstypen”‑melding te tonen. Het maakt ook het bouwen van dynamische UI‑componenten mogelijk — zoals bestandskiezer‑filters — die alleen compatibele extensies weergeven, wat de algehele gebruikerservaring verbetert.

## Voorvereisten

- **Java Development Kit (JDK):** Versie 8 of hoger wordt aanbevolen.  
- **Integrated Development Environment (IDE):** Elke IDE zoals IntelliJ IDEA of Eclipse werkt.  
- **GroupDocs.Merger Library:** Neem deze bibliotheek op in de project‑dependencies.  

Bekendheid met basis‑Java‑programmeerconcepten en ervaring met het werken met bibliotheken in een Maven‑ of Gradle‑omgeving zijn ook nuttig. Als je nieuw bent met deze tools, overweeg dan eerst hun documentatie te bekijken.

## GroupDocs.Merger voor Java instellen

Om GroupDocs.Merger voor Java te gebruiken, stel je de bibliotheek in je project in via Maven, Gradle of door direct van de officiële site te downloaden.

### Maven-installatie

Voeg de volgende dependency toe aan je `pom.xml`‑bestand:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle-installatie

Neem deze regel op in je `build.gradle`‑bestand:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Directe download

Download anders de nieuwste versie van [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Stappen voor licentie‑acquisitie
1. **Free Trial:** Start met een gratis proefversie om de functies van de bibliotheek te verkennen.  
2. **Temporary License:** Verkrijg een tijdelijke licentie als je uitgebreide toegang zonder beperkingen nodig hebt.  
3. **Purchase:** Overweeg het aanschaffen van een volledige licentie voor langdurig gebruik.

## Basisinitialisatie en -configuratie

Om GroupDocs.Merger in je Java‑applicatie te initialiseren, importeer je de benodigde klassen:

```java
import com.groupdocs.merger.domain.FileType;
```

Laten we nu doorgaan met het implementeren van de functie die ondersteunde bestandstypen ophaalt.

## Wat is de FileType‑klasse?

De `FileType`‑klasse is het kernmodel in GroupDocs.Merger dat een enkel documentformaat vertegenwoordigt, met zijn extensie, MIME‑type en een vriendelijke weergavenaam. Je werkt met deze klasse wanneer je `FileType.getSupportedFileTypes()` aanroept om de volledige catalogus van formaten te verkrijgen.

## Hoe haal je ondersteunde bestandstypen op?

Om de ondersteunde formaten op te halen, roep je simpelweg de statische methode `FileType.getSupportedFileTypes()` aan die door de GroupDocs.Merger‑bibliotheek wordt geleverd. Deze oproep retourneert een `List<FileType>` met elk formaat dat de bibliotheek kan verwerken. De bewerking is lichtgewicht en kan bij het opstarten van de applicatie of wanneer je bestandsuploads moet valideren, worden uitgevoerd.

### Stap 1: Verkrijg ondersteunde bestandstypen

Haal eerst de lijst met ondersteunde bestandstypen op uit de `FileType`‑klasse:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

Deze methode retourneert een lijst met alle bestandstypen die GroupDocs.Merger ondersteunt.

### Stap 2: Toon ondersteunde extensies

Itereer vervolgens door elk `FileType`‑object en print de extensie. Dit is het gedeelte waarin we **display supported extensions** voor ontwikkelaars of eindgebruikers tonen:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

De lus doorloopt elk ondersteund bestandstype en geeft de extensie weer in de console.

### Stap 3: Bevestigingsbericht

Tot slot geef je een bevestigingsbericht weer dat aangeeft dat het ophalen succesvol was:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Praktische toepassingen

Het begrijpen van ondersteunde bestandstypen is essentieel voor diverse toepassingen:
1. **Document Management Systems:** Documenten automatisch categoriseren op basis van hun type.  
2. **File Conversion Tools:** Compatibiliteit controleren vóór het converteren van bestanden tussen formaten.  
3. **Merging Applications:** Invoergegevens valideren vóór het samenvoegen om fouten te voorkomen.  

Integratie met andere systemen — zoals cloudopslag of document‑verwerkingsservices — kan de functionaliteit verder verbeteren.

## Prestatie‑overwegingen

Bij het werken met GroupDocs.Merger in Java, houd rekening met de volgende prestatie‑tips:
- **Optimize Memory Usage:** Maak objecten vrij wanneer ze niet meer nodig zijn.  
- **Batch Processing:** Verwerk bestanden in batches om het resource‑verbruik te verminderen.  
- **Asynchronous Operations:** Gebruik asynchrone methoden voor niet‑blokkerende bewerkingen.  

## Veelvoorkomende problemen en oplossingen

- **Dependency Issues:** Controleer of Maven‑ of Gradle‑dependencies correct zijn gedeclareerd; versie‑conflicten veroorzaken class‑not‑found‑fouten.  
- **Library Version:** Gebruik altijd de nieuwste GroupDocs.Merger‑release om te profiteren van nieuw toegevoegde formaten en bug‑fixes.  
- **License Errors:** Als je licentie‑exceptions ziet, controleer dan of het proef‑ of permanente licentiebestand correct wordt gerefereerd in je code.

## Veelgestelde vragen

**Q: Wat is GroupDocs.Merger voor Java?**  
A: Het is een Java‑bibliotheek die samenvoegen, splitsen en converteren van een breed scala aan documentformaten mogelijk maakt zonder Microsoft Office te vereisen.

**Q: Hoe begin ik met GroupDocs.Merger?**  
A: Voeg de Maven‑ of Gradle‑dependency toe, verkrijg een proef‑ of volledige licentie, en initialiseert de bibliotheek zoals weergegeven in de installatie‑sectie.

**Q: Kan ik GroupDocs.Merger gratis gebruiken?**  
A: Ja, er is een gratis proefversie beschikbaar voor evaluatie; een volledige licentie is vereist voor productie‑implementaties.

**Q: Welke bestandstypen ondersteunt GroupDocs.Merger?**  
A: Gebruik de `FileType.getSupportedFileTypes()`‑methode om een lijst van **70+** ondersteunde formaten op te halen, waaronder PDF, DOCX, PPTX, XLSX, HTML en afbeeldingsformaten.

**Q: Hoe ga ik om met niet‑ondersteunde bestandstypen?**  
A: Valideer uploads tegen de ondersteunde lijst vóór verwerking; weiger of converteer niet‑ondersteunde bestanden vroegtijdig om runtime‑fouten te voorkomen.

**Q: Kan ik de lijst filteren zodat alleen de extensies die ik nodig heb worden getoond?**  
A: Ja. Na het aanroepen van `getSupportedFileTypes()` kun je de lijst itereren en alleen de gewenste extensies behouden.

**Q: Is een licentie vereist voor ontwikkel‑builds?**  
A: Een proeflicentie werkt voor ontwikkeling en testen; een volledige licentie is vereist voor commercieel productiegebruik.

**Q: Heeft deze methode invloed op de opstarttijd van de applicatie?**  
A: Nee. De lijst met ondersteunde bestandstypen is statisch, dus het ophalen is praktisch onmiddellijk.

**Q: Verandert de lijst met nieuwe bibliotheekversies?**  
A: Nieuwe releases kunnen formaten toevoegen of verwijderen; gebruik altijd de nieuwste versie om de meest actuele lijst te krijgen.

## Bronnen
- [Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Purchase](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support](https://forum.groupdocs.com/c/merger/) 

Voel je vrij om deze bronnen te verkennen voor meer gedetailleerde informatie en ondersteuning. Veel programmeerplezier!

**Last Updated:** 2026-07-06  
**Tested With:** GroupDocs.Merger latest version (as of 2026)  
**Author:** GroupDocs  

## Gerelateerde tutorials

- [GroupDocs.Merger for Java: License Setup & File Existence Check Guide](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Load Local Document Java Using GroupDocs.Merger – Guide](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Merge Specific Pages Java – Document Joining Tutorials for GroupDocs.Merger](/merger/java/document-joining/)