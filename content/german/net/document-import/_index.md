---
date: 2026-09-11
description: Erfahren Sie, wie Sie PDF mit GroupDocs.Merger for .NET in Word und andere
  Formate importieren, einschließlich PDF in Word einbetten und PDF-Anhänge in wenigen
  einfachen Schritten hinzufügen.
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: Erfahren Sie, wie Sie PDF mit GroupDocs.Merger for .NET in Word und
  andere Formate importieren, einschließlich PDF in Word einbetten, PDF-Anhänge hinzufügen
  und OLE embedding.
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: Wie man PDF in Word mit GroupDocs.Merger for .NET importiert
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: Wie man PDF in Word mit GroupDocs.Merger for .NET importiert
type: docs
url: /de/net/document-import/
weight: 10
---

# Wie man PDF in Word importiert mit GroupDocs.Merger für .NET

In diesem Leitfaden erfahren Sie, wie Sie **PDF in Word** und andere Dokumenttypen mit GroupDocs.Merger für .NET importieren. Egal, ob Sie ein PDF in eine Word‑Datei einbetten, PDFs an bestehende Dokumente anhängen oder Inhalte zwischen Diagrammen, Präsentationen, Tabellenkalkulationen und Textverarbeitungsdateien verschieben müssen – dieses Tutorial führt Sie durch die gängigsten Szenarien, erklärt, warum sie wichtig sind, und zeigt Ihnen die genauen Schritte, um die Aufgabe schnell zu erledigen.

## Schnelle Antworten
- **Kann ich ein PDF in ein Word-Dokument importieren?** Ja – GroupDocs.Merger ermöglicht das Einbetten eines PDFs als OLE‑Objekt oder als nativen Inhalt in einer .docx‑Datei.  
- **Benötige ich eine separate PDF-Bibliothek?** Nein, das Merger SDK verarbeitet den PDF‑Import ohne zusätzliche Abhängigkeiten.  
- **Welche .NET-Versionen werden unterstützt?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Ist für die Produktion eine Lizenz erforderlich?** Eine kommerzielle Lizenz ist für die Produktion erforderlich; eine kostenlose Testversion ist für die Evaluierung verfügbar.  
- **Wie groß darf ein PDF sein, das ich importieren kann?** Bis zu 500 MB pro Datei werden unterstützt, ohne das gesamte Dokument in den Speicher zu laden.

## Was bedeutet das Importieren von PDF in Word?
PDF‑Import in Word bedeutet, den Inhalt einer PDF‑Datei zu nehmen und ihn in ein Microsoft Word (.docx)‑Dokument zu platzieren, entweder als eingebettetes Objekt oder als konvertierte native Elemente, wobei Layout, Bilder und Textformatierung erhalten bleiben. Der Vorgang kann Textfluss, Bilder, Tabellen und Vektorgrafiken beibehalten und sorgt dafür, dass die resultierende Word‑Datei dem ursprünglichen PDF‑Layout so nahe wie möglich kommt.

## Warum GroupDocs.Merger für diese Aufgabe verwenden?
GroupDocs.Merger unterstützt **30+ Eingabe‑ und Ausgabeformate** und kann Dokumente bis zu **500 MB** verarbeiten, ohne sie vollständig in den RAM zu laden, was den Speicherverbrauch bei serverseitigen Anwendungen reduziert. Die Bibliothek bietet zudem **eingebautes OLE‑Embedding**, sodass Sie PDFs direkt in Word-, Excel‑ oder PowerPoint‑Dateien mit einem einzigen API‑Aufruf anhängen können.

## Voraussetzungen
- .NET‑Entwicklungsumgebung (Visual Studio 2022 oder neuer).  
- GroupDocs.Merger für .NET NuGet‑Paket installiert (`Install-Package GroupDocs.Merger`).  
- Eine gültige GroupDocs.Merger‑Lizenz für den Produktionseinsatz (eine temporäre Lizenz ist für Tests verfügbar).

## Schritt‑für‑Schritt-Anleitung zum Importieren von PDF in Word

### Wie bette ich eine PDF-Datei in ein Word-Dokument ein?
`Merger` ist die Kernklasse des GroupDocs.Merger SDK, die Methoden zur Dokumentmanipulation bereitstellt.  
`Insert` fügt ein Quelldokument oder -objekt an einer angegebenen Position in ein Zieldokument ein.  

Laden Sie das Quell‑PDF mit `Merger` und rufen Sie `Insert` auf, um es in das Ziel‑`.docx` zu platzieren. Der Vorgang wird in zwei Code‑Zeilen ausgeführt und übernimmt automatisch das OLE‑Packaging, sodass das PDF als interaktives Objekt in Word erscheint.

### Wie füge ich PDF-Anhänge zu einer bestehenden Word-Datei hinzu?
`AddAttachment` hängt eine externe Datei an ein Container‑Dokument an und speichert sie im Paket für späteren Zugriff.  

Erstellen Sie eine `Merger`‑Instanz, öffnen Sie das Word‑Dokument und verwenden Sie die `AddAttachment`‑Methode, um das PDF anzuhängen. Der Anhang wird im Word‑Paket gespeichert und kann direkt über den Dialog „Einfügen > Objekt“ des Dokuments geöffnet werden.

### Wie bette ich OLE-Objekte (wie PDFs) in Excel-Tabellen ein?
`InsertOleObject` bettet ein OLE‑Objekt wie ein PDF in eine Tabellenzelle ein und ermöglicht ein interaktives Öffnen aus Excel.  

Verwenden Sie die `InsertOleObject`‑Methode in einer Excel‑Arbeitsmappe. Die Methode akzeptiert den PDF‑Dateipfad und den Zellstandort und fügt das PDF als OLE‑Objekt ein, das durch Doppelklick geöffnet werden kann.

## Häufige Probleme und Lösungen
- **PDF wird nur als Symbol angezeigt:** Stellen Sie sicher, dass die Ziel‑Word‑Datei mit der `.docx`‑Erweiterung gespeichert ist; ältere `.doc`‑Dateien unterstützen keine eingebetteten OLE‑Objekte.  
- **Große PDFs verursachen langsame Importe:** Rufen Sie `MergerSettings.EnableMemoryOptimization = true` vor dem Import auf, um den Speicherverbrauch gering zu halten.  
- **Eingebettetes PDF ist nicht anklickbar:** Stellen Sie sicher, dass die PDF‑Datei nicht passwortgeschützt ist; Merger kann verschlüsselte PDFs nicht einbetten, ohne das Passwort bereitzustellen.

## Häufig gestellte Fragen

**Q: Kann ich nur ausgewählte Seiten eines PDFs in Word importieren?**  
A: Ja – verwenden Sie die `PageRange`‑Option beim Aufruf von `Insert`, um anzugeben, welche Seiten eingebettet werden sollen.

**Q: Bewahrt die Bibliothek Hyperlinks im PDF beim Import?**  
A: Beim Einbetten als OLE‑Objekt bleiben Hyperlinks im PDF‑Viewer funktionsfähig; beim Konvertieren zu nativen Word‑Inhalten werden die meisten Hyperlinks beibehalten.

**Q: Ist es möglich, mehrere PDFs stapelweise in ein einzelnes Word‑Dokument zu importieren?**  
A: Absolut. Durchlaufen Sie Ihre PDF‑Sammlung und rufen Sie für jede Datei `Insert` auf; die Bibliothek fügt sie nacheinander zusammen.

**Q: Was, wenn mein PDF Vektorgrafiken enthält?**  
A: Vektorgrafiken bleiben erhalten, wenn das PDF als OLE‑Objekt eingebettet wird; sie werden bei jeder Zoomstufe scharf dargestellt.

**Q: Funktioniert GroupDocs.Merger in Linux‑Containern?**  
A: Ja – das .NET‑Standard‑Build läuft auf Linux, macOS und Windows ohne native Abhängigkeiten.

## Verfügbare Tutorials

### [Anhänge zu PDFs hinzufügen mit GroupDocs.Merger für .NET: Eine Schritt‑für‑Schritt‑Anleitung](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Lernen Sie, wie Sie PDFs Anhänge hinzufügen mit GroupDocs.Merger für .NET. Dieser Schritt‑für‑Schritt‑Leitfaden behandelt Einrichtung, Implementierung und praktische Anwendungen.

### [PDF als OLE in PowerPoint einbetten mit GroupDocs.Merger für .NET: Eine Schritt‑für‑Schritt‑Anleitung](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Lernen Sie, wie Sie eine PDF‑Datei nahtlos als OLE‑Objekt in Ihre PowerPoint‑Präsentation einbetten mit GroupDocs.Merger für .NET. Folgen Sie diesem umfassenden Leitfaden.

### [PDF in Word einbetten mit GroupDocs.Merger für .NET: Eine Schritt‑für‑Schritt‑Anleitung](./embed-pdf-word-groupdocs-merger-dotnet/)
Lernen Sie, wie Sie ein PDF nahtlos in ein Microsoft Word‑Dokument einbetten mit GroupDocs.Merger für .NET. Optimieren Sie Ihre Dokumente effizient mit dynamischem Inhalt.

### [Wie man OLE‑Objekte in Excel‑Tabellen einbettet mit GroupDocs.Merger für .NET](./embed-ole-objects-groupdocs-merger-net/)
Lernen Sie, wie Sie OLE‑Objekte wie PDFs in Excel‑Tabellen einbetten mit GroupDocs.Merger für .NET, um die Datenpräsentation und Funktionalität zu verbessern.

## Zusätzliche Ressourcen

- [GroupDocs.Merger für .net Dokumentation](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger für .net API‑Referenz](https://reference.groupdocs.com/merger/net/)
- [GroupDocs.Merger für .net herunterladen](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Kostenloser Support](https://forum.groupdocs.com/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

---

**Zuletzt aktualisiert:** 2026-09-11  
**Getestet mit:** GroupDocs.Merger 23.12 für .NET  
**Autor:** GroupDocs

## Verwandte Tutorials

- [PDF in Word einbetten mit GroupDocs.Merger für .NET: Eine Schritt‑für‑Schritt‑Anleitung](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Anhänge zu PDFs hinzufügen mit GroupDocs.Merger für .NET: Eine Schritt‑für‑Schritt‑Anleitung](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [PDF von URL in .NET laden mit GroupDocs.Merger: Ein umfassender Leitfaden](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)