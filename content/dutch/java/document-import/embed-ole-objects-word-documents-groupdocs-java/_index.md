---
date: '2025-12-19'
description: Leer hoe je pdf's in Word-documenten kunt insluiten en pdf's aan Word-bestanden
  kunt toevoegen met GroupDocs.Merger voor Java. Stapsgewijze tutorial voor naadloze
  OLE-insluiting.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: Hoe PDF in Word in te sluiten met GroupDocs.Merger voor Java – Een uitgebreide
  gids
type: docs
url: /nl/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# Hoe pdf in Word in te sluiten met GroupDocs.Merger voor Java

Het direct insluiten van een PDF in een Word‑document kan de samenwerking aanzienlijk verbeteren, omdat lezers niet meer tussen bestanden hoeven te schakelen. In deze gids ontdek je **hoe pdf in word in te sluiten** met GroupDocs.Merger voor Java, en zie je praktische tips over **pdf aan word toevoegen** workflows. We lopen alles door, van het installeren van de bibliotheek tot het aanpassen van de grootte en positie van het OLE‑object.

## Snelle antwoorden
- **Welke bibliotheek is vereist?** GroupDocs.Merger for Java (nieuwste versie)  
- **Kan ik elk bestandstype insluiten?** Ja – PDF's, afbeeldingen, spreadsheets, enz., als OLE‑objecten  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor ontwikkeling; een commerciële licentie is vereist voor productie  
- **Welke Java‑IDE werkt het beste?** IntelliJ IDEA, Eclipse, of elke IDE die Maven/Gradle ondersteunt  
- **Hoe lang duurt de implementatie?** Ongeveer 10‑15 minuten voor een eenvoudige insluiting  

## Wat is pdf in word insluiten?
Het insluiten van een PDF creëert een OLE (Object Linking and Embedding) object binnen het Word‑bestand. De PDF blijft volledig functioneel—gebruikers kunnen dubbelklikken op het pictogram om het te openen in een PDF‑viewer, terwijl het Word‑document zelf‑bevat blijft.

## Waarom pdf aan word toevoegen met GroupDocs.Merger?
- **Documentatie uit één bron:** Houd contracten, handleidingen of rapporten samen zonder externe koppelingen.  
- **Verbeterde toegankelijkheid:** Lezers kunnen de PDF bekijken zonder de Word‑omgeving te verlaten.  
- **Automatiseringsvriendelijk:** Perfect voor het programmatisch genereren van batch‑rapporten of juridische pakketten.  

## Vereisten
- **Bibliotheken & afhankelijkheden:** Voeg de GroupDocs.Merger‑bibliotheek toe via Maven of Gradle.  
- **Ontwikkelomgeving:** IntelliJ IDEA, Eclipse, of elke Java‑IDE.  
- **Basiskennis:** Vertrouwdheid met Java en concepten voor documentmanipulatie.  

## GroupDocs.Merger voor Java instellen
Om OLE‑objecten in te sluiten, voeg je eerst de bibliotheek toe aan je project.

### Maven
Add this dependency to your `pom.xml` file:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Include this in your `build.gradle` file:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Directe download
Alternatively, download the latest version from the [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/).

**Licentie‑acquisitie:** Je kunt beginnen met een gratis proefversie of een tijdelijke licentie verkrijgen om functies te evalueren voordat je koopt. Bezoek [Purchase GroupDocs](https://purchase.groupdocs.com/buy) voor meer details.

## Basisinitialisatie
Import the required classes so you can work with OLE objects:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Stapsgewijze gids om pdf in word in te sluiten

### Stap 1: Definieer bestands‑paden en doelpagina
Stel het bron‑Word‑document, de PDF die je wilt insluiten, en de locatie in waar het OLE‑object moet verschijnen.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – pad naar het bestaande Word‑bestand.  
- **`embeddedFilePath`** – de PDF die je wilt **pdf aan word toevoegen**.  
- **`outputFilePath`** – waar het nieuwe document wordt opgeslagen.  
- **`pageNumber`** – de pagina die het OLE‑object zal bevatten.  

### Stap 2: Configureer OleWordProcessingOptions
Pas het uiterlijk van de ingesloten PDF aan door de afmetingen in te stellen.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – bepaal hoe groot het PDF‑pictogram verschijnt binnen het Word‑document.  

### Stap 3: Initialiseer Merger en importeer het OLE‑object
Maak een `Merger`‑instantie voor het bron‑document, importeer het OLE‑object en sla het resultaat op.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – neemt de `OleWordProcessingOptions` en voegt de PDF in als OLE‑object.  
- **`save()`** – schrijft het gewijzigde document naar `outputFilePath`.  

### Stap 4: (Optioneel) Configuratie opnieuw toepassen voor extra objecten
Als je meer PDF's moet insluiten, herhaal dan **Stap 1‑3** met nieuwe bestands‑paden en paginanummers. Dezelfde `OleWordProcessingOptions`‑klasse laat je elk object afzonderlijk beheren.

## OleWordProcessingOptions configureren (Geavanceerd)
Je kunt de plaatsing verder aanpassen, zoals het uitlijnen van het object of het toevoegen van een bijschrift. De code‑snippet hieronder herhaalt de basisconfiguratie voor duidelijkheid:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Praktische toepassingen
Het insluiten van PDF's is nuttig in veel praktische scenario's:

1. **Technische handleidingen** – Voeg gedetailleerde schema's of referentie‑PDF's direct in de gids in.  
2. **Financiële rapporten** – Voeg aanvullende audit‑PDF's toe zonder de stroom van het hoofdrapport te onderbreken.  
3. **Juridische contracten** – Voeg bijlagen of bijlagen toe als OLE‑objecten voor gemakkelijke toegang tijdens de beoordeling.  

## Prestatie‑overwegingen
Bij het verwerken van grote documenten of meerdere OLE‑objecten, houd deze tips in gedachten:

- **Verwijder onnodige inhoud** – sluit alleen de pagina's in die je echt nodig hebt.  
- **Beheer geheugen** – gebruik Java’s `-Xmx`‑vlag om voldoende heap‑ruimte toe te wijzen voor grote bestanden.  
- **Blijf up‑to‑date** – nieuwere GroupDocs.Merger‑releases bevatten vaak prestatie‑optimalisaties.  

## Veelgestelde vragen

**Q: Wat is OLE‑insluiting?**  
A: Insluiten stelt je in staat om objecten zoals PDF's in Word‑documenten te plaatsen als koppelingen die hun oorspronkelijke functionaliteit behouden.

**Q: Kan ik meerdere OLE‑objecten in één document insluiten?**  
A: Ja, elk kan worden geconfigureerd voor verschillende pagina's en groottes met afzonderlijke `OleWordProcessingOptions`.

**Q: Is er een limiet op de grootte van ingesloten bestanden?**  
A: De limiet wordt meestal bepaald door de eigen beperkingen van Word, maar GroupDocs.Merger verwerkt grote bestanden efficiënt.

**Q: Hoe los ik insluitfouten op?**  
A: Controleer of de bestands‑paden correct zijn en of de JVM voldoende geheugen heeft. Controleer of de bron‑PDF niet beschadigd is.

**Q: Kan ik ingesloten objecten na invoeging wijzigen?**  
A: Je kunt het Word‑bestand opnieuw openen in Microsoft Word en het OLE‑object bewerken, of de Merger‑code opnieuw uitvoeren met bijgewerkte opties.

## Aanvullende bronnen
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Laatst bijgewerkt:** 2025-12-19  
**Getest met:** GroupDocs.Merger for Java latest version  
**Auteur:** GroupDocs