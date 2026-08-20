---
date: '2026-08-20'
description: Erfahren Sie, wie Sie PDFs mit Lesezeichen mithilfe von GroupDocs.Merger
  für .NET zusammenführen, einschließlich Einrichtung, Codebeispielen und bewährten
  Methoden für das Kombinieren von PDF-Dokumenten.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Erfahren Sie, wie Sie PDFs mit Lesezeichen mithilfe von GroupDocs.Merger
  für .NET zusammenführen. Folgen Sie dem Schritt‑für‑Schritt‑Code, um PDF-Dokumente
  zu kombinieren und dabei die Navigation beizubehalten.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: PDFs mit Lesezeichen mithilfe von GroupDocs.Merger für .NET zusammenführen
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: PDFs mit Lesezeichen mithilfe von GroupDocs.Merger für .NET zusammenführen
type: docs
url: /de/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Wie man PDFs mit Lesezeichen mithilfe von GroupDocs.Merger für .NET zusammenführt

Das Zusammenführen mehrerer PDF‑Dateien bei gleichzeitiger Beibehaltung ihrer ursprünglichen Lesezeichen kann Ihnen Stunden manueller Neuorganisation ersparen. In diesem Tutorial lernen Sie, wie Sie **PDFs mit Lesezeichen zusammenführen** mit GroupDocs.Merger für .NET, von der Projektkonfiguration bis zu einem vollständigen, produktionsbereiten Code‑Beispiel.

## Schnelle Antworten
- **Welche Bibliothek unterstützt das Zusammenführen unter Beibehaltung von Lesezeichen?** GroupDocs.Merger für .NET.  
- **Kann ich mehr als zwei PDFs gleichzeitig zusammenführen?** Ja – fügen Sie so viele Quelldateien hinzu, wie Sie benötigen.  
- **Benötige ich eine Lizenz für die Entwicklung?** Eine kostenlose Testversion funktioniert für Tests; für die Produktion ist eine permanente Lizenz erforderlich.  
- **Wird .NET Core unterstützt?** Absolut – die Bibliothek funktioniert mit .NET Core, .NET 5/6 und dem vollständigen .NET Framework.  
- **Wie groß ist die maximale Dateigröße, die sie verarbeiten kann?** Bis zu 2 GB pro Dokument, verarbeitet, ohne die gesamte Datei in den Speicher zu laden.

## Was ist das Zusammenführen von PDFs mit Lesezeichen?
**Das Zusammenführen von PDFs mit Lesezeichen** bedeutet, mehrere PDF‑Dokumente zu einer einzigen Datei zu kombinieren, wobei die Lesezeichen‑Hierarchie jedes Quelldokuments erhalten bleibt. Das resultierende PDF bewahrt die ursprüngliche Navigationsstruktur, sodass Leser direkt zu den Abschnitten springen können, die aus den einzelnen Dateien stammen – ein Muss für umfangreiche Berichte oder zusammengestellte Handbücher.

## Warum PDFs mit Lesezeichen zusammenführen?
Das Beibehalten von Lesezeichen beim Zusammenführen von PDFs verbessert die Navigation in konsolidierten Dokumenten, sodass Benutzer schnell bestimmte Kapitel oder Abschnitte finden können, ohne das gesamte File zu scrollen. GroupDocs.Merger erhält die ursprüngliche Outline‑Hierarchie, reduziert manuellen Aufwand und unterstützt Dateien bis zu 2 GB bei minimalem Speicherverbrauch, was es ideal für Unternehmens‑Workflows macht.

## Voraussetzungen
- **.NET Core SDK** (3.1 oder später) oder **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** oder jede IDE, die .NET‑Entwicklung unterstützt.  
- Grundkenntnisse in C# und Vertrautheit mit Datei‑I/O.  

## Einrichtung von GroupDocs.Merger für .NET

### Installation
Fügen Sie die Bibliothek Ihrem Projekt mit einem der folgenden Befehle hinzu:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Suchen Sie nach „GroupDocs.Merger“ und installieren Sie die neueste Version.

### Lizenzbeschaffung
- **Kostenlose Testversion:** Download von der [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) Seite.  
- **Temporäre Lizenz:** Erhalten Sie eine über die [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Vollständige Lizenz:** Kauf über die [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Grundlegende Initialisierung
Die `Merger`‑Klasse ist der Einstiegspunkt für alle Zusammenführungs‑Operationen.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Dieser Namespace gibt Ihnen Zugriff auf das komplette Set an PDF‑Manipulations‑Funktionen.

## Wie man PDFs mit Lesezeichen in .NET zusammenführt

Laden Sie Ihr primäres PDF, konfigurieren Sie die Lesezeichen‑Verarbeitung, fügen Sie weitere Dateien hinzu und speichern Sie das Ergebnis – alles in wenigen prägnanten Code‑Zeilen.

**Direkte Antwort (40‑70 Wörter):**  
Erstellen Sie eine `Merger`‑Instanz mit dem ersten PDF, aktivieren Sie `PdfJoinOptions.UseBookmarks`, fügen Sie jedes nachfolgende PDF über `Join` hinzu und rufen Sie `Save` auf, um die kombinierte Datei zu schreiben. Dieser Ansatz bewahrt jede ursprüngliche Lesezeichen‑Hierarchie und läuft in einem einzigen Durchlauf, wodurch der Speicherverbrauch minimiert wird.

### Schritt 1: Verzeichnis‑Pfade definieren
Richten Sie Quell‑ und Ausgabeverzeichnisse ein, damit der Code die zu merge‑enden PDFs finden kann.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Schritt 2: Primäres PDF laden
`Merger` repräsentiert das Hauptdokument, dem Sie weitere hinzufügen werden.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code zum Zusammenführen zusätzlicher Dateien kommt hier hin.
   }
   ```  
```  

### Schritt 3: Optionen zum Beibehalten von Lesezeichen konfigurieren
`PdfJoinOptions` steuert das Merge‑Verhalten; das Flag `UseBookmarks` weist die Engine an, vorhandene Lesezeichen zu erhalten.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Schritt 4: Weitere PDFs hinzufügen
Rufen Sie `Join` für jede zusätzliche Datei auf. Die Bibliothek fügt deren Lesezeichen‑Bäume automatisch unter dem Outline‑Baum des Hauptdokuments ein.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Schritt 5: Zusammengeführtes PDF speichern
Geben Sie den Ausgabepfad und das Format an; die Bibliothek schreibt ein einzelnes PDF, das alle Lesezeichen‑Einträge beibehält.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Häufige Probleme und Lösungen
- **Fehlende Lesezeichen:** Überprüfen Sie `UseBookmarks = true` in `PdfJoinOptions`.  
- **Pfad‑Fehler:** Verwenden Sie `Path.Combine` und prüfen Sie die Dateiexistenz vor dem Zusammenführen.  
- **Große Dateien verursachen Speicher‑Spitzen:** Verarbeiten Sie PDFs sequenziell und entsorgen Sie das `Merger`‑Objekt nach jedem Speichern.

## Praktische Anwendungen
1. **Konsolidierung von Finanzberichten** – Quartalsabschnitte sofort über Lesezeichen erreichbar.  
2. **Kursmaterial‑Pakete** – Vorlesungs‑PDFs zusammenführen und die Kapitel‑Navigation für Studierende erhalten.  
3. **Projekt‑Dokumentations‑Pakete** – Design‑Spezifikationen, Testpläne und Release‑Notes zu einer einzigen durchsuchbaren Datei kombinieren.

## Leistungsüberlegungen
- Verarbeiten Sie jeweils eine Datei, wenn Sie mehr als 20 PDFs zusammenführen, um den RAM‑Verbrauch gering zu halten.  
- Verwenden Sie die neueste .NET‑Runtime (z. B. .NET 6) für optimale JIT‑Kompilierung und Garbage‑Collection‑Effizienz.  
- Für PDFs größer als 500 MB aktivieren Sie den Streaming‑Modus über `MergerSettings`, um das Laden des gesamten Dokuments in den Speicher zu vermeiden.

## Häufig gestellte Fragen

**Q: Was ist GroupDocs.Merger?**  
A: GroupDocs.Merger ist eine .NET‑Bibliothek, mit der Sie PDFs und andere Dokumentformate programmgesteuert zusammenführen, teilen, drehen und anderweitig manipulieren können.

**Q: Kann ich mehr als zwei PDF‑Dateien gleichzeitig zusammenführen?**  
A: Ja – rufen Sie `Join` wiederholt auf oder übergeben Sie eine Sammlung von Dateipfaden, um beliebig viele PDFs in einem Vorgang zu merge‑en.

**Q: Wie handhabe ich die Lizenzierung für den Produktionseinsatz?**  
A: Erwerben Sie eine permanente Lizenz über die GroupDocs‑Kaufseite; die Testlizenz funktioniert nur für Evaluierungen und läuft nach 30 Tagen ab.

**Q: Mein zusammengeführtes PDF zeigt keine Lesezeichen – was ist schiefgelaufen?**  
A: Stellen Sie sicher, dass `PdfJoinOptions.UseBookmarks` auf `true` gesetzt ist und dass jedes Quell‑PDF tatsächlich Lesezeichen enthält, bevor es zusammengeführt wird.

**Q: Ist die Bibliothek mit .NET Core und .NET Framework kompatibel?**  
A: Absolut – sie unterstützt .NET Core 3.1+, .NET 5/6 und das vollständige .NET Framework 4.6.1+.

## Ressourcen
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**Zuletzt aktualisiert:** 2026-08-20  
**Getestet mit:** GroupDocs.Merger 23.11 für .NET  
**Autor:** GroupDocs

## Verwandte Tutorials

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)