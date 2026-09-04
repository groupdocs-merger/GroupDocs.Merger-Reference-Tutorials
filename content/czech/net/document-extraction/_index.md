---
date: 2026-08-31
description: Naučte se, jak extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger
  pro .NET. Průvodci krok za krokem pokrývají scénáře extrakce z Word, PDF a DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Naučte se, jak extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger
  pro .NET. Podrobné návody vám pomohou efektivně vyjmout stránky z PDF, Word a DOCX
  souborů.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Jak extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger
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
title: Jak extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger
type: docs
url: /cs/net/document-extraction/
weight: 9
---

# Jak extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger

Extrahování konkrétních stránek PDF je běžný požadavek, když potřebujete znovu použít, sdílet nebo archivovat jen část většího dokumentu. S GroupDocs.Merger pro .NET můžete programově vyjmout jednotlivé stránky, rozsahy stránek nebo vlastní výběry z PDF, Word a DOCX souborů bez ruční úpravy. Tento tutoriál vás provede koncepty, předpoklady a krok‑za‑krokem pracovním postupem, abyste mohli integrovat extrakci stránek do jakékoli .NET aplikace.

## Rychlé odpovědi
- **Co znamená „extrahovat konkrétní stránky PDF“?** Znamená to výběr jednotlivých stránek nebo rozsahů z PDF (nebo jiného podporovaného formátu) a jejich uložení jako nový, menší dokument.  
- **Jaké formáty jsou podporovány?** GroupDocs.Merger zpracovává více než 50 vstupních a výstupních formátů, včetně PDF, DOCX, PPTX a obrázků.  
- **Potřebuji licenci?** Dočasná licence funguje pro testování; plná licence je vyžadována pro produkční použití.  
- **Mohu zpracovávat velké soubory?** Ano – knihovna zpracovává soubory s mnoha stovkami stránek pomocí streamování, což udržuje nízkou spotřebu paměti.  
- **Je podporován .NET Core?** Rozhodně – API funguje s .NET Framework 4.6+, .NET Core 3.1+ a .NET 6/7.

## Co je extrahování konkrétních stránek PDF?
`extract specific pages pdf` odkazuje na operaci, při které se vezme jedna nebo více stránek z existujícího PDF (nebo podporovaného dokumentu) a vytvoří se nové PDF, které obsahuje jen tyto stránky. To vám umožní sdílet pouze relevantní části a zároveň zachovat původní soubor nedotčený.

## Proč extrahovat konkrétní stránky PDF pomocí GroupDocs.Merger?
GroupDocs.Merger zpracovává až **50+ formátů souborů** a může extrahovat stránky z dokumentů obsahujících **500+ stránek** za méně než **2 sekundy** na typickém serverovém procesoru. API funguje bez nutnosti instalace Microsoft Office nebo Adobe Acrobat, což snižuje složitost nasazení a náklady na licence.

## Předpoklady
- .NET 6 SDK (nebo .NET Core 3.1 / .NET Framework 4.6+) nainstalovaný na vašem vývojovém počítači.  
- Platný NuGet balíček GroupDocs.Merger pro .NET (`GroupDocs.Merger`) přidaný do vašeho projektu.  
- (Volitelné) Dočasný nebo plný licenční soubor, pokud plánujete spouštět kód po vypršení zkušební doby.

## Jak extrahovat konkrétní stránky PDF v C# pomocí GroupDocs.Merger

Načtěte zdrojový dokument, určete stránky, které potřebujete, a uložte výsledek. Knihovna abstrahuje všechny formátově specifické detaily, takže stejný kód funguje pro PDF, DOCX, PPTX a další.

Načtěte svůj zdrojový soubor a zavolejte metodu `Extract` s požadovanými čísly stránek. Metoda `Extract` vytvoří nový dokument obsahující pouze zadané stránky. Metoda vrací nový objekt `Document`, který můžete okamžitě uložit. Objekt `Document` představuje in‑memory reprezentaci výsledného souboru.

### Krok 1: vytvoření instance mergeru
Třída `Merger` je vstupním bodem pro načítání a manipulaci s dokumenty. Vytvořte instanci třídy `Merger` předáním cesty ke zdrojovému souboru. Tento objekt představuje dokument, se kterým budete pracovat.

### Krok 2: určení stránek k extrakci
Poskytněte seznam indexů stránek (číslování od 1) nebo řetězec rozsahu, například `"1-3,5"`, abyste knihovně sdělili, které stránky zachovat.

### Krok 3: uložení extrahovaného dokumentu
Zavolejte `Save` na objektu `Document`, přičemž zadáte výstupní cestu a požadovaný formát (např. `SaveFormat.Pdf`). `SaveFormat` je výčtový typ, který určuje typ výstupního souboru, například PDF. Operace zapíše nový soubor obsahující pouze vybrané stránky.

## Časté problémy a řešení
- **Stránky jsou posunuty o jednu:** GroupDocs.Merger používá číslování stránek od 1. Ujistěte se, že váš seznam začíná na 1, ne na 0.  
- **Soubory chráněné heslem:** Předávejte heslo konstruktoru `Merger` nebo použijte objekt `LoadOptions`. `LoadOptions` poskytuje nastavení, která řídí, jak je dokument načten, např. povolení ukládání do paměti.  
- **Velké soubory způsobují časové limity:** Povolením streamování nastavením `LoadOptions.UseMemoryCache = true` udržujete nízkou spotřebu paměti.

## Často kladené otázky

**Q: Mohu extrahovat stránky z dokumentu Word jako PDF?**  
A: Ano – stejný volání `Extract` funguje pro DOCX a výsledek můžete uložit přímo jako PDF pomocí `SaveFormat.Pdf`.

**Q: Je možné extrahovat nesouvislé stránky?**  
A: Rozhodně. Poskytněte seznam oddělený čárkami, např. `"2,4,7"` nebo smíšený rozsah `"1-2,5,8-10"`.

**Q: Podporuje knihovna šifrované PDF?**  
A: Ano. Zadejte heslo při otevírání dokumentu; API jej automaticky dešifruje.

**Q: Jak GroupDocs.Merger zachází s obrázky uvnitř PDF?**  
A: Obrázky jsou zachovány přesně tak, jak se objevují na vybraných stránkách; nejsou potřeba žádné další kroky převodu.

**Q: Jaké verze .NET jsou oficiálně podporovány?**  
A: .NET Framework 4.6+, .NET Core 3.1+ a .NET 5/6/7 jsou plně podporovány.

## Dostupné tutoriály

### [Extrahovat konkrétní stránky z dokumentů pomocí GroupDocs.Merger pro .NET](./extract-pages-groupdocs-merger-net/)
Naučte se efektivně extrahovat konkrétní stránky pomocí GroupDocs.Merger pro .NET. Ideální pro správu Word, PDF a dalších formátů v profesionálním prostředí.

### [Jak extrahovat konkrétní stránky z dokumentu pomocí GroupDocs.Merger pro .NET v C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Naučte se, jak extrahovat konkrétní stránky z dokumentů pomocí GroupDocs.Merger pro .NET s tímto komplexním průvodcem. Zjednodušte své úkoly správy dokumentů bez námahy.

## Další zdroje

- [Dokumentace GroupDocs.Merger pro .NET](https://docs.groupdocs.com/merger/net/)
- [Reference API GroupDocs.Merger pro .NET](https://reference.groupdocs.com/merger/net/)
- [Stáhnout GroupDocs.Merger pro .NET](https://releases.groupdocs.com/merger/net/)
- [Fórum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Bezplatná podpora](https://forum.groupdocs.com/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-08-31  
**Testováno s:** GroupDocs.Merger 23.9 for .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Jak sloučit konkrétní PDF stránky pomocí GroupDocs.Merger pro .NET: Kompletní průvodce](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Jak sloučit konkrétní stránky z více dokumentů pomocí GroupDocs.Merger pro .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Otáčení PDF stránek v .NET pomocí GroupDocs.Merger: Krok za krokem](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)