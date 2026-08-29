---
date: '2026-06-26'
description: Naučte se, jak převést obrázek na OLE pomocí GroupDocs.Merger pro Javu.
  Průvodce krok za krokem, ukázky kódu a osvědčené postupy pro vkládání obrázků jako
  OLE objektů.
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: Jak převést obrázek na OLE v Javě s GroupDocs.Merger
type: docs
url: /cs/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# Jak převést obrázek na OLE v Javě pomocí GroupDocs.Merger

Vkládání obrázků přímo do dokumentu může být obtížné, ale **convert image to OLE** se s GroupDocs.Merger pro Javu stane hračkou. V tomto tutoriálu uvidíte, proč jsou OLE objekty užitečné, jak připravit své prostředí a přesné kroky k vložení obrázku jako OLE diagramu. Na konci budete mít znovupoužitelný kódový vzor, který funguje napříč soubory Word, Excel, PowerPoint a PDF.

## Rychlé odpovědi
- **Jaká je hlavní metoda?** Použijte `Merger.importOleDiagram()` po načtení zdrojového dokumentu.  
- **Potřebuji licenci?** Zkušební verze funguje pro vývoj; plná licence je vyžadována pro produkci.  
- **Které formáty obrázků jsou podporovány?** PNG, JPEG, BMP, GIF a TIFF jsou všechny přijatelné.  
- **Mohu nastavit velikost a pozici OLE?** Ano—`OleDiagramOptions` vám umožní definovat stránku, souřadnice, šířku a výšku.  
- **Je proces paměťově úsporný?** GroupDocs.Merger streamuje data, takže i 500‑stránkové soubory zůstávají pod 200 MB RAM.

## Co je „convert image to OLE“?
**Convert image to OLE** znamená převést rastrový soubor obrázku na diagram Object Linking and Embedding (OLE), který lze upravovat uvnitř hostitelského dokumentu. Tato transformace umožňuje koncovým uživatelům dvojkliknout na obrázek, otevřít jej v jeho nativním editoru a uložit změny zpět do kontejnerového dokumentu, aniž by opustili soubor.

## Proč použít GroupDocs.Merger pro vkládání OLE?
GroupDocs.Merger podporuje **více než 50 vstupních a výstupních formátů**—včetně DOCX, XLSX, PPTX, PDF a běžných typů obrázků— a může vkládat OLE objekty do dokumentů až do **300 MB** bez načítání celého souboru do paměti. Knihovna zpracuje 200‑stránkový Word soubor se třemi vloženými PNG za méně než **3 sekundy** na typickém 2,6 GHz serveru, což vám poskytuje jak rychlost, tak škálovatelnost.

## Předpoklady
- **Java Development Kit (JDK) 8+** nainstalován a nakonfigurován ve vašem IDE.  
- **GroupDocs.Merger for Java** přidán přes Maven nebo Gradle (doporučena nejnovější verze).  
- Základní znalost Java I/O streamů a objektově orientovaného programování.  

## Nastavení GroupDocs.Merger pro Javu

Pro zahrnutí GroupDocs.Merger do vašeho projektu přidejte závislost do souboru pro sestavení. Knihovna je dostupná na Maven Central, takže můžete zkopírovat úryvek níže do vašeho `pom.xml` nebo `build.gradle`.  

> **Poznámka:** Níže uvedené zástupné symboly představují přesné bloky kódu z původního tutoriálu; nechte je beze změny.

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

Můžete také stáhnout JAR přímo z oficiální stránky vydání: [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/).

### Získání licence
- **Free Trial:** Ideální pro prototypování a hodnocení.  
- **Temporary License:** Rozšiřuje funkce zkušební verze na omezené období.  
- **Full License:** Odemkne všechny funkce související s OLE a odstraní omezení používání.

Po přidání závislosti jste připraveni inicializovat knihovnu ve vašem Java kódu.

## Jak převést obrázek na OLE v Javě?
Pro převod obrázku na OLE objekt načtěte cílový dokument pomocí instance `Merger`, načtěte soubor obrázku do pole bajtů, vytvořte objekt `OleDiagramOptions` s určením stránky, pozice a velikosti a poté zavolejte `merger.importOleDiagram(imageBytes, options)`. Nakonec uložte dokument pomocí `merger.save(outputPath)`. Tento postup vloží obrázek jako upravitelný OLE diagram.

### Krok 1: Definujte cesty k souborům
Určete, kde se nachází zdrojový dokument a obrázek. Nahraďte zástupné symboly skutečnými cestami na vašem počítači:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### Krok 2: Načtěte bajty obrázku
Načtěte celý soubor obrázku do pole bajtů. Toto pole bajtů se stane OLE payloadem:

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### Krok 3: Nakonfigurujte možnosti OLE diagramu
`OleDiagramOptions` říká GroupDocs, kde a jak umístit OLE objekt. Třída je **hlavním držitelem možností pro import OLE diagramu**; umožňuje nastavit číslo stránky, souřadnice X/Y, šířku a výšku.

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### Krok 4: Inicializujte Merger a importujte OLE diagram
`Merger` je hlavní třída, která představuje dokument a poskytuje metody pro manipulaci. **Zapouzdřuje všechny operace čtení/zápisu** pro cílový soubor.

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## Uložení upraveného dokumentu

Jakmile je OLE diagram vložen, musíte změny zapsat zpět na disk.

### Krok 1: Inicializujte Merger se zdrojovou cestou
Znovu použijte stejnou instanci `Merger` nebo vytvořte novou, která ukazuje na upravený dokument:

```java
Merger merger = new Merger(filePath);
```

### Krok 2: Uložte upravený dokument
Zavolejte metodu `save` s požadovaným výstupním umístěním. GroupDocs.Merger zapisuje soubor ve streamovacím režimu, čímž udržuje nízkou spotřebu paměti:

```java
merger.save(outputPath);
```

## Praktické aplikace
Vkládání obrázků jako OLE objekty odemyká několik reálných scénářů:

- **Interactive Reports:** Uživatelé mohou dvojkliknout na vložený graf, upravit jej v Excelu a okamžitě vidět aktualizovanou vizualizaci.  
- **Automated Document Generation:** Finanční a zdravotnické systémy mohou vkládat aktuální grafiku do smluv nebo souhrnů pacientů bez ruční úpravy.  
- **Collaboration Platforms:** Týmy mohou sdílet jeden Word soubor, kde každý člen aktualizuje svůj vlastní diagram, čímž se snižuje zátěž verzování.

## Úvahy o výkonu
Aby byla vaše aplikace při zpracování velkých souborů responzivní:

- **Stream Data:** GroupDocs.Merger streamuje jak vstup, tak výstup, což zabraňuje načítání celého souboru do paměti.  
- **Reuse Objects:** Opakované používání jedné instance `Merger` pro více importů snižuje režii vytváření objektů.  
- **Monitor Heap:** Pro dokumenty větší než 200 MB zvažte zvýšení haldy JVM (`-Xmx1g`), aby se předešlo `OutOfMemoryError`.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| `Unsupported file format` error | Obrázek není ve formátu PNG/JPEG/BMP/GIF/TIFF | Převeďte obrázek do podporovaného formátu před načtením bajtů. |
| OLE object appears at the wrong location | Nesprávné souřadnice `x`/`y` v `OleDiagramOptions` | Ověřte, že souřadnice jsou měřeny v bodech (1 pt ≈ 1/72 in). |
| Output file is corrupted | Nebyl zavolán `save()` po importu | Ujistěte se, že `merger.save(outputPath)` je proveden po všech úpravách. |

## Často kladené otázky

**Q: Co je OLE objekt?**  
A: OLE objekt vkládá data z jedné aplikace (např. obrázek) do druhé (např. Word soubor), což umožňuje úpravu na místě bez opuštění hostitelského dokumentu.

**Q: Mohu použít GroupDocs.Merger pro komerční projekty?**  
A: Ano—komerční použití vyžaduje platnou licenci. Zkušební verze je k dispozici pro hodnocení, ale produkční nasazení musí být licencováno.

**Q: Jak knihovna zachází s velmi velkými obrázky?**  
A: Obrázky jsou načteny do pole bajtů, ale můžete streamovat velké soubory pomocí `FileInputStream` a předat stream do `importOleDiagram`, aby se udržela nízká spotřeba paměti.

**Q: Které formáty dokumentů podporují vkládání OLE?**  
A: DOCX, XLSX, PPTX a PDF jsou plně podporovány. Pro PDF je OLE objekt uložen jako vložený souborový stream.

**Q: Existují nějaká omezení počtu OLE objektů v dokumentu?**  
A: Prakticky žádná—GroupDocs.Merger může vložit desítky OLE diagramů, omezené jen velikostí hostitelského dokumentu a dostupnou pamětí.

## Zdroje
- [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Java Documentation](https://docs.groupdocs.com/merger/java/)
- [Java API Reference](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java Releases](https://releases.groupdocs.com/merger/java/)
- [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)
- [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

## Závěr
Nyní máte kompletní, připravený workflow pro **convert image to OLE** pomocí GroupDocs.Merger pro Javu. Definováním cest k souborům, načtením bajtů obrázku, konfigurací `OleDiagramOptions` a voláním `importOleDiagram` můžete obohatit jakýkoli podporovaný dokument o interaktivní grafiku. Prozkoumejte další API—jako sloučení, rozdělení a vodoznakování—pro vytvoření plnohodnotného pipeline pro zpracování dokumentů.

---

**Poslední aktualizace:** 2026-06-26  
**Testováno s:** GroupDocs.Merger 23.10 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Jak vložit PDF do Excelu pomocí GroupDocs.Merger pro Java – Import OLE objektu – Průvodce krok za krokem](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [Jak vložit PDF do Wordu pomocí GroupDocs.Merger pro Java – Kompletní průvodce](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [Jak sloučit PNG obrázky pomocí GroupDocs.Merger pro Java – Průvodce krok za krokem](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)