---
date: '2026-02-06'
description: Leer hoe je een tekstbestand per regel kunt splitsen met GroupDocs.Merger
  voor Java. Een stapsgewijze gids voor efficiënt document‑splitsen in Java‑projecten.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Hoe een bestand per regels splitsen met GroupDocs.Merger voor Java
type: docs
url: /nl/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Hoe een bestand per regels splitsen met GroupDocs.Merger voor Java

Het opdelen van een groot tekstbestand in kleinere, beter hanteerbare stukken **per regels** is een veelvoorkomende behoefte wanneer je ‑ bijvoorbeeld ‑ logbestanden verwerkt, batch‑import van gegevens uitvoert, of lange rapporten herschikt. In deze tutorial leer je precies hoe je **bestand per regels splitst** met GroupDocs.Merger voor Java, zie waarom deze aanpak tijd bespaart, en krijg je een kant‑klaar code‑voorbeeld.

## Snelle antwoorden
- **Wat betekent “bestand per regels splitsen”?** Het maakt afzonderlijke tekstbestanden die elk een gedefinieerd bereik van regelnummers uit het originele document bevatten.  
- **Welke bibliotheek voert de splitsing uit?** GroupDocs.Merger voor Java biedt een eenvoudige API voor splitsen op regelintervallen.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een permanente licentie is vereist voor productiegebruik.  
- **Kan ik in plaats daarvan splitsen op tekenaantal?** Niet direct—gebruik een pre‑processing stap om het bestand te herschikken vóór het splitsen.  
- **Welke Java‑versie wordt ondersteund?** Elke Java 8+ runtime is compatibel.

## Wat betekent “bestand per regels splitsen”?
Een bestand per regels splitsen betekent dat je een enkel tekstdocument neemt en het opdeelt in meerdere bestanden, elk met een specifiek bereik van opeenvolgende regels (bijv. regels 1‑3, 4‑6, enz.). Deze techniek is ideaal voor batchverwerking, parallelle analyse, of gewoon om de leesbaarheid te verbeteren.

## Waarom GroupDocs.Merger voor Java gebruiken?
GroupDocs.Merger abstraheert het low‑level bestand‑I/O werk, zodat je je kunt concentreren op de bedrijfslogica. Het verwerkt grote bestanden efficiënt, ondersteunt vele documentformaten, en biedt een schone, vloeiende API die goed integreert met Maven‑ of Gradle‑builds.

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
Begin met een gratis proefversie om de API te verkennen. Voor productie‑workloads verkrijg je een tijdelijke of volledige licentie via het GroupDocs‑portaal.

## Hoe een tekstbestand per regels splitsen (Java‑implementatie)

Hieronder vind je een beknopte, stap‑voor‑stap walkthrough. Elke stap wordt in eenvoudige taal uitgelegd vóór het code‑blok, zodat je precies weet wat er gebeurt.

### Stap 1: Definieer bron‑ en uitvoer‑paden
Eerst geef je de bibliotheek aan waar je originele bestand zich bevindt en waar de gesplitste fragmenten moeten worden weggeschreven.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Stap 2: Configureer de split‑opties
Maak een `TextSplitOptions`‑instantie aan die de gewenste regelintervallen beschrijft. De array `new int[] { 3, 6 }` vertelt de API om te knippen na regel 3 en regel 6, waardoor twee delen ontstaan: regels 1‑3 en regels 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Stap 3: Initialiseert de Merger en voer de split uit
Instantieer tenslotte `Merger` met het bronbestand en roep `split()` aan met de opties die je zojuist hebt opgebouwd.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Dat is alles! Nadat de oproep is voltooid, vind je twee nieuwe bestanden in `YOUR_OUTPUT_DIRECTORY`, elk met de opgegeven regelbereiken.

## Praktische toepassingen (Waarom dit belangrijk is)
1. **Data‑verwerkingspijplijnen** – Splits enorme logbestanden in kleinere stukken voor parallelle parsing.  
2. **Documentbeheer** – Zet een enkel rapport om in hoofdstuk‑niveau bestanden voor eenvoudigere distributie.  
3. **Inhoudssegmentatie** – Bereid secties van een groot artikel voor voor gerichte publicatieplatformen.

## Prestatie‑tips
- **Stroomlijn I/O** – Geef de voorkeur aan `Files.newBufferedReader` bij het omgaan met zeer grote bestanden om het geheugenverbruik laag te houden.  
- **Sluit bronnen** – Hoewel GroupDocs.Merger het meeste opruimt, voorkomt het expliciet sluiten van aangepaste streams lekken.  
- **Monitor geheugen** – Het splitsen van bestanden van gigabyte‑grootte kan veel geheugen verbruiken; wijs voldoende heap toe (`-Xmx2g` of hoger) indien nodig.

## Veelvoorkomende problemen en oplossingen

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| `OutOfMemoryError` | Groot bronbestand overschrijdt de heap. | Verhoog de JVM‑heap of split met kleinere intervallen. |
| `FileNotFoundException` | Onjuist pad of ontbrekende permissies. | Controleer of `filePath` en `filePathOut` absoluut en schrijfbaar zijn. |
| Lege uitvoerbestanden | Intervalarray dekt niet het hele document. | Zorg ervoor dat het laatste interval eindigt op of voorbij het totale aantal regels. |

## FAQ‑sectie

**Q: Kan ik bestanden splitsen op basis van tekenaantal in plaats van regelnummers?**  
A: Momenteel richt GroupDocs.Merger voor Java zich op regelintervallen. Je kunt echter je tekst vooraf verwerken zodat het gewenste tekenaantal per regel overeenkomt voordat je deze functie gebruikt.

**Q: Is er een limiet aan hoeveel intervallen ik kan opgeven voor het splitsen?**  
A: Er is geen specifieke limiet in de bibliotheek zelf; echter kan de prestaties afnemen bij een buitensporig aantal splitsingen vanwege verhoogde verwerkingsvereisten.

**Q: Hoe ga ik om met fouten tijdens het splitsen van bestanden?**  
A: Implementeer try‑catch‑blokken rond je code om uitzonderingen effectief af te vangen en te beheren. GroupDocs.Merger biedt gedetailleerde foutmeldingen die kunnen helpen bij het oplossen van problemen.

**Q: Ondersteunt de bibliotheek andere tekst‑gebaseerde formaten zoals CSV of TSV?**  
A: Ja, omdat CSV en TSV platte‑tekstbestanden zijn, geldt dezelfde regel‑intervallogica. Behandel ze gewoon als `.txt`‑bestanden in de API.

**Q: Kan ik het splitsen automatiseren voor meerdere bestanden in een map?**  
A: Zeker. Plaats de bovenstaande logica in een lus die itereert over `Files.list(Paths.get("folder"))` en pas dezelfde `TextSplitOptions` toe op elk bestand.

## Bronnen
- **Documentatie:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API‑referentie:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Aankoop en licenties:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Gratis proefversie:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Tijdelijke licentie:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Supportforum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Laatst bijgewerkt:** 2026-02-06  
**Getest met:** GroupDocs.Merger 23.12 voor Java  
**Auteur:** GroupDocs