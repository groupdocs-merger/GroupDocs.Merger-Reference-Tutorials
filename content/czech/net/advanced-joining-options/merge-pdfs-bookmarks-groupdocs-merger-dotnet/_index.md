---
date: '2026-08-20'
description: Zjistěte, jak sloučit PDF soubory se záložkami pomocí GroupDocs.Merger
  for .NET, včetně nastavení, ukázek kódu a osvědčených postupů pro kombinaci PDF
  dokumentů.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Zjistěte, jak sloučit PDF soubory se záložkami pomocí GroupDocs.Merger
  for .NET. Postupujte podle krok‑za‑krokem kódu pro kombinaci PDF dokumentů při zachování
  navigace.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Jak sloučit PDF soubory se záložkami pomocí GroupDocs.Merger for .NET
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
title: Jak sloučit PDF soubory se záložkami pomocí GroupDocs.Merger for .NET
type: docs
url: /cs/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Jak sloučit PDF soubory se záložkami pomocí GroupDocs.Merger pro .NET

Sloučení několika PDF souborů při zachování jejich původních záložek může ušetřit hodiny ruční reorganizace. V tomto tutoriálu se naučíte, jak **sloučit PDF se záložkami** pomocí GroupDocs.Merger pro .NET, od nastavení projektu až po kompletní, připravený k produkci ukázkový kód.

## Rychlé odpovědi
- **Která knihovna podporuje sloučení zachovávající záložky?** GroupDocs.Merger for .NET.  
- **Mohu sloučit více než dva PDF najednou?** Ano – přidejte tolik zdrojových souborů, kolik potřebujete.  
- **Potřebuji licenci pro vývoj?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována trvalá licence.  
- **Je podporován .NET Core?** Rozhodně – knihovna funguje s .NET Core, .NET 5/6 a s plným .NET Framework.  
- **Jaká je maximální velikost souboru, kterou zvládne?** Až 2 GB na dokument, zpracováno bez načítání celého souboru do paměti.

## Co je sloučení PDF se záložkami?
**Sloučení PDF se záložkami** znamená vzít několik PDF dokumentů a spojit je do jednoho souboru při zachování hierarchie záložek každého zdrojového dokumentu. Výsledné PDF si zachovává původní navigační strukturu, což umožňuje čtenářům přejít přímo na sekce, které pocházejí z jednotlivých souborů, což je nezbytné pro rozsáhlé zprávy nebo sestavené příručky.

## Proč sloučit PDF se záložkami?
Zachování záložek při sloučení PDF zlepšuje navigaci v konsolidovaných dokumentech, umožňuje uživatelům rychle najít konkrétní kapitoly nebo sekce bez procházení celého souboru. GroupDocs.Merger udržuje původní hierarchii osnovy, snižuje úsilí potřebné k ruční reorganizaci a podporuje velké soubory až do 2 GB při minimální spotřebě paměti, což ho činí ideálním pro podnikové workflow.

## Požadavky
- **.NET Core SDK** (3.1 nebo novější) nebo **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** nebo jakékoli IDE, které podporuje vývoj v .NET.  
- Základní znalost C# a povědomí o práci se soubory (file I/O).  

## Nastavení GroupDocs.Merger pro .NET

### Instalace
Přidejte knihovnu do svého projektu pomocí jednoho z následujících příkazů:

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
- Vyhledejte “GroupDocs.Merger” a nainstalujte nejnovější verzi.

### Získání licence
- **Bezplatná zkušební verze:** Stáhněte ze stránky [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Dočasná licence:** Získejte ji prostřednictvím [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Plná licence:** Zakupte na [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Základní inicializace
Třída `Merger` je vstupním bodem pro všechny operace sloučení.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Tento namespace vám poskytuje přístup k úplné sadě funkcí pro manipulaci s PDF.

## Jak sloučit PDF se záložkami v .NET

Načtěte svůj hlavní PDF, nakonfigurujte zpracování záložek, přidejte další soubory a uložte výsledek – vše v několika stručných řádcích kódu.

**Přímá odpověď (40‑70 slov):**  
Vytvořte instanci `Merger` s prvním PDF, povolte `PdfJoinOptions.UseBookmarks`, přidejte každý následující PDF pomocí `Join` a zavolejte `Save` pro zápis sloučeného souboru. Tento přístup zachovává každou původní hierarchii záložek a provádí se v jediném průchodu, čímž minimalizuje spotřebu paměti.

### Krok 1: definujte cesty ke složkám
Nastavte složky pro zdroj a výstup, aby kód mohl najít PDF soubory, které chcete sloučit.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Krok 2: načtěte hlavní PDF
`Merger` představuje hlavní dokument, ke kterému budete přidávat ostatní.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Krok 3: nakonfigurujte možnosti zachování záložek
`PdfJoinOptions` řídí, jak se sloučení chová; příznak `UseBookmarks` říká enginu, aby zachoval existující záložky.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Krok 4: přidejte další PDF
Zavolejte `Join` pro každý další soubor. Knihovna automaticky sloučí jejich stromy záložek pod osnovu hlavního dokumentu.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Krok 5: uložte sloučený PDF
Zadejte výstupní cestu a formát; knihovna zapíše jeden PDF soubor, který zachová všechny položky záložek.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Časté problémy a řešení
- **Chybějící záložky:** Ověřte, že `UseBookmarks = true` v `PdfJoinOptions`.  
- **Chyby cesty:** Používejte `Path.Combine` a před sloučením zkontrolujte existenci souboru.  
- **Velké soubory způsobují špičky v paměti:** Zpracovávejte PDF soubory sekvenčně a po každém uložení uvolněte objekt `Merger`.

## Praktické aplikace
1. **Konsolidace finančních zpráv** – udržujte čtvrtletní sekce okamžitě přístupné pomocí záložek.  
2. **Balíčky studijního materiálu** – sloučte přednáškové PDF při zachování navigace kapitol pro studenty.  
3. **Balíčky projektové dokumentace** – spojte specifikace návrhu, testovací plány a poznámky k vydání do jednoho prohledávatelného souboru.

## Úvahy o výkonu
- Zpracovávejte jeden soubor najednou při sloučení více než 20 PDF, aby byl nízký odběr RAM.  
- Používejte nejnovější .NET runtime (např. .NET 6) pro optimální JIT kompilaci a efektivitu garbage collection.  
- Pro PDF větší než 500 MB povolte režim streamování pomocí `MergerSettings`, aby se zabránilo načítání celého dokumentu do paměti.

## Často kladené otázky

**Q: Co je GroupDocs.Merger?**  
A: GroupDocs.Merger je .NET knihovna, která vám umožní programově sloučit, rozdělit, otočit a jinak manipulovat s PDF a dalšími formáty dokumentů.

**Q: Mohu sloučit více než dva PDF soubory najednou?**  
A: Ano – opakovaně volajte `Join` nebo předávejte kolekci cest k souborům, abyste sloučili libovolný počet PDF v jedné operaci.

**Q: Jak řešit licencování pro produkční použití?**  
A: Získejte trvalou licenci na stránce nákupu GroupDocs; zkušební licence funguje pouze pro hodnocení a vyprší po 30 dnech.

**Q: Můj sloučený PDF neukazuje žádné záložky – co se stalo?**  
A: Ujistěte se, že `PdfJoinOptions.UseBookmarks` je nastaven na `true` a že každý zdrojový PDF skutečně obsahuje záložky před sloučením.

**Q: Je knihovna kompatibilní s .NET Core a .NET Framework?**  
A: Rozhodně – podporuje .NET Core 3.1+, .NET 5/6 a plný .NET Framework 4.6.1+.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/merger/net/)  
- [Reference API](https://reference.groupdocs.com/merger/net/)  
- [Stáhnout GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Koupit licenci](https://purchase.groupdocs.com/buy)  
- [Bezplatná zkušební verze](https://releases.groupdocs.com/merger/net/)  
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)  
- [Fórum podpory](https://forum.groupdocs.com/c/merger/)  

---

**Poslední aktualizace:** 2026-08-20  
**Testováno s:** GroupDocs.Merger 23.11 pro .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Jak sloučit konkrétní PDF stránky pomocí GroupDocs.Merger pro .NET: Kompletní průvodce](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Jak snadno spojit dokumenty pomocí GroupDocs.Merger pro .NET: Kompletní průvodce](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Přidání příloh do PDF pomocí GroupDocs.Merger pro .NET: Krok za krokem](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)