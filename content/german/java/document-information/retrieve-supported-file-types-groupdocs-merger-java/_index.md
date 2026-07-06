---
date: '2026-07-06'
description: Erfahren Sie, wie Sie unterstützte Dateitypen mit GroupDocs.Merger für
  Java abrufen, unterstützte Erweiterungen für Java prüfen und die Liste in Ihren
  Workflow integrieren.
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
title: GroupDocs.Merger unterstützte Formate – Typen in Java abrufen
type: docs
url: /de/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger unterstützte Formate – Typen abrufen in Java

Die Arbeit mit einer großen Vielfalt von Dokumentformaten in Java kann schnell zu einem Kopfzerbrechen werden, wenn Sie nicht wissen, welche Formate Ihre Bibliothek tatsächlich unterstützt. **GroupDocs.Merger unterstützte Formate** bieten Ihnen einen zuverlässigen Referenzpunkt, mit dem Sie Uploads validieren, Laufzeitfehler vermeiden und intelligentere Dokument‑Management‑Pipelines entwerfen können. In diesem Tutorial sehen Sie genau, wie Sie die Liste der unterstützten Dateitypen mit GroupDocs.Merger für Java abrufen, warum das wichtig ist und wie Sie die Informationen in realen Anwendungen integrieren.

### Schnelle Antworten
- **Was bewirkt „unterstützte Dateitypen abrufen“?**  
  Es gibt eine Liste aller Dokumentformate zurück, die GroupDocs.Merger verarbeiten kann.
- **Welche Methode liefert die Liste?**  
  `FileType.getSupportedFileTypes()` aus dem Paket `com.groupdocs.merger.domain`.
- **Benötige ich eine Lizenz, um diese Methode aufzurufen?**  
  Für den Produktionseinsatz ist eine Test- oder Volllizenz erforderlich; die Methode funktioniert im Evaluierungsmodus.
- **Kann ich die Liste auf nur die benötigten Erweiterungen filtern?**  
  Ja – iterieren Sie über die zurückgegebene Liste und behalten Sie die gewünschten Erweiterungen.
- **Ist dieser Vorgang leistungshungrig?**  
  Nein, er liest lediglich eine statische Sammlung, sodass er sofort ausgeführt wird.

## Welche Formate unterstützt GroupDocs.Merger?

GroupDocs.Merger unterstützt **über 70** Eingabe‑ und Ausgabeformate – darunter PDF, DOCX, PPTX, XLSX, HTML und gängige Bildtypen – sodass Sie praktisch jedes Geschäftsdokument verarbeiten können. Die Format‑Tabelle der Bibliothek wird intern als statische Sammlung gespeichert, sodass das Abrufen ein O(1)-Vorgang ist, der in wenigen Millisekunden abgeschlossen ist, selbst auf bescheidener Hardware.

## Wie kann ich unterstützte Erweiterungen in Java prüfen?

Rufen Sie die statische Methode `FileType.getSupportedFileTypes()` auf und durchlaufen Sie anschließend die zurückgegebene Sammlung, um jede Erweiterung zu lesen. Dieser einzeilige Aufruf liefert Ihnen eine sofort einsatzbereite `List<FileType>`, die Sie filtern, anzeigen oder für spätere Validierungen speichern können.

## Warum sollte ich unterstützte Dateitypen vor der Verarbeitung abrufen?

Das genaue Wissen über die Liste der Formate verhindert vermeidbare Ausnahmen, reduziert den Bedarf an defensiver Programmierung und ermöglicht es Ihnen, den Benutzern eine klare Meldung „erlaubte Dateitypen“ anzuzeigen. Es erlaubt zudem den Aufbau dynamischer UI‑Komponenten – wie Dateiauswahl‑Filter – die nur kompatible Erweiterungen anzeigen und so das Gesamterlebnis der Benutzer verbessern.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:
- **Java Development Kit (JDK):** Version 8 oder höher wird empfohlen.  
- **Integrated Development Environment (IDE):** Jede IDE wie IntelliJ IDEA oder Eclipse funktioniert.  
- **GroupDocs.Merger Bibliothek:** Binden Sie diese Bibliothek in Ihre Projektabhängigkeiten ein.  

Vertrautheit mit grundlegenden Java‑Programmierungskonzepten und Erfahrung im Umgang mit Bibliotheken in einer Maven‑ oder Gradle‑Umgebung sind ebenfalls vorteilhaft. Wenn Sie neu mit diesen Tools sind, sollten Sie zunächst deren Dokumentation prüfen.

## Einrichtung von GroupDocs.Merger für Java

Um GroupDocs.Merger für Java zu verwenden, richten Sie die Bibliothek in Ihrem Projekt mithilfe von Maven, Gradle oder durch direkten Download von der offiziellen Website ein.

### Maven-Installation

Add the following dependency to your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle-Installation

Include this line in your `build.gradle` file:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direkter Download

Alternativ laden Sie die neueste Version von [GroupDocs.Merger für Java Releases](https://releases.groupdocs.com/merger/java/).

#### Schritte zum Erwerb einer Lizenz
1. **Kostenlose Testversion:** Beginnen Sie mit einer kostenlosen Testversion, um die Funktionen der Bibliothek zu erkunden.  
2. **Temporäre Lizenz:** Erhalten Sie eine temporäre Lizenz, wenn Sie erweiterten Zugriff ohne Einschränkungen benötigen.  
3. **Kauf:** Erwägen Sie den Kauf einer Volllizenz für den langfristigen Einsatz.

## Grundlegende Initialisierung und Einrichtung

To initialize GroupDocs.Merger in your Java application, import the necessary classes:

```java
import com.groupdocs.merger.domain.FileType;
```

Jetzt gehen wir zur Implementierung der Funktion über, die unterstützte Dateitypen abruft.

## Was ist die Klasse FileType?

Die Klasse `FileType` ist das Kernmodell in GroupDocs.Merger, das ein einzelnes Dokumentformat darstellt und dessen Erweiterung, MIME‑Typ und einen benutzerfreundlichen Anzeigenamen bereitstellt. Sie interagieren mit dieser Klasse, wenn Sie `FileType.getSupportedFileTypes()` aufrufen, um den vollständigen Katalog der Formate zu erhalten.

## Wie ruft man unterstützte Dateitypen ab?

Um die unterstützten Formate abzurufen, rufen Sie einfach die statische Methode `FileType.getSupportedFileTypes()` der GroupDocs.Merger‑Bibliothek auf. Dieser Aufruf liefert eine `List<FileType>` mit allen Formaten, die die Bibliothek verarbeiten kann. Der Vorgang ist leichtgewichtig und kann beim Anwendungsstart oder jederzeit, wenn Sie Dateiuploads validieren müssen, ausgeführt werden.

### Schritt 1: Unterstützte Dateitypen erhalten

First, retrieve the list of supported file types from the `FileType` class:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

Diese Methode gibt eine Liste zurück, die alle Dateitypen enthält, die GroupDocs.Merger unterstützt.

### Schritt 2: Unterstützte Erweiterungen anzeigen

Als Nächstes iterieren Sie über jedes `FileType`‑Objekt und geben dessen Erweiterung aus. Dies ist der Teil, in dem wir **unterstützte Erweiterungen anzeigen** für Entwickler oder End‑benutzer:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

### Schritt 3: Bestätigungsnachricht

Abschließend geben Sie eine Bestätigungsnachricht aus, die den erfolgreichen Abruf anzeigt:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Praktische Anwendungen

Das Verständnis der unterstützten Dateitypen ist für verschiedene Anwendungen entscheidend:
1. **Dokumentenmanagement‑Systeme:** Dokumente automatisch nach ihrem Typ kategorisieren.  
2. **Dateikonvertierungstools:** Vor der Konvertierung von Dateien zwischen Formaten die Kompatibilität sicherstellen.  
3. **Zusammenführungs‑Anwendungen:** Eingabedateien vor dem Zusammenführen validieren, um Fehler zu vermeiden.  

Die Integration mit anderen Systemen – wie Cloud‑Speicher oder Dokumenten‑Verarbeitungs‑Diensten – kann die Funktionalität weiter verbessern.

## Leistungsüberlegungen

Bei der Arbeit mit GroupDocs.Merger in Java beachten Sie folgende Leistungstipps:
- **Speichernutzung optimieren:** Objekte freigeben, wenn sie nicht mehr benötigt werden.  
- **Batch‑Verarbeitung:** Dateien stapelweise verarbeiten, um den Ressourcenverbrauch zu reduzieren.  
- **Asynchrone Vorgänge:** Asynchrone Methoden für nicht blockierende Vorgänge verwenden.

## Häufige Probleme und Lösungen

- **Abhängigkeitsprobleme:** Stellen Sie sicher, dass Maven‑ oder Gradle‑Abhängigkeiten korrekt deklariert sind; Versionskonflikte führen zu class‑not‑found‑Fehlern.  
- **Bibliotheksversion:** Verwenden Sie stets die neueste GroupDocs.Merger‑Version, um von neu hinzugefügten Formaten und Fehlerbehebungen zu profitieren.  
- **Lizenzfehler:** Wenn Lizenzausnahmen auftreten, prüfen Sie, ob die Test‑ oder Dauerlizenzdatei korrekt im Code referenziert wird.

## Häufig gestellte Fragen

**Q: Was ist GroupDocs.Merger für Java?**  
A: Es ist eine Java‑Bibliothek, die das Zusammenführen, Aufteilen und Konvertieren einer breiten Palette von Dokumentformaten ermöglicht, ohne Microsoft Office zu benötigen.

**Q: Wie beginne ich mit GroupDocs.Merger?**  
A: Fügen Sie die Maven‑ oder Gradle‑Abhängigkeit hinzu, erhalten Sie eine Test‑ oder Volllizenz und initialisieren Sie die Bibliothek wie im Einrichtungsabschnitt gezeigt.

**Q: Kann ich GroupDocs.Merger kostenlos nutzen?**  
A: Ja, eine kostenlose Testversion steht für die Evaluierung zur Verfügung; für den Produktionseinsatz ist eine Volllizenz erforderlich.

**Q: Welche Dateitypen unterstützt GroupDocs.Merger?**  
A: Verwenden Sie die Methode `FileType.getSupportedFileTypes()`, um eine Liste von **über 70** unterstützten Formaten abzurufen, darunter PDF, DOCX, PPTX, XLSX, HTML und Bildtypen.

**Q: Wie gehe ich mit nicht unterstützten Dateitypen um?**  
A: Validieren Sie Uploads anhand der unterstützten Liste, bevor Sie sie verarbeiten; lehnen Sie nicht unterstützte Dateien ab oder konvertieren Sie sie frühzeitig, um Laufzeitfehler zu vermeiden.

**Q: Kann ich die Liste filtern, um nur die benötigten Erweiterungen anzuzeigen?**  
A: Ja. Nach dem Aufruf von `getSupportedFileTypes()` iterieren Sie die Liste und behalten nur die gewünschten Erweiterungen.

**Q: Ist eine Lizenz für Entwicklungs‑Builds erforderlich?**  
A: Eine Testlizenz funktioniert für Entwicklung und Tests; für den kommerziellen Produktionseinsatz ist eine Volllizenz erforderlich.

**Q: Beeinflusst diese Methode die Anwendungsstartzeit?**  
A: Nein. Die Liste der unterstützten Dateitypen ist statisch, sodass das Abrufen praktisch sofort erfolgt.

**Q: Wird sich die Liste mit neuen Bibliotheksversionen ändern?**  
A: Neue Versionen können Formate hinzufügen oder entfernen; verwenden Sie stets die neueste Version, um die aktuellste Liste zu erhalten.

## Ressourcen
- [Dokumentation](https://docs.groupdocs.com/merger/java/)
- [API‑Referenz](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Kauf](https://purchase.groupdocs.com/buy)
- [Kostenlose Testversion](https://releases.groupdocs.com/merger/java/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)
- [Support](https://forum.groupdocs.com/c/merger/) 

Nutzen Sie diese Ressourcen gerne für detailliertere Informationen und Unterstützung. Viel Spaß beim Programmieren!

---

**Last Updated:** 2026-07-06  
**Tested With:** GroupDocs.Merger neueste Version (Stand 2026)  
**Author:** GroupDocs  

## Verwandte Tutorials

- [GroupDocs.Merger für Java: Lizenz‑Einrichtung & Datei‑Existenz‑Prüfungs‑Leitfaden](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Lokales Dokument in Java mit GroupDocs.Merger laden – Leitfaden](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Bestimmte Seiten in Java zusammenführen – Dokument‑Zusammenführungs‑Tutorials für GroupDocs.Merger](/merger/java/document-joining/)