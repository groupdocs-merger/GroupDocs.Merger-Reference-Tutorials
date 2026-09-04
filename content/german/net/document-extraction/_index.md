---
date: 2026-08-31
description: Erfahren Sie, wie Sie bestimmte PDF-Seiten mit GroupDocs.Merger für .NET
  extrahieren. Schritt-für-Schritt-Anleitungen decken Extraktionsszenarien für Word,
  PDF und DOCX ab.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Erfahren Sie, wie Sie bestimmte PDF-Seiten mit GroupDocs.Merger für
  .NET extrahieren. Detaillierte Anleitungen helfen Ihnen, Seiten aus PDF-, Word-
  und DOCX-Dateien effizient zu entnehmen.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Wie man bestimmte PDF-Seiten mit GroupDocs.Merger extrahiert
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Wie man bestimmte PDF-Seiten mit GroupDocs.Merger extrahiert
type: docs
url: /de/net/document-extraction/
weight: 9
---

# Wie man bestimmte Seiten aus PDF mit GroupDocs.Merger extrahiert

Das Extrahieren bestimmter Seiten aus PDF ist ein häufiges Bedürfnis, wenn Sie nur einen Teil eines größeren Dokuments wiederverwenden, teilen oder archivieren müssen. Mit GroupDocs.Merger für .NET können Sie programmgesteuert einzelne Seiten, Seitenbereiche oder benutzerdefinierte Auswahlen aus PDF-, Word- und DOCX-Dateien ohne manuelle Bearbeitung herausziehen. Dieses Tutorial führt Sie durch die Konzepte, Voraussetzungen und den Schritt‑für‑Schritt‑Arbeitsablauf, sodass Sie die Seitenauswahl in jede .NET‑Anwendung integrieren können.

## Schnelle Antworten
- **Was bedeutet “extract specific pages pdf”?** Es bedeutet, einzelne Seiten oder Bereiche aus einem PDF (oder einem anderen unterstützten Format) auszuwählen und sie als ein neues, kleineres Dokument zu speichern.  
- **Welche Formate werden unterstützt?** GroupDocs.Merger unterstützt über 50 Eingabe‑ und Ausgabeformate, darunter PDF, DOCX, PPTX und Bilder.  
- **Brauche ich eine Lizenz?** Eine temporäre Lizenz funktioniert für Tests; für den Produktionseinsatz ist eine Volllizenz erforderlich.  
- **Kann ich große Dateien verarbeiten?** Ja – die Bibliothek verarbeitet Dateien mit mehreren hundert Seiten mittels Streaming und hält den Speicherverbrauch niedrig.  
- **Wird .NET Core unterstützt?** Absolut – die API funktioniert mit .NET Framework 4.6+, .NET Core 3.1+ und .NET 6/7.

## Was ist extract specific pages pdf?
`extract specific pages pdf` bezieht sich auf den Vorgang, eine oder mehrere Seiten aus einem bestehenden PDF (oder einem unterstützten Dokument) zu entnehmen und ein neues PDF zu erstellen, das nur diese Seiten enthält. So können Sie nur die relevanten Abschnitte teilen, während die Originaldatei unverändert bleibt.

## Warum extract specific pages pdf mit GroupDocs.Merger?
GroupDocs.Merger verarbeitet bis zu **50+ Dateiformate** und kann Seiten aus Dokumenten mit **500+ Seiten** in weniger als **2 Sekunden** auf einer typischen Server‑CPU extrahieren. Die API funktioniert, ohne dass Microsoft Office oder Adobe Acrobat installiert sein muss, was die Bereitstellungskomplexität und Lizenzkosten reduziert.

## Voraussetzungen
- .NET 6 SDK (oder .NET Core 3.1 / .NET Framework 4.6+) auf Ihrer Entwicklungsmaschine installiert.  
- Ein gültiges GroupDocs.Merger für .NET NuGet‑Paket (`GroupDocs.Merger`) zu Ihrem Projekt hinzugefügt.  
- (Optional) Eine temporäre oder vollständige Lizenzdatei, falls Sie den Code über den Evaluierungszeitraum hinaus ausführen möchten.

## Wie man extract specific pages pdf in C# mit GroupDocs.Merger
Laden Sie das Quelldokument, geben Sie die gewünschten Seiten an und speichern Sie das Ergebnis. Die Bibliothek abstrahiert alle format‑spezifischen Details, sodass derselbe Code für PDF, DOCX, PPTX und mehr funktioniert.

Laden Sie Ihre Quelldatei und rufen Sie die `Extract`‑Methode mit den gewünschten Seitenzahlen auf. Die `Extract`‑Methode erstellt ein neues Dokument, das nur die angegebenen Seiten enthält. Die Methode gibt ein neues `Document`‑Objekt zurück, das Sie sofort speichern können. Ein `Document`‑Objekt stellt eine In‑Memory‑Darstellung der resultierenden Datei dar.

### Schritt 1: Eine Merger‑Instanz erstellen
Die Klasse `Merger` ist der Einstiegspunkt zum Laden und Manipulieren von Dokumenten. Instanziieren Sie die Klasse `Merger`, indem Sie den Pfad der Quelldatei übergeben. Dieses Objekt repräsentiert das Dokument, mit dem Sie arbeiten werden.

### Schritt 2: Seiten zum Extrahieren angeben
Geben Sie eine Liste von Seitenindizes (1‑basiert) oder einen Bereichs‑String wie `"1-3,5"` an, um der Bibliothek mitzuteilen, welche Seiten beibehalten werden sollen.

### Schritt 3: Das extrahierte Dokument speichern
Rufen Sie `Save` auf dem `Document`‑Objekt auf und geben Sie den Ausgabepfad sowie das gewünschte Format an (z. B. `SaveFormat.Pdf`). `SaveFormat` ist eine Aufzählung, die den Ausgabetyp der Datei festlegt, z. B. PDF. Der Vorgang schreibt eine neue Datei, die nur die ausgewählten Seiten enthält.

## Häufige Probleme und Lösungen
- **Pages are off‑by‑one:** GroupDocs.Merger verwendet 1‑basierte Seitennummerierung. Stellen Sie sicher, dass Ihre Liste bei 1 beginnt, nicht bei 0.  
- **Password‑protected files:** Übergeben Sie das Passwort an den `Merger`‑Konstruktor oder verwenden Sie das `LoadOptions`‑Objekt. `LoadOptions` bietet Einstellungen, die steuern, wie ein Dokument geladen wird, z. B. das Aktivieren des Speichercachings.  
- **Large files cause timeouts:** Aktivieren Sie Streaming, indem Sie `LoadOptions.UseMemoryCache = true` setzen, um den Speicherverbrauch niedrig zu halten.

## Häufig gestellte Fragen

**Q: Kann ich Seiten aus einem Word‑Dokument als PDF extrahieren?**  
A: Ja – derselbe `Extract`‑Aufruf funktioniert für DOCX, und Sie können das Ergebnis direkt als PDF mit `SaveFormat.Pdf` speichern.

**Q: Ist es möglich, nicht‑aufeinanderfolgende Seiten zu extrahieren?**  
A: Absolut. Geben Sie eine kommagetrennte Liste wie `"2,4,7"` oder einen gemischten Bereich `"1-2,5,8-10"` an.

**Q: Unterstützt die Bibliothek verschlüsselte PDFs?**  
A: Ja. Geben Sie das Passwort beim Öffnen des Dokuments an; die API entschlüsselt es automatisch.

**Q: Wie geht GroupDocs.Merger mit Bildern in PDFs um?**  
A: Bilder werden exakt so erhalten, wie sie auf den ausgewählten Seiten erscheinen; es sind keine zusätzlichen Konvertierungsschritte erforderlich.

**Q: Welche .NET‑Versionen werden offiziell unterstützt?**  
A: .NET Framework 4.6+, .NET Core 3.1+ und .NET 5/6/7 werden vollständig unterstützt.

## Verfügbare Tutorials

### [Bestimmte Seiten aus Dokumenten mit GroupDocs.Merger für .NET extrahieren](./extract-pages-groupdocs-merger-net/)
Erfahren Sie, wie Sie mit GroupDocs.Merger für .NET effizient bestimmte Seiten extrahieren können. Ideal für die Verwaltung von Word, PDF und mehr in professionellen Umgebungen.

### [Wie man bestimmte Seiten aus einem Dokument mit GroupDocs.Merger für .NET in C# extrahiert](./extract-pages-groupdocs-merger-dotnet-csharp/)
Erfahren Sie, wie Sie mit diesem umfassenden Leitfaden bestimmte Seiten aus Dokumenten mit GroupDocs.Merger für .NET extrahieren können. Optimieren Sie Ihre Dokumentenverwaltungsaufgaben mühelos.

## Zusätzliche Ressourcen

- [GroupDocs.Merger für .net Dokumentation](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger für .net API‑Referenz](https://reference.groupdocs.com/merger/net/)
- [GroupDocs.Merger für .net herunterladen](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Kostenloser Support](https://forum.groupdocs.com/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

---

**Zuletzt aktualisiert:** 2026-08-31  
**Getestet mit:** GroupDocs.Merger 23.9 for .NET  
**Autor:** GroupDocs

## Verwandte Tutorials

- [Wie man bestimmte PDF‑Seiten mit GroupDocs.Merger für .NET zusammenführt: Ein umfassender Leitfaden](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Wie man bestimmte Seiten aus mehreren Dokumenten mit GroupDocs.Merger für .NET zusammenführt](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [PDF‑Seiten in .NET mit GroupDocs.Merger drehen: Ein Schritt‑für‑Schritt‑Leitfaden](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)