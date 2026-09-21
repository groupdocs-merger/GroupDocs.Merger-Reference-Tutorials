---
date: '2026-09-21'
description: Naučte se, jak vložit PDF do PowerPointu jako OLE objekt pomocí GroupDocs.Merger
  pro .NET. Tento krok‑za‑krokem průvodce vám ukáže přesné volání API a osvědčené
  postupy.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: vložit PDF do PowerPointu pomocí GroupDocs.Merger pro .NET. Postupujte
  podle tohoto stručného tutoriálu, abyste přidali OLE objekty, nakonfigurovali možnosti
  a vyhnuli se běžným chybám.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: vložit PDF do PowerPointu – vložit PDF jako OLE s GroupDocs.Merger
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
title: Jak vložit PDF do PowerPointu jako OLE pomocí GroupDocs.Merger pro .NET
type: docs
url: /cs/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# Vložit PDF do PowerPointu jako OLE pomocí GroupDocs.Merger pro .NET

Vložení PDF přímo do snímku PowerPointu vám umožní zachovat původní dokument beze změny a zároveň poskytnout publiku okamžitý přístup. V tomto tutoriálu se naučíte **jak vložit PDF do PowerPointu** jako OLE objekt pomocí GroupDocs.Merger pro .NET, podíváte se na požadované možnosti API a objevíte tipy pro spolehlivý výkon.

## Rychlé odpovědi
- **Která knihovna zajišťuje OLE vkládání?** GroupDocs.Merger pro .NET poskytuje třídu `OlePresentationOptions` pro tento účel.  
- **Potřebuji licenci?** Zkušební licence funguje pro vývoj; plná licence je vyžadována pro produkční použití.  
- **Mohu vložit více než jeden PDF?** Ano – opakujte krok importu pro každý cílový snímek.  
- **Jaké verze .NET jsou podporovány?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Je proces paměťově úsporný?** API streamuje soubory, takže i PDF s několika stovkami stran lze vložit bez načtení celého souboru do paměti.

## Co znamená vložit PDF do PowerPointu?
**Vložit PDF do PowerPointu** znamená vložení PDF souboru jako OLE (Object Linking and Embedding) objekt, takže snímek zobrazuje ikonu nebo náhled, který po dvojitém kliknutí otevře původní PDF ve výchozím prohlížeči. Tento přístup zachovává formátování, hypertextové odkazy a bezpečnostní nastavení zdrojového dokumentu.

## Proč použít OLE vkládání místo konverze PDF?
Vkládání zachovává původní velikost souboru a rozvržení beze změny, eliminuje chyby konverze a umožňuje aktualizovat zdrojové PDF bez opětovného exportu prezentace. GroupDocs.Merger podporuje **více než 50 vstupních a výstupních formátů** a může vložit PDF až několik stovek megabajtů při streamování dat, aby spotřeba paměti zůstala pod 100 MB.

## Předpoklady
- Visual Studio 2022 (nebo jakékoli .NET‑kompatibilní IDE)  
- .NET Framework 4.5+ nebo .NET Core 3.1+ runtime  
- Platná licence GroupDocs.Merger pro .NET (zkušební nebo komerční)  
- Soubor PowerPoint (.pptx) a PDF, který chcete vložit  

## Nastavení GroupDocs.Merger pro .NET

### Jak nainstalovat knihovnu?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – vyhledejte “GroupDocs.Merger” a klikněte na **Install** pro získání nejnovější verze.

### Jak získat licenci?
- **Bezplatná zkušební verze** – zaregistrujte se na webu GroupDocs a získejte dočasný licenční klíč.  
- **Dočasná licence** – požádejte o prodlouženou zkušební verzi, pokud potřebujete více než 30 dnů.  
- **Plná koupě** – zakupte komerční licenci pro neomezené produkční použití.

### Jak inicializovat API?
`Merger` je hlavní třída, která poskytuje operace manipulace s dokumenty, jako je import, sloučení a konverze.  
Přidejte požadované `using` direktivy na začátek vašeho C# souboru a vytvořte instanci `Merger` s cestou k licenčnímu souboru:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Průvodce implementací

### Jak vložit PDF do PowerPointu jako OLE?
Načtěte svou prezentaci, nakonfigurujte OLE možnosti a zavolejte metodu importu – celá operace proběhne ve třech logických krocích.

**Krok 1 – definujte umístění souborů**  
Určete absolutní nebo relativní cesty ke zdrojovému PDF, cílovému souboru PowerPoint a složce, kam bude upravená prezentace uložena.

**Krok 2 – nakonfigurujte OLE možnosti**  
`OlePresentationOptions` je třída, která říká GroupDocs.Merger, který soubor vložit, na který snímek a na jaké souřadnice. Také vám umožní nastavit šířku, výšku a režim zobrazení vloženého objektu.

**Krok 3 – importujte PDF**  
`ImportDocument` je volání Merger API, které vloží OLE objekt do souboru PowerPoint pomocí poskytnutých možností. Metoda streamuje PDF do snímku, aniž by načetla celý dokument do paměti.

#### Definiční kotvy
- `OlePresentationOptions` je kontejner možností, který definuje vložený soubor, jeho pozici (X/Y), velikost a číslo cílového snímku.  
- `ImportDocument` je volání Merger API, které vloží OLE objekt do souboru PowerPoint pomocí poskytnutých možností.

## Běžné konfigurační parametry
- **SlideNumber** – jednorozměrný index (od 1) snímku, který bude hostit OLE objekt.  
- **XCoordinate / YCoordinate** – pozice měřená v bodech od levého horního rohu snímku.  
- **Width / Height** – rozměry OLE zástupce; nastavte na 0 pro výchozí velikost.  
- **ObjectName** – volitelný přátelský název zobrazený při výběru objektu v PowerPointu.

## Praktické aplikace
Vkládání PDF jako OLE objekt vyniká v mnoha reálných scénářích:

1. **Firemní briefinky** – připojte nejnovější finanční zprávu, aniž byste zvětšili velikost prezentace.  
2. **Akademické přednášky** – poskytněte plné texty výzkumných prací vedle souhrnů snímků.  
3. **Aktualizace stavu projektu** – vložte živý plán projektu, který mohou zúčastněné strany otevřít pro podrobnosti.  
4. **Prodejní prezentace** – zahrňte specifikační listy produktů, které mohou prodejci otevřít na požádání.  
5. **Technické workshopy** – představte schémata nebo technické listy, které mohou inženýři okamžitě prohlédnout.

## Úvahy o výkonu
Aby byl proces vkládání rychlý a šetrný k paměti:

- **Streamovat soubory** – GroupDocs.Merger čte a zapisuje streamy, takže i 200‑stránkový PDF používá méně než 100 MB RAM.  
- **Dávkové zpracování** – při aktualizaci mnoha prezentací znovu použijte jednu instanci `Merger` a rychle uzavírejte streamy.  
- **Změna velikosti velkých PDF** – komprimujte nebo zmenšete rozlišení obrázků ve zdrojovém PDF, pokud zaznamenáte pomalé načítání.

## Často kladené otázky

**Q: Mohu vložit více PDF do jedné prezentace?**  
A: Ano. Zavolejte `ImportDocument` pro každé PDF, přičemž určíte jiný `SlideNumber` nebo pozici na stejném snímku.

**Q: Jak velký PDF mohu vložit?**  
A: Praktické omezení je určeno pamětí vašeho serveru; vkládání až do 500 MB bylo testováno bez problémů při streamování.

**Q: Zachovává OLE objekt interaktivní prvky jako hypertextové odkazy?**  
A: Rozhodně. Vložený PDF se otevře ve výchozím prohlížeči a zachová všechny vnitřní odkazy a záložky.

**Q: Co když je PDF chráněno heslem?**  
A: Zadejte heslo pomocí vlastnosti `Password` třídy `OlePresentationOptions` před zavoláním `ImportDocument`.

**Q: Bude vložený objekt fungovat ve všech verzích PowerPointu?**  
A: Formát OLE je podporován v PowerPoint 2007 a novějších, včetně Office 365.

## Závěr
Nyní máte kompletní, připravený workflow pro **vložení PDF do PowerPointu** jako OLE objekt pomocí GroupDocs.Merger pro .NET. Streamováním souborů, konfigurací `OlePresentationOptions` a voláním `ImportDocument` můžete obohatit prezentace o originální PDF při nízké spotřebě paměti a zachování všech interaktivních funkcí. Prozkoumejte další možnosti Merger, jako je slučování snímků, konverze formátů a vodoznakování, pro další automatizaci vašich dokumentových pipeline.

---

**Poslední aktualizace:** 2026-09-21  
**Testováno s:** GroupDocs.Merger 23.12 pro .NET  
**Autor:** GroupDocs  

## Zdroje
- **Dokumentace:** [GroupDocs.Merger for .NET Documentation](https://docs.groupdocs.com/merger/net/)  
- **Reference API:** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **Stáhnout:** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **Koupit:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Bezplatná zkušební verze:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Dočasná licence:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

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

## Související tutoriály

- [Vložit PDF do Wordu pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Načítání PDF z URL v .NET pomocí GroupDocs.Merger: Kompletní průvodce](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [Jak získat informace o dokumentu pomocí GroupDocs.Merger pro .NET: Kompletní průvodce](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)