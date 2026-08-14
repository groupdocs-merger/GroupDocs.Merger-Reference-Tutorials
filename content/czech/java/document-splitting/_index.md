---
date: 2026-05-22
description: Naučte se, jak vytvářet jednostránkové PDF soubory a rozdělovat PDF pomocí
  GroupDocs.Merger pro Java. Obsahuje podrobné návody krok za krokem pro split pdf
  java a další.
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
title: Vytvořte jednostránkový PDF s GroupDocs.Merger Java
type: docs
url: /cs/java/document-splitting/
weight: 12
---

# Vytvořit jednostránkový PDF s GroupDocs.Merger Java

Pokud potřebujete **vytvořit jednostránkový PDF** soubory z větších dokumentů nebo jednoduše rozdělit PDF na snadněji spravovatelné části, jste na správném místě. Tento průvodce vás provede nejčastějšími scénáři rozdělování – soubory s více stránkami, rozsahy stránek, liché/sudé stránky, rozdělení DOCX a dokonce i rozdělení založené na textu – pomocí výkonné knihovny GroupDocs.Merger pro Java. Na konci tohoto tutoriálu budete přesně vědět, jak tyto techniky integrovat do svých aplikací, zlepšit výkon zpracování dokumentů a udržet svůj kód čistý a udržovatelný.

## Rychlé odpovědi
- **Co znamená „create single page PDF“?** Znamená to extrahování jedné stránky ze zdrojového dokumentu a uložení jako samostatného PDF souboru.  
- **Která knihovna tuto úlohu řeší?** GroupDocs.Merger pro Java poskytuje plynulé API pro všechny operace rozdělování.  
- **Potřebuji licenci?** Dočasná licence funguje pro vývoj; pro produkci je vyžadována plná licence.  
- **Mohu rozdělit PDF na liché a sudé stránky?** Ano – GroupDocs.Merger vám umožní filtrovat stránky podle lichých/sudých čísel.  
- **Je podporováno rozdělení DOCX?** Rozhodně; můžete rozdělit soubory DOCX stránku po stránce nebo podle vlastních rozsahů.  

## Co je „create single page PDF“?
Vytvoření jednostránkového PDF zahrnuje převzetí vícestránkového zdrojového dokumentu (PDF, DOCX, PPTX atd.) a extrahování jediné stránky do samostatného PDF souboru. To je užitečné při generování faktur, certifikátů nebo náhledových obrázků, kde je potřeba pouze konkrétní stránka.

## Proč používat GroupDocs.Merger pro Java?
GroupDocs.Merger pro Java nabízí jednotné, konzistentní API, které pracuje s mnoha formáty dokumentů a zároveň poskytuje vysoký výkon a nízkou spotřebu paměti. Zjednodušuje vývoj tím, že abstrahuje složité zpracování souborů, což vám umožní soustředit se na obchodní logiku místo detailů nízkoúrovňového zpracování.

- **Jednotné API** – Funguje s PDF, DOCX, PPTX, obrázky a mnoha dalšími formáty.  
- **Vysoký výkon** – Optimalizováno pro velké soubory a dávkové operace; dokáže zpracovat dokumenty až do 2 GB, aniž by načítalo celý soubor do paměti.  
- **Jemná kontrola** – Rozdělení podle rozsahu stránek, lichých/sudých stránek nebo vlastních oddělovačů.  
- **Přátelské ke streamům** – Výstup lze uložit do souboru nebo vrátit jako stream pro webové služby.

## Požadavky
- Java 8 nebo novější.  
- GroupDocs.Merger pro Java přidaný do vašeho projektu (Maven/Gradle).  
- Platný (dočasný nebo plný) licenční soubor GroupDocs.

## Jak vytvořit jednostránkový PDF?
Vytvoření jednostránkového PDF pomocí GroupDocs.Merger zahrnuje načtení zdrojového souboru, určení přesné stránky nebo rozsahu, vyvolání operace rozdělení a nakonec uložení výsledku. Tento postup zajišťuje, že původní dokument zůstane nedotčen, zatímco extrahovaná stránka je uložena jako samostatný PDF soubor.

Třída `Merger` je hlavní komponentou, která načítá zdrojové dokumenty a poskytuje funkci rozdělení.

### Krok 1: Inicializace Merger
Třída `Merger` je hlavní komponentou GroupDocs.Merger, která načítá zdrojový dokument a poskytuje operace rozdělení. Vytvořte instanci předáním cesty k souboru nebo vstupního streamu.

### Krok 2: Definujte kritéria rozdělení
Vyberte přesné číslo stránky nebo rozsah, který potřebujete. Pro jednostránkové extrahování zadáte rozsah jako `1‑1`. Když potřebujete **rozdělit pdf podle rozsahu**, můžete předat více rozsahů, např. `1‑5, 6‑10`.

### Krok 3: Proveďte rozdělení
Zavolejte odpovídající metodu `split`. Například `merger.split(new int[]{1})` extrahuje první stránku, zatímco `merger.splitByRange(new int[][]{{1,5},{6,10}})` zpracuje více rozsahů v jednom volání.

### Krok 4: Uložte výsledek
Zapište každý výstup na cestu k souboru nebo jej vraťte jako `java.io.InputStream`. To usnadňuje integraci s webovými API nebo uložení výsledku do cloudového úložiště.

> **Tip:** Při práci s velkými PDF zavolejte `merger.setOptimizeResources(true)` před rozdělením, aby se snížila spotřeba paměti.

## Jak rozdělit PDF soubory v Java na více stránek
Třída `Merger` poskytuje hlavní API pro načítání a manipulaci s PDF soubory. Pro rozdělení PDF na samostatné jednostránkové soubory stačí načíst dokument pomocí instance Merger a zavolat metodu split bez parametrů. Knihovna automaticky vytvoří nový PDF pro každou stránku, zachová původní obsah a metadata, což je ideální pro dávkové zpracování faktur nebo zpráv.

## Jak rozdělit PDF na liché a sudé stránky
Třída `Merger` je hlavní komponentou, která provádí operace rozdělení dokumentů. Když potřebujete pouze liché nebo sudé stránky z PDF, poskytněte seznam požadovaných čísel stránek funkci split. Merger vygeneruje nový dokument obsahující jen tyto stránky, což vám umožní rychle vytvořit samostatné soubory pro obsah s lichými nebo sudými čísly.

## Jak rozdělit soubory DOCX (jak rozdělit docx)
Třída `Merger` také funguje se soubory DOCX. Použijte `splitByPage` k vytvoření jednoho DOCX (nebo PDF) na stránku, nebo jej zkombinujte s `saveAsPdf`, pokud potřebujete výstup ve formátu PDF. To pokrývá workflow **docx to pdf java** konverze v jednom kroku.

## Jak rozdělit dokumenty na více‑stránkové soubory
Třída `Merger` zajišťuje stránkování a vytváření souborů pro operace rozdělení. Pokud chcete rozdělit velký dokument na úseky pevné velikosti, určete počet stránek na výstupní soubor. Merger projde zdroj a vytvoří nové PDF, z nichž každé bude obsahovat definovaný počet stránek, což usnadňuje archivaci, distribuci a paralelní zpracování rozsáhlých dokumentů.

## Dostupné tutoriály

### [Jak rozdělit dokumenty na více‑stránkové soubory pomocí GroupDocs.Merger pro Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Learn how to efficiently split large documents into smaller, multi-page files using GroupDocs.Merger for Java. Optimize document management with ease.

### [Jak rozdělit textový soubor podle řádkových intervalů pomocí GroupDocs.Merger pro Java | Průvodce rozdělováním dokumentů](./split-text-file-line-intervals-groupdocs-merger-java/)
Learn how to split text files into manageable sections using line intervals with GroupDocs.Merger for Java. A comprehensive guide for efficient document handling.

### [Mistrovské rozdělení dokumentů podle rozsahu stránek s GroupDocs.Merger pro Java](./split-documents-page-range-groupdocs-merger-java/)
Learn how to split documents into specific page ranges using GroupDocs.Merger for Java. Streamline document management and apply filters like odd/even pages.

### [Mistrovské rozdělení dokumentů s GroupDocs.Merger&#58; Komplexní průvodce](./master-document-splitting-groupdocs-merger-java/)
Learn how to efficiently split documents into single pages using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

### [Mistrovské rozdělení Java dokumentů s GroupDocs.Merger&#58; Rozdělení stránek DOCX do souborů a streamů](./master-java-document-splitting-groupdocs-merger/)
Learn how to efficiently split DOCX documents into separate pages or streams using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

## Další zdroje

- [Dokumentace GroupDocs.Merger pro Java](https://docs.groupdocs.com/merger/java/)
- [Reference API GroupDocs.Merger pro Java](https://reference.groupdocs.com/merger/java/)
- [Stáhnout GroupDocs.Merger pro Java](https://releases.groupdocs.com/merger/java/)
- [Fórum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Bezplatná podpora](https://forum.groupdocs.com/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)

## Časté problémy a řešení
| Problém | Řešení |
|-------|----------|
| **Přetížení paměti u velkých PDF** | Povolit optimalizaci zdrojů: `merger.setOptimizeResources(true);` |
| **Nesprávná čísla stránek po rozdělení** | Pamatujte, že indexování stránek začíná od 1, ne od 0. |
| **Licence nebyla nalezena** | Ověřte cestu k souboru `GroupDocs.Merger.lic` a ujistěte se, že je zahrnutá v classpath. |
| **Rozdělení DOCX vede k prázdným stránkám** | Zajistěte, aby zdrojový DOCX měl správné zalomení stránek; jinak použijte `splitByParagraph` jako náhradní řešení. |

## Často kladené otázky

**Q: Mohu rozdělit PDF chráněné heslem?**  
A: Ano. Načtěte dokument s parametrem hesla a poté proveďte libovolnou operaci rozdělení jako obvykle.

**Q: Jak rozdělit pouze liché stránky PDF?**  
A: Poskytněte seznam stránek obsahující jen lichá čísla (např. 1,3,5…) metodě `split`.

**Q: Je možné rozdělit DOCX přímo na PDF?**  
A: Rozhodně. Po načtení DOCX zavolejte `saveAsPdf` na každém rozděleném segmentu.

**Q: Jaké formáty GroupDocs.Merger podporuje pro rozdělení?**  
A: PDF, DOCX, PPTX, TXT, HTML a mnoho formátů obrázků (PNG, JPEG atd.).

**Q: Potřebuji samostatnou licenci pro každý typ souboru?**  
A: Ne. Jedna licence GroupDocs.Merger pokrývá všechny podporované formáty.

**Poslední aktualizace:** 2026-05-22  
**Testováno s:** GroupDocs.Merger 23.11 pro Java  
**Autor:** GroupDocs

## Související tutoriály

- [split pdf java: Rozdělení dokumentů s GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Mistrovské rozdělení dokumentů podle rozsahu stránek s GroupDocs.Merger pro Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Efektivní sloučení PDF pomocí GroupDocs.Merger pro Java: Průvodce krok za krokem](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)