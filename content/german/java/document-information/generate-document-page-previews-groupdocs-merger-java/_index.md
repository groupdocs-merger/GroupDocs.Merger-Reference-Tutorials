---
date: '2026-01-24'
description: Erfahren Sie, wie Sie Dokumente mit GroupDocs.Merger für Java durch das
  Erzeugen von Seitenvorschauen anzeigen können – ein schneller Weg, Seiten in Bilder
  zu konvertieren, um Dokument-Thumbnails zu erstellen.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: Wie man Dokumente mit GroupDocs.Merger für Java vorschaut
type: docs
url: /de/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# Wie man Dokumente mit GroupDocs.Merger für Java vorschaut

Das Erstellen von Seitenvorschauen für Dokumente ist eine leistungsstarke Methode, um **Dokumente schnell vorzuschauen**, den Benutzern einen visuellen Schnappschuss zu geben, ohne die gesamte Datei zu öffnen. In diesem Tutorial lernen Sie, wie Sie diese Vorschauen mit GroupDocs.Merger für Java erzeugen, einer Bibliothek, die das **Konvertieren von Seiten zu Bildern** erleichtert und die **Erstellung von Dokumenten‑Thumbnails** in Ihren Anwendungen unterstützt.

## Schnelle Antworten
- **Was bedeutet „Dokumente vorschauen“?** Erzeugen leichter Bilddarstellungen jeder Seite.  
- **Welches Format wird für Vorschauen verwendet?** Standardmäßig JPEG, aber andere Formate werden unterstützt.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion funktioniert für die Entwicklung; für die Produktion ist eine kostenpflichtige Lizenz erforderlich.  
- **Kann ich den Ausgabepfad anpassen?** Ja, indem Sie Inhalte schnell überfliegen können. Diese Techniksystemen,chnelle Konvertierung** von Seiten zu Bildern, ohne das gesamte Dokument in einer Benutzeroberfläche zu öffnen.  
- **Integrierte Unterstützung** für viele Formate (PDF, DOCX, XLSX usw.).  
- **Erweiterbare API** ermöglicht es Ihnen, zu steuern, wo und wie Vorschaudateien gespeichert werden.  

## Voraussetzungen
- **GroupDocs.Merger für Java** Bibliothek (siehe Installation unten).  
- **JDK 8+** auf Ihrem Rechner installiert.  
- Eine IDE (IntelliJ IDEA, Eclipse, NetBeans) sowie Maven oder Gradle für das Abhängigkeitsmanagement.  

## Einrichtung von GroupDocs.Merger für Java
Fügen Sie die Bibliothek Ihrem Projekt mit dem von Ihnen bevorzugten Build‑Tool hinzu.

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direkter Download:**  
Alternativ können Sie die neueste Version von [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) herunterladen.

### Lizenzbeschaffung
- **Kostenlose Testversion:** Beginnen Sie mit dem Herunterladen einer kostenlosen Testversion, um die Funktionen zu erkunden.  
- **Temporäre Lizenz:** Erhalten Sie eine temporäre Lizenz für erweiterten Zugriff während der Entwicklung.  
- **Kauf:** Für den vollständigen Produktionseinsatz erwerben Sie eine Lizenz bei [GroupDocs](https://purchase.groupdocs.com/buy).

Sobald die Bibliothek hinzugefügt ist, initialisieren Sie sie mit dem Pfad zu dem Dokument, das Sie vorschauen möchten:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Dokumente vorschauen: Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Merger initialisieren und einen PageStreamFactory definieren
Der `PageStreamFactory` gibt der Bibliothek an, wohin jedes Vorschaubild geschrieben werden soll.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### Schritt 2: Vorschauen erzeugen
Rufen Sie die Methode `generatePreview` mit den gerade konfigurierten Optionen auf.

```java
merger.generatePreview(previewOption);
```

### Seiten zu Bildern konvertieren – Benutzerdefinierter PageStreamFactory
Wenn Sie mehr Kontrolle über die Dateibenennung oder den Speicherort benötigen, implementieren Sie Ihre eigene Factory:

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### Hilfsmethoden – Streams verwalten
Diese Hilfsmethoden halten den Code übersichtlich und behandeln Ausnahmen sauber.

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## Erstellung von Dokumenten‑Thumbnails – Praktische Anwendungen
Das Erzeugen von Vorschauen ist besonders nützlich für:

1. **Dokumentenmanagement‑Systeme** – Benutzer können Dateien überfliegen, ohne sie zu öffnen.  
2. **Plattformen zur Inhaltsprüfung** – Schnelle visuelle Kontrollen vor der Genehmigung von Uploads.  
3. **Bildungswerkzeuge** – Studierende können einen Blick auf Vorlesungsfolien oder Buchseiten werfen.  

## Leistungsüberlegungen
- **Streams sofort freigeben**, um Speicher zu sparen.  
- **Vermeiden Sie das Laden ganzer Dokumente** in den Speicher; lassen Sie die Bibliothek das Paging übernehmen.  
- **Verwenden Sie geeignete Bildqualitäts‑Einstellungen**, um Geschwindigkeit und visuelle Treue auszubalancieren.

## Häufig gestellte Fragen

**F: Wofür wird GroupDocs.Merger für Java verwendet?**  
A: Es wird zum effizienten Zusammenführen, Aufteilen und Verwalten von Dokumenten verwendet, einschließlich der Erstellung von Vorschauen.

**F: Wie gehe ich mit Ausnahmen bei Stream‑Operationen um?**  
A: Wickeln Sie die Erstellung und das Schließen von Streams in try‑catch‑Blöcke, wie in den Hilfsmethoden gezeigt.

**F: Kann ich Vorschauen in anderen Formaten als JPEG erzeugen?**  
A: Ja, ändern Sie das `PreviewMode`‑Enum zu PNG, BMP usw., um Ihren Bedürfnissen zu entsprechen.

**F: Was sind häufige Probleme bei der Erstellung von Dokumentenvorschauen?**  
A: Typische Probleme sind falsche Dateipfade und das Nicht‑Schließen von Streams, was zu Speicherlecks führen kann.

**F: Wie kann ich GroupDocs.Merger in andere Systeme integrieren?**  
A: Nutzen Sie die API, um sich mit Datenbanken, Web‑Services oder anderen Java‑Anwendungen zu verbinden und eine nahtlose Workflow‑Automatisierung zu ermöglichen.

## Zusätzliche Ressourcen
- [Dokumentation](https://docs.groupdocs.com/merger/java/)
- [API‑Referenz](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Kauf](https://purchase.groupdocs.com/buy)
- [Kostenlose Testversion](https://releases.groupdocs.com/merger/java/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)
- [Support](https://forum.groupdocs.com/c/merger/)

---

**Zuletzt aktualisiert:** 2026-01-24  
**Getestet mit:** GroupDocs.Merger neueste Version (2025‑latest)  
**Autor:** GroupDocs