---
date: 2026-09-11
description: Zjistěte, jak importovat PDF do Wordu a dalších formátů pomocí GroupDocs.Merger
  for .NET, včetně vložení PDF do Wordu a přidání PDF příloh během několika jednoduchých
  kroků.
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: Zjistěte, jak importovat PDF do Wordu a dalších formátů pomocí GroupDocs.Merger
  for .NET, zahrnující vložení PDF do Wordu, přidání PDF příloh a OLE vložení.
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: Jak importovat PDF do Wordu pomocí GroupDocs.Merger for .NET
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
title: Jak importovat PDF do Wordu pomocí GroupDocs.Merger for .NET
type: docs
url: /cs/net/document-import/
weight: 10
---

# Jak importovat PDF do Wordu pomocí GroupDocs.Merger pro .NET

V tomto průvodci se dozvíte, jak **importovat PDF do Wordu** a dalších typů dokumentů pomocí GroupDocs.Merger pro .NET. Ať už potřebujete vložit PDF do souboru Word, připojit PDF k existujícím dokumentům nebo přesunout obsah mezi diagramy, prezentacemi, tabulkovými kalkulátory a textovými soubory, tento tutoriál vás provede nejčastějšími scénáři, vysvětlí, proč jsou důležité, a ukáže vám přesné kroky k rychlému dokončení úkolu.

## Rychlé odpovědi
- **Mohu importovat PDF do dokumentu Word?** Ano – GroupDocs.Merger vám umožní vložit PDF jako OLE objekt nebo jako nativní obsah v souboru .docx.  
- **Potřebuji samostatnou PDF knihovnu?** Ne, Merger SDK zpracovává import PDF bez dalších závislostí.  
- **Které verze .NET jsou podporovány?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Je pro výrobu vyžadována licence?** Pro výrobu je vyžadována komerční licence; pro hodnocení je k dispozici bezplatná zkušební verze.  
- **Jak velký PDF mohu importovat?** Podporováno je až 500 MB na soubor bez načítání celého dokumentu do paměti.

## Co je import PDF do Wordu?
Import PDF do Wordu znamená převzít obsah PDF souboru a umístit jej do dokumentu Microsoft Word (.docx), buď jako vložený objekt, nebo jako převedené nativní prvky, přičemž zachovává rozvržení, obrázky a formátování textu. Proces může zachovat tok textu, obrázky, tabulky a vektorovou grafiku, což zajišťuje, že výsledný Word soubor vypadá co nejblíže původnímu rozvržení PDF.

## Proč použít GroupDocs.Merger pro tento úkol?
GroupDocs.Merger podporuje **více než 30 vstupních a výstupních formátů** a může zpracovávat dokumenty až do **500 MB** bez úplného načtení do RAM, což snižuje zatížení paměti u serverových aplikací. Knihovna také poskytuje **vestavěné vkládání OLE**, což vám umožní připojit PDF přímo k souborům Word, Excel nebo PowerPoint jedním voláním API.

## Předpoklady
- .NET development environment (Visual Studio 2022 nebo novější).  
- GroupDocs.Merger for .NET NuGet package installed (`Install-Package GroupDocs.Merger`).  
- Platná licence GroupDocs.Merger pro produkční použití (dočasná licence je k dispozici pro testování).

## Jak importovat PDF do Wordu krok za krokem

### Jak vložit PDF soubor do dokumentu Word?
`Merger` je hlavní třída SDK GroupDocs.Merger, která poskytuje metody pro manipulaci s dokumenty.  
`Insert` vloží zdrojový dokument nebo objekt do cílového dokumentu na určenou pozici.

Načtěte zdrojové PDF pomocí `Merger` a zavolejte `Insert`, aby se umístilo do cílového `.docx`. Operace je provedena ve dvou řádcích kódu a automaticky zpracovává OLE balíčkování, takže PDF se zobrazí jako interaktivní objekt ve Wordu.

### Jak přidat PDF přílohy do existujícího souboru Word?
`AddAttachment` připojí externí soubor k dokumentu kontejneru a uloží jej do balíčku pro pozdější načtení.

Vytvořte instanci `Merger`, otevřete dokument Word a použijte metodu `AddAttachment` k připojení PDF. Příloha je uložena uvnitř balíčku Word a může být otevřena přímo z dialogu dokumentu „Insert > Object“.

### Jak vložit OLE objekty (např. PDF) do tabulek Excel?
`InsertOleObject` vloží OLE objekt, například PDF, do buňky tabulky, což umožňuje interaktivní otevření z Excelu.

Použijte metodu `InsertOleObject` na sešitu Excel. Metoda přijímá cestu k PDF souboru a umístění buňky, vloží PDF jako OLE objekt, který lze dvojklikem otevřít.

## Časté problémy a řešení
- **PDF se zobrazuje pouze jako ikona:** Ujistěte se, že cílový soubor Word je uložen s příponou `.docx`; starší soubory `.doc` nepodporují vložené OLE objekty.  
- **Velké PDF způsobují pomalý import:** Zavolejte `MergerSettings.EnableMemoryOptimization = true` před importem, aby se udržovalo nízké využití paměti.  
- **Vložené PDF není klikatelné:** Ověřte, že PDF soubor není chráněn heslem; Merger nemůže vložit šifrované PDF bez zadání hesla.

## Často kladené otázky

**Q: Mohu importovat pouze vybrané stránky PDF do Wordu?**  
A: Ano – použijte možnost `PageRange` při volání `Insert`, abyste určili, které stránky vložit.

**Q: Zachovává knihovna hypertextové odkazy v PDF při importu?**  
A: Při vkládání jako OLE objekt hypertextové odkazy zůstávají funkční v prohlížeči PDF; při konverzi na nativní obsah Wordu je většina hypertextových odkazů zachována.

**Q: Je možné hromadně importovat více PDF do jednoho dokumentu Word?**  
A: Rozhodně. Projděte svou kolekci PDF a zavolejte `Insert` pro každý soubor; knihovna je sloučí postupně.

**Q: Co když mé PDF obsahuje vektorovou grafiku?**  
A: Vektorová grafika je zachována, když je PDF vloženo jako OLE objekt; vykresluje se ostře při libovolné úrovni přiblížení.

**Q: Funguje GroupDocs.Merger v Linuxových kontejnerech?**  
A: Ano – sestavení .NET Standard běží na Linuxu, macOS a Windows bez jakýchkoli nativních závislostí.

## Dostupné tutoriály

### [Přidání příloh do PDF pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Naučte se, jak přidávat přílohy do PDF pomocí GroupDocs.Merger pro .NET. Tento průvodce krok za krokem pokrývá nastavení, implementaci a praktické aplikace.

### [Vložení PDF jako OLE do PowerPointu pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Naučte se, jak bez problémů vložit PDF soubor jako OLE objekt do vaší prezentace PowerPoint pomocí GroupDocs.Merger pro .NET. Postupujte podle tohoto komplexního průvodce.

### [Vložení PDF do Wordu pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](./embed-pdf-word-groupdocs-merger-dotnet/)
Naučte se, jak bez problémů vložit PDF do dokumentu Microsoft Word pomocí GroupDocs.Merger pro .NET. Efektivně vylepšete své dokumenty dynamickým obsahem.

### [Jak vložit OLE objekty do tabulek Excel pomocí GroupDocs.Merger pro .NET](./embed-ole-objects-groupdocs-merger-net/)
Naučte se, jak bez problémů vložit OLE objekty, jako jsou PDF, do tabulek Excel pomocí GroupDocs.Merger pro .NET, a zlepšit tak prezentaci a funkčnost dat.

## Další zdroje

- [GroupDocs.Merger pro .net Dokumentace](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger pro .net API Reference](https://reference.groupdocs.com/merger/net/)
- [Stáhnout GroupDocs.Merger pro .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger fórum](https://forum.groupdocs.com/c/merger)
- [Bezplatná podpora](https://forum.groupdocs.com/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)

---

**Poslední aktualizace:** 2026-09-11  
**Testováno s:** GroupDocs.Merger 23.12 for .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Vložení PDF do Wordu pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Přidání příloh do PDF pomocí GroupDocs.Merger pro .NET: Průvodce krok za krokem](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [Načítání PDF z URL v .NET pomocí GroupDocs.Merger: Kompletní průvodce](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)