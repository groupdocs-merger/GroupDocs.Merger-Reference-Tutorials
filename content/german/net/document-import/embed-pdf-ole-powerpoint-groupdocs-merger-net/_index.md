---
date: '2026-09-21'
description: Erfahren Sie, wie Sie PDF in PowerPoint als OLE-Objekt mit GroupDocs.Merger
  for .NET einbetten. Diese Schritt‑für‑Schritt‑Anleitung zeigt Ihnen die genauen
  API‑Aufrufe und bewährte Methoden.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: PDF in PowerPoint mit GroupDocs.Merger for .NET einbetten. Folgen
  Sie dieser kompakten Anleitung, um OLE‑Objekte hinzuzufügen, Optionen zu konfigurieren
  und häufige Fallstricke zu vermeiden.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: PDF in PowerPoint einbetten – PDF als OLE mit GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: Wie man PDF in PowerPoint als OLE mit GroupDocs.Merger for .NET einbettet
type: docs
url: /de/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# PDF in PowerPoint als OLE einbetten mit GroupDocs.Merger für .NET

Das direkte Einbetten einer PDF in eine PowerPoint‑Folien ermöglicht es, das Originaldokument unverändert zu lassen und dem Publikum sofortigen Zugriff zu geben. In diesem Tutorial lernen Sie **wie man PDF in PowerPoint einbettet** als OLE‑Objekt mit GroupDocs.Merger für .NET, sehen die erforderlichen API‑Optionen und entdecken Tipps für zuverlässige Leistung.

## Schnelle Antworten
- **Welche Bibliothek übernimmt das OLE‑Einbetten?** GroupDocs.Merger für .NET stellt die Klasse `OlePresentationOptions` für diesen Zweck bereit.  
- **Brauche ich eine Lizenz?** Eine Testlizenz funktioniert für die Entwicklung; eine Volllizenz ist für den Produktionseinsatz erforderlich.  
- **Kann ich mehr als ein PDF einbetten?** Ja – wiederholen Sie den Import‑Schritt für jede Ziel‑Folien.  
- **Welche .NET‑Versionen werden unterstützt?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Ist der Vorgang speichereffizient?** Die API streamt Dateien, sodass selbst PDFs mit mehreren hundert Seiten eingebettet werden können, ohne die gesamte Datei in den Speicher zu laden.

## Was bedeutet PDF in PowerPoint einbetten?
**embed pdf in powerpoint** bedeutet, eine PDF‑Datei als OLE‑Objekt (Object Linking and Embedding) einzufügen, sodass die Folie ein Symbol oder eine Vorschau anzeigt, das beim Doppelklick die Original‑PDF im Standard‑Viewer öffnet. Dieser Ansatz bewahrt die Formatierung, Hyperlinks und Sicherheitseinstellungen des Quelldokuments.

## Warum OLE‑Einbetten statt PDF‑Konvertierung verwenden?
Einbetten bewahrt die ursprüngliche Dateigröße und das Layout, eliminiert Konvertierungsfehler und ermöglicht es, die Quell‑PDF zu aktualisieren, ohne die Präsentation erneut zu exportieren. GroupDocs.Merger unterstützt **mehr als 50 Eingabe‑ und Ausgabeformate** und kann PDFs von mehreren hundert Megabyte einbetten, während Daten gestreamt werden, um den Speicherverbrauch unter 100 MB zu halten.

## Voraussetzungen
- Visual Studio 2022 (oder jede .NET‑kompatible IDE)  
- .NET Framework 4.5+ oder .NET Core 3.1+ Runtime  
- Eine gültige GroupDocs.Merger für .NET Lizenz (Test- oder kommerziell)  
- Eine PowerPoint‑(.pptx)‑Datei und die PDF, die Sie einbetten möchten  

## Einrichtung von GroupDocs.Merger für .NET

### Wie installiere ich die Bibliothek?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – suchen Sie nach „GroupDocs.Merger“ und klicken Sie auf **Install**, um die neueste Version zu erhalten.

### Wie erhalte ich eine Lizenz?
- **Kostenlose Testversion** – melden Sie sich auf der GroupDocs‑Website für einen temporären Lizenzschlüssel an.  
- **Temporäre Lizenz** – beantragen Sie eine erweiterte Testversion, wenn Sie mehr als 30 Tage benötigen.  
- **Vollkauf** – erwerben Sie eine kommerzielle Lizenz für unbegrenzte Produktion.

### Wie initialisiere ich die API?
`Merger` ist die primäre Klasse, die Dokumentmanipulations‑Operationen wie Import, Zusammenführen und Konvertierung bereitstellt.  
Fügen Sie die erforderlichen `using`‑Direktiven am Anfang Ihrer C#‑Datei hinzu und erstellen Sie eine `Merger`‑Instanz mit dem Pfad zur Lizenzdatei:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Implementierungs‑Leitfaden

### Wie PDF in PowerPoint als OLE einbetten?
Laden Sie Ihre Präsentation, konfigurieren Sie die OLE‑Optionen und rufen Sie die Import‑Methode auf – der gesamte Vorgang wird in drei logischen Schritten abgeschlossen.

**Schritt 1 – Dateipfade festlegen**  
Geben Sie die absoluten oder relativen Pfade für die Quell‑PDF, die Ziel‑PowerPoint‑Datei und den Ordner an, in dem die modifizierte Präsentation gespeichert werden soll.

**Schritt 2 – OLE‑Optionen konfigurieren**  
`OlePresentationOptions` ist die Klasse, die GroupDocs.Merger mitteilt, welche Datei eingebettet werden soll, auf welcher Folie und bei welchen Koordinaten. Sie ermöglicht zudem das Festlegen von Breite, Höhe und Anzeigemodus des eingebetteten Objekts.

**Schritt 3 – PDF importieren**  
`ImportDocument` ist der Merger‑API‑Aufruf, der das OLE‑Objekt in die PowerPoint‑Datei einfügt, wobei die übergebenen Optionen verwendet werden. Die Methode streamt die PDF in die Folie, ohne das gesamte Dokument in den Speicher zu laden.

#### Definitionsanker
- `OlePresentationOptions` ist der Optionscontainer, der die eingebettete Datei, ihre Position (X/Y), Größe und Ziel‑Foliennummer definiert.  
- `ImportDocument` ist der Merger‑API‑Aufruf, der das OLE‑Objekt in die PowerPoint‑Datei einfügt, wobei die übergebenen Optionen verwendet werden.

## Häufige Konfigurationsparameter
- **SlideNumber** – der 1‑basierte Index der Folie, die das OLE‑Objekt enthält.  
- **XCoordinate / YCoordinate** – Position gemessen in Punkten vom oberen linken Eck der Folie.  
- **Width / Height** – Abmessungen des OLE‑Platzhalters; auf 0 setzen, um die Standardgröße zu verwenden.  
- **ObjectName** – optionaler freundlicher Name, der angezeigt wird, wenn das Objekt in PowerPoint ausgewählt ist.

## Praktische Anwendungsfälle
Das Einbetten einer PDF als OLE‑Objekt glänzt in vielen realen Szenarien:

1. **Unternehmenspräsentationen** – fügen Sie den neuesten Finanzbericht bei, ohne die Präsentationsgröße zu erhöhen.  
2. **Akademische Vorlesungen** – stellen Sie vollständige Forschungspapiere neben den Folienzusammenfassungen bereit.  
3. **Projektstatus‑Updates** – betten Sie einen Live‑Projektplan ein, den Stakeholder für Details öffnen können.  
4. **Verkaufspräsentationen** – enthalten Sie Produktspezifikationsblätter, die Vertriebsmitarbeiter bei Bedarf öffnen können.  
5. **Technische Workshops** – präsentieren Sie Schaltpläne oder Datenblätter, die Ingenieure sofort prüfen können.

## Leistungsüberlegungen
Um den Einbettungsprozess schnell und speicherschonend zu halten:

- **Dateien streamen** – GroupDocs.Merger liest und schreibt Streams, sodass selbst eine 200‑seitige PDF weniger als 100 MB RAM verbraucht.  
- **Stapelverarbeitung** – beim Aktualisieren vieler Präsentationen verwenden Sie eine einzelne `Merger`‑Instanz erneut und schließen Sie Streams umgehend.  
- **Große PDFs verkleinern** – komprimieren oder reduzieren Sie die Auflösung von Bildern in der Quell‑PDF, wenn Sie langsame Ladezeiten bemerken.

## Häufig gestellte Fragen

**Q: Kann ich mehrere PDFs in eine einzelne Präsentation einbetten?**  
A: Ja. Rufen Sie `ImportDocument` für jede PDF auf und geben Sie eine andere `SlideNumber` oder Position auf derselben Folie an.

**Q: Wie groß darf eine PDF sein, die ich einbetten kann?**  
A: Das praktische Limit wird durch den Speicher Ihres Servers bestimmt; Einbettungen bis zu 500 MB wurden beim Streaming ohne Probleme getestet.

**Q: Behält das OLE‑Objekt interaktive Elemente wie Hyperlinks bei?**  
A: Absolut. Die eingebettete PDF öffnet sich im Standard‑Viewer und bewahrt alle internen Links und Lesezeichen.

**Q: Was ist, wenn die PDF passwortgeschützt ist?**  
A: Geben Sie das Passwort über die `Password`‑Eigenschaft von `OlePresentationOptions` an, bevor Sie `ImportDocument` aufrufen.

**Q: Funktioniert das eingebettete Objekt in allen PowerPoint‑Versionen?**  
A: Das OLE‑Format wird von PowerPoint 2007 und später, einschließlich Office 365, unterstützt.

## Fazit
Sie haben nun einen vollständigen, produktionsbereiten Workflow für **PDF in PowerPoint einbetten** als OLE‑Objekt mit GroupDocs.Merger für .NET. Durch das Streamen von Dateien, das Konfigurieren von `OlePresentationOptions` und das Aufrufen von `ImportDocument` können Sie Präsentationen mit Original‑PDFs anreichern, dabei den Speicherverbrauch gering halten und alle interaktiven Funktionen bewahren. Erkunden Sie weitere Merger‑Funktionen wie das Zusammenführen von Folien, das Konvertieren von Formaten und das Hinzufügen von Wasserzeichen, um Ihre Dokument‑Pipelines weiter zu automatisieren.

---

**Zuletzt aktualisiert:** 2026-09-21  
**Getestet mit:** GroupDocs.Merger 23.12 for .NET  
**Autor:** GroupDocs  

## Ressourcen
- **Dokumentation:** [GroupDocs.Merger für .NET Dokumentation](https://docs.groupdocs.com/merger/net/)  
- **API reference:** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **Download:** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **Purchase:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Free trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Temporary license:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## Verwandte Tutorials

- [Embed PDF in Word Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Loading PDF from URL in .NET Using GroupDocs.Merger: A Comprehensive Guide](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [How to Retrieve Document Information Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)