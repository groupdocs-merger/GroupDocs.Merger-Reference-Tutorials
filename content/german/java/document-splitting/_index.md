---
date: 2026-05-22
description: Erfahren Sie, wie Sie einseitige PDF-Dateien erstellen und PDFs mit GroupDocs.Merger
  für Java teilen. Enthält Schritt‑für‑Schritt‑Anleitungen für split pdf java und
  mehr.
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
title: Einseitige PDF mit GroupDocs.Merger Java erstellen
type: docs
url: /de/java/document-splitting/
weight: 12
---

# Einseitiges PDF mit GroupDocs.Merger Java erstellen

Wenn Sie **einseitige PDF**‑Dateien aus größeren Dokumenten erstellen oder PDFs einfach in handlichere Stücke aufteilen möchten, sind Sie hier genau richtig. Dieser Leitfaden führt Sie durch die gängigsten Aufteilungsszenarien – mehrseitige Dateien, Seitenbereiche, ungerade/gerade Seiten, DOCX‑Aufteilung und sogar textbasierte Aufteilungen – mithilfe der leistungsstarken GroupDocs.Merger‑Bibliothek für Java. Am Ende dieses Tutorials wissen Sie genau, wie Sie diese Techniken in Ihre eigenen Anwendungen integrieren, die Dokumentenverarbeitung verbessern und Ihren Code sauber und wartbar halten.

## Schnelle Antworten
- **Was bedeutet „einseitige PDF erstellen“?** Es bedeutet, eine Seite aus einem Quelldokument zu extrahieren und sie als eigenständige PDF‑Datei zu speichern.  
- **Welche Bibliothek erledigt die Aufgabe?** GroupDocs.Merger für Java bietet eine fluente API für alle Aufteilungs‑Operationen.  
- **Brauche ich eine Lizenz?** Eine temporäre Lizenz funktioniert für die Entwicklung; für die Produktion ist eine Voll‑Lizenz erforderlich.  
- **Kann ich PDF‑Seiten ungerade und gerade aufteilen?** Ja – GroupDocs.Merger ermöglicht das Filtern von Seiten nach ungeraden/geraden Nummern.  
- **Wird das Aufteilen von DOCX unterstützt?** Absolut; Sie können DOCX‑Dateien seitenweise oder nach benutzerdefinierten Bereichen aufteilen.  

## Was bedeutet „einseitige PDF erstellen“?
Das Erstellen einer einseitigen PDF beinhaltet das Entnehmen einer einzelnen Seite aus einem mehrseitigen Quelldokument (PDF, DOCX, PPTX usw.) und das Speichern dieser Seite als eigene PDF‑Datei. Dies ist nützlich für die Erstellung von Rechnungen, Zertifikaten oder Vorschaubildern, bei denen nur eine bestimmte Seite benötigt wird.

## Warum GroupDocs.Merger für Java verwenden?
GroupDocs.Merger für Java bietet eine einheitliche, konsistente API, die viele Dokumentformate verarbeitet und dabei hohe Leistung sowie geringen Speicherverbrauch liefert. Sie vereinfacht die Entwicklung, indem sie komplexe Dateiverarbeitung abstrahiert, sodass Sie sich auf die Geschäftslogik statt auf niedrig‑level Details konzentrieren können.

- **Einheitliche API** – Arbeitet mit PDF, DOCX, PPTX, Bildern und vielen anderen Formaten.  
- **Hohe Leistung** – Optimiert für große Dateien und Batch‑Operationen; sie kann Dokumente bis zu 2 GB verarbeiten, ohne die gesamte Datei in den Speicher zu laden.  
- **Feinkörnige Kontrolle** – Aufteilen nach Seitenbereich, ungeraden/geraden Seiten oder benutzerdefinierten Trennzeichen.  
- **Stream‑freundlich** – Die Ausgabe kann in einer Datei gespeichert oder als Stream für Web‑Services zurückgegeben werden.

## Voraussetzungen
- Java 8 oder neuer.  
- GroupDocs.Merger für Java zu Ihrem Projekt hinzugefügt (Maven/Gradle).  
- Eine gültige (temporäre oder vollständige) GroupDocs‑Lizenzdatei.

## Wie erstelle ich ein einseitiges PDF?
Das Erstellen einer einseitigen PDF mit GroupDocs.Merger umfasst das Laden der Quelldatei, das Festlegen der genauen Seite oder des Bereichs, das Aufrufen der Aufteilungs‑Operation und schließlich das Persistieren des Ergebnisses. Dieser Ablauf stellt sicher, dass das Originaldokument unverändert bleibt, während die extrahierte Seite als eigenständige PDF‑Datei gespeichert wird.

Die Klasse `Merger` ist die Kernkomponente, die Quelldokumente lädt und Aufteilungs‑Funktionalität bereitstellt.

### Schritt 1: Merger initialisieren
Die Klasse `Merger` ist die Kernkomponente von GroupDocs.Merger, die ein Quelldokument lädt und Aufteilungs‑Operationen bereitstellt. Erzeugen Sie eine Instanz, indem Sie den Dateipfad oder einen Input‑Stream übergeben.

### Schritt 2: Split‑Kriterien definieren
Wählen Sie die gewünschte Seitenzahl oder den gewünschten Bereich. Für eine einseitige Extraktion geben Sie einen Bereich wie `1‑1` an. Wenn Sie **PDF nach Bereich aufteilen** möchten, können Sie mehrere Bereiche wie `1‑5, 6‑10` übergeben.

### Schritt 3: Aufteilung ausführen
Rufen Sie die passende `split`‑Methode auf. Zum Beispiel extrahiert `merger.split(new int[]{1})` die erste Seite, während `merger.splitByRange(new int[][]{{1,5},{6,10}})` mehrere Bereiche in einem Aufruf verarbeitet.

### Schritt 4: Ergebnis speichern
Schreiben Sie jede Ausgabe in einen Dateipfad oder geben Sie sie als `java.io.InputStream` zurück. Das erleichtert die Integration in Web‑APIs oder das Speichern des Ergebnisses im Cloud‑Speicher.

> **Pro‑Tipp:** Wenn Sie mit großen PDFs arbeiten, rufen Sie vor dem Aufteilen `merger.setOptimizeResources(true)` auf, um den Speicherverbrauch zu reduzieren.

## Wie PDFs in Java in mehrere Seiten aufteilen
Die Klasse `Merger` stellt die primäre API zum Laden und Manipulieren von PDF‑Dateien bereit. Um ein PDF in separate einseitige Dateien zu teilen, laden Sie das Dokument einfach mit der Merger‑Instanz und rufen die split‑Methode ohne Parameter auf. Die Bibliothek erstellt automatisch ein neues PDF für jede Seite, wobei Inhalt und Metadaten erhalten bleiben – ideal für die Batch‑Verarbeitung von Rechnungen oder Berichten.

## Wie PDFs nach ungeraden/geraden Seiten aufteilen
Die Klasse `Merger` ist die Kernkomponente, die Aufteilungs‑Operationen an Dokumenten ausführt. Wenn Sie nur ungerade oder gerade Seiten aus einem PDF benötigen, übergeben Sie eine Liste der gewünschten Seitenzahlen an die split‑Funktion. Der Merger erzeugt ein neues Dokument, das ausschließlich diese Seiten enthält, sodass Sie schnell separate Dateien für ungerade bzw. gerade Inhalte erstellen können.

## Wie DOCX‑Dateien aufteilen (wie man DOCX aufteilt)
Die Klasse `Merger` arbeitet ebenfalls mit DOCX‑Dateien. Verwenden Sie `splitByPage`, um pro Seite ein DOCX (oder PDF) zu erzeugen, oder kombinieren Sie es mit `saveAsPdf`, wenn Sie PDF‑Ausgabe benötigen. Damit wird der **docx to pdf java**‑Konvertierungs‑Workflow in einem Schritt abgedeckt.

## Wie Dokumente in mehrseitige Dateien aufteilen
Die Klasse `Merger` übernimmt die Seitennummerierung und Dateierstellung für Aufteilungs‑Operationen. Wenn Sie ein großes Dokument in gleichgroße Stücke aufteilen möchten, geben Sie die Anzahl der Seiten pro Ausgabedatei an. Der Merger iteriert durch die Quelle und erstellt neue PDFs, die jeweils die definierte Seitenzahl enthalten, was die Archivierung, Verteilung und parallele Verarbeitung umfangreicher Dokumente vereinfacht.

## Verfügbare Tutorials

### [Wie Dokumente in mehrseitige Dateien mit GroupDocs.Merger für Java aufteilen](./split-documents-multi-page-files-java-groupdocs-merger/)
Erfahren Sie, wie Sie große Dokumente effizient in kleinere, mehrseitige Dateien mit GroupDocs.Merger für Java aufteilen. Optimieren Sie die Dokumentenverwaltung mühelos.

### [Wie man eine Textdatei nach Zeilenintervallen mit GroupDocs.Merger für Java aufteilt | Dokumenten‑Aufteilungs‑Leitfaden](./split-text-file-line-intervals-groupdocs-merger-java/)
Erfahren Sie, wie Sie Textdateien mit Zeilenintervallen in handhabbare Abschnitte aufteilen, mithilfe von GroupDocs.Merger für Java. Ein umfassender Leitfaden für effiziente Dokumentenverarbeitung.

### [Dokumentaufteilung nach Seitenbereich mit GroupDocs.Merger für Java](./split-documents-page-range-groupdocs-merger-java/)
Erfahren Sie, wie Sie Dokumente mit GroupDocs.Merger für Java in bestimmte Seitenbereiche aufteilen. Optimieren Sie die Dokumentenverwaltung und wenden Sie Filter wie ungerade/gerade Seiten an.

### [Dokumentaufteilung mit GroupDocs.Merger: Ein umfassender Leitfaden](./master-document-splitting-groupdocs-merger-java/)
Erfahren Sie, wie Sie Dokumente effizient in einzelne Seiten mit GroupDocs.Merger für Java aufteilen. Dieser Leitfaden behandelt Einrichtung, Implementierung und praktische Anwendungen.

### [Java‑Dokumentaufteilung mit GroupDocs.Merger: DOCX‑Seiten in Dateien und Streams aufteilen](./master-java-document-splitting-groupdocs-merger/)
Erfahren Sie, wie Sie DOCX‑Dokumente effizient in separate Seiten oder Streams mit GroupDocs.Merger für Java aufteilen. Dieser Leitfaden behandelt Einrichtung, Implementierung und praktische Anwendungen.

## Zusätzliche Ressourcen

- [GroupDocs.Merger für Java Dokumentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger für Java API‑Referenz](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger für Java herunterladen](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Kostenloser Support](https://forum.groupdocs.com/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

## Häufige Probleme und Lösungen

| Problem | Lösung |
|-------|----------|
| **Speicherüberlastung bei großen PDFs** | Ressourcenoptimierung aktivieren: `merger.setOptimizeResources(true);` |
| **Falsche Seitenzahlen nach dem Aufteilen** | Beachten Sie, dass die Seitennummerierung bei 1 beginnt, nicht bei 0. |
| **Lizenz nicht gefunden** | Überprüfen Sie den Pfad zu Ihrer `GroupDocs.Merger.lic`‑Datei und stellen Sie sicher, dass sie im Klassenpfad enthalten ist. |
| **Aufteilen von DOCX führt zu leeren Seiten** | Stellen Sie sicher, dass das Quell‑DOCX korrekte Seitenumbrüche enthält; andernfalls verwenden Sie `splitByParagraph` als Alternative. |

## Häufig gestellte Fragen

**F: Kann ich ein passwortgeschütztes PDF aufteilen?**  
A: Ja. Laden Sie das Dokument mit dem Passwort‑Parameter und führen Sie anschließend jede Aufteilungs‑Operation wie gewohnt aus.

**F: Wie teile ich nur die ungeraden Seiten eines PDFs?**  
A: Übergeben Sie eine Seitenliste, die nur ungerade Zahlen enthält (z. B. 1,3,5…) an die `split`‑Methode.

**F: Ist es möglich, ein DOCX direkt in PDFs aufzuteilen?**  
A: Absolut. Nach dem Laden des DOCX rufen Sie `saveAsPdf` für jedes aufgeteilte Segment auf.

**F: Welche Formate unterstützt GroupDocs.Merger zum Aufteilen?**  
A: PDF, DOCX, PPTX, TXT, HTML und viele Bildformate (PNG, JPEG usw.).

**F: Benötige ich für jeden Dateityp eine separate Lizenz?**  
A: Nein. Eine einzige GroupDocs.Merger‑Lizenz deckt alle unterstützten Formate ab.

---

**Zuletzt aktualisiert:** 2026-05-22  
**Getestet mit:** GroupDocs.Merger 23.11 für Java  
**Autor:** GroupDocs

## Verwandte Tutorials

- [split pdf java: Dokumentaufteilung mit GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Dokumentaufteilung nach Seitenbereich mit GroupDocs.Merger für Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [PDFs effizient zusammenführen mit GroupDocs.Merger für Java: Eine Schritt‑für‑Schritt‑Anleitung](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)