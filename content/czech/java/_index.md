---
date: 2026-06-16
description: Naučte se, jak rozdělit PDF a sloučit PDF pomocí GroupDocs.Merger pro
  Java – podrobný průvodce krok za krokem, který zahrnuje split pdf java, merge pdf
  java, protect pdf java a další.
is_root: true
keywords:
- split pdf java
- java combine pdf files
- groupdocs merger for java
- protect pdf java
- merge multiple pdfs java
linktitle: GroupDocs.Merger pro Java – návody
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to split PDF and merge PDFs with GroupDocs.Merger for Java
    – step-by-step guide covering split pdf java, merge pdf java, protect pdf java,
    and more.
  headline: How to Split PDF and Merge PDFs with GroupDocs.Merger for Java
  type: TechArticle
- questions:
  - answer: Instantiate a `Merger`, call `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`,
      and specify an output folder—each range becomes a separate PDF file.
    question: How do I split PDFs using GroupDocs.Merger in Java?
  - answer: Yes—GroupDocs.Merger supports cross‑format merging, allowing you to combine
      PDFs with Excel files (`merge excel files java`) into a single PDF output.
    question: Can I merge PDFs and Excel sheets together?
  - answer: After calling `merge()`, invoke `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))`
      to encrypt the final document.
    question: How do I add password protection after merging?
  - answer: Enable streaming (`Merger.setStreaming(true)`) to process files in a buffered
      fashion, which dramatically reduces memory consumption for large documents.
    question: Is it possible to merge PDFs without loading the entire file into memory?
  - answer: A commercial GroupDocs.Merger license is mandatory for production deployments;
      a free 30‑day trial is available for development and testing.
    question: What licensing is required for production use?
  type: FAQPage
title: Jak rozdělit PDF a sloučit PDF pomocí GroupDocs.Merger pro Java
type: docs
url: /cs/java/
weight: 10
---

# Jak rozdělit PDF a sloučit PDF pomocí GroupDocs.Merger pro Java

V moderních Java aplikacích je **split pdf java** častým požadavkem — ať už potřebujete rozdělit obrovskou zprávu na menší kapitoly nebo spojit několik faktur do jednoho archivu. GroupDocs.Merger pro Java usnadňuje jak rozdělování, tak sloučení PDF (a více než 50 dalších formátů), poskytuje vysoce výkonné zpracování pomocí několika řádků kódu. V tomto tutoriálu prozkoumáme hlavní API, projdeme reálné scénáře a nasměrujeme vás k podrobnějším tutoriálům pro každou potřebu zpracování dokumentů, na kterou můžete narazit.

## Rychlé odpovědi
- **Jaký je hlavní účel GroupDocs.Merger?** Kombinovat, rozdělovat a manipulovat s dokumenty ve více než 50 formátech, včetně PDF, Word, Excel a obrázků.  
- **Mohu v Javě rozdělovat PDF?** Ano – API nabízí vyhrazenou metodu “split pdf java”, která vám umožní definovat rozsahy stránek nebo rozdělení podle velikosti.  
- **Jak sloučím více PDF v Javě?** Použijte třídu `Merger` s pracovním postupem “merge pdf java” pro okamžité spojení souborů.  
- **Je po sloučení k dispozici ochrana heslem?** Ano; funkce “protect pdf java” zašifruje výsledek heslem, které si zvolíte.  
- **Potřebuji licenci pro produkci?** Pro jakékoli nasazení do produkce je vyžadována komerční licence GroupDocs.Merger; k vyzkoušení je k dispozici bezplatná zkušební verze.

## Co je “how to merge PDFs” s GroupDocs.Merger?
`GroupDocs.Merger for Java` je knihovna, která programově kombinuje více PDF souborů (nebo jakýkoli podporovaný formát) do jednoho dobře strukturovaného dokumentu. Automaticky zachovává pořadí stránek, metadata a volitelné bezpečnostní nastavení, což vám umožní dosáhnout složitých pracovních postupů s minimálním množstvím kódu.

## Proč používat GroupDocs.Merger pro Java?
Načtěte své zdrojové PDF, určete požadované stránky a zavolejte `merge()` — API se postará o těžkou práci. Poskytuje **více než 50 vstupních a výstupních formátů**, zpracovává **stovky stránek za sekundu** a funguje jak v on‑premise, tak v cloudových prostředích bez externích závislostí.

## Ovládněte manipulaci s dokumenty pomocí GroupDocs.Merger

GroupDocs.Merger pro Java je výkonné API, které umožňuje vývojářům Java kombinovat, rozdělovat a manipulovat s dokumenty ve více než 50 populárních formátech souborů. Naše komplexní série tutoriálů poskytuje podrobné, krok za krokem vedení, jak využít plné možnosti GroupDocs.Merger k zefektivnění vašich pracovních postupů správy dokumentů.

Ať už potřebujete **sloučit více PDF**, spojit Word dokumenty, spojit tabulky, konsolidovat prezentace nebo pracovat s obrázky – tyto tutoriály vám pomohou implementovat robustní funkce zpracování dokumentů ve vašich Java aplikacích s minimálním množstvím kódu.

## Co můžete s GroupDocs.Merger dosáhnout
- **Sloučit více dokumentů** do jednoho souboru při zachování formátování a integrity obsahu.  
- **Spojit konkrétní stránky nebo rozsahy** z různých zdrojových dokumentů.  
- **Rozdělit velké dokumenty** na menší, lépe spravovatelné soubory.  
- **Manipulovat s pořadím stránek** pomocí přesunu, odstraňování, otáčení nebo výměny.  
- **Chránit dokumenty** pomocí šifrování heslem a správy oprávnění.  
- **Extrahovat obsah** z konkrétních částí dokumentu.  
- **Zpracovávat dokumenty** v mnoha formátech včetně PDF, Word, Excel, PowerPoint a dalších.

## Kategorie tutoriálů GroupDocs.Merger pro Java

### [Načítání dokumentu](./document-loading/)
Ovládněte zásadní první krok při zpracování dokumentů. Naučte se různé techniky načítání dokumentů ze souborů, streamů a URL s vhodnou konfigurací pro různé formáty.

### [Informace o dokumentu](./document-information/)
Extrahujte cenná metadata ze svých dokumentů. Tyto tutoriály vám ukážou, jak získat vlastnosti dokumentu, počet stránek a podrobnosti o formátu pro lepší správu dokumentů.

### [Spojování dokumentů](./document-joining/)
Bezproblémově kombinujte více dokumentů. Objevte, jak sloučit celé soubory nebo vybrat konkrétní stránky z různých zdrojů do jednoho soudržného dokumentu.

### [Formátově specifické sloučení](./format-specific-merging/)
Optimalizujte operace sloučení pro konkrétní typy souborů. Naučte se specializované techniky pro spojování PDF, Word dokumentů, Excel tabulek, PowerPoint prezentací a dalších.

### [Pokročilé možnosti spojování](./advanced-joining-options/)
Posuňte sloučení dokumentů na další úroveň. Prozkoumejte složité scénáře spojování s vlastním výběrem stránek, cross‑format sloučením a možnostmi zachování obsahu.

### [Zabezpečení dokumentu](./document-security/)
Implementujte robustní ochranu svých dokumentů. Naučte se přidávat, odstraňovat nebo aktualizovat hesla, spravovat oprávnění a zajistit důvěrnost dokumentu.

### [Operace se stránkami](./page-operations/)
Získejte přesnou kontrolu nad stránkami dokumentu. Objevte techniky pro přeskupování, otáčení, odstraňování a úpravu jednotlivých stránek ve vašich dokumentech.

### [Extrahování dokumentu](./document-extraction/)
Extrahujte konkrétní obsah z větších dokumentů. Naučte se vybrat a uložit určité stránky nebo sekce jako samostatné soubory.

### [Import dokumentu](./document-import/)
Vylepšete dokumenty externím obsahem. Tyto tutoriály ukazují, jak importovat obsah z různých zdrojů, včetně OLE objektů a příloh.

### [Operace s obrázky](./image-operations/)
Efektivně zpracovávejte soubory obrázků. Prozkoumejte metody práce s obrázky, včetně sloučení, konverze a vkládání do dokumentů.

### [Rozdělení dokumentu](./document-splitting/)
Strategicky rozdělujte dokumenty. Naučte se techniky rozdělení souborů podle čísel stránek, rozsahů nebo specifických kritérií pro vytvoření více výstupních dokumentů.

### [Operace s textem](./text-operations/)
Efektivně manipulujte s textovými dokumenty. Objevte přístupy ke zpracování textových souborů, včetně sloučení, rozdělení podle řádků a konverze formátu.

### [Licencování](./licensing/)
Správně nastavte GroupDocs.Merger ve svých projektech. Seznamte se s možnostmi licencování, přístupy ke konfiguraci a úvahami o nasazení.

## Podporované formáty souborů

GroupDocs.Merger pro Java podporuje širokou škálu formátů dokumentů, včetně:

- **Zpracování textu**: DOCX, DOC, RTF, ODT, DOTX, DOTM, DOT
- **Tabulky**: XLSX, XLS, XLSM, XLSB, ODS, XLT, XLTX
- **Prezentace**: PPTX, PPT, PPSX, PPS, ODP, POT
- **Přenosné dokumenty**: PDF, XPS
- **Diagramy Visio**: VSDX, VSDM, VSTX, VSSX, VDX, VSX, VTX
- **eKnihy**: EPUB
- **Obrázky**: BMP, JPG, PNG, TIFF
- **Web**: HTML, MHT, MHTML
- **Text**: TXT, CSV, TSV
- **A mnoho dalších!** (více než 50 formátů celkem)

## Začínáme

Tutoriály v této sekci následují praktický, kód‑první přístup s kompletními příklady, které můžete přímo implementovat ve svých aplikacích. Každý tutoriál obsahuje:
- Jasné vysvětlení funkce a jejích případů použití
- Krok za krokem instrukce implementace
- Kompletní ukázky kódu s komentáři (kód je poskytován v odkazovaných pod‑tutoriálech)
- Možnosti konfigurace a alternativní přístupy
- Úvahy o výkonu a osvědčené postupy

Začněte dnes prozkoumávat naše tutoriály a odemkněte plný potenciál GroupDocs.Merger pro Java ve vašich pracovních postupech zpracování dokumentů!

## Jak rozdělit PDF v Javě?

Rozdělte PDF na jednotlivé stránky nebo vlastní rozsahy během pouhých tří řádků v Javě. Zavolejte metodu `split()` na instanci `Merger`, předáte cestu ke zdrojovému souboru a určíte požadovaný rozsah stránek nebo velikost. Knihovna zapíše každý segment do samostatného souboru při zachování původní kvality a metadat.

Můžete také rozdělovat podle velikosti (např. úseky po 5 MB) nebo podle seznamu čísel stránek, což je ideální pro generování PDF po kapitolách z jednoho hlavního dokumentu. Operace běží lineárně vzhledem k počtu stránek, což ji činí vhodnou pro hromadné zpracování ve velkém měřítku.

## Jak sloučit více PDF v Javě?

Načtěte každý zdrojový PDF pomocí metody `addDocument()` třídy `Merger`, uspořádejte je v požadovaném pořadí a zavolejte `merge()`. API automaticky harmonizuje rozměry stránek, aktualizuje záložky a konsoliduje vlastnosti dokumentu. Můžete také sloučit PDF s jinými formáty — například Word nebo Excel — jejich konverzí za běhu, což vede k jedinému, jednotnému PDF výstupu.

Pro scénáře s vysokou propustností povolte režim streamování, aby se zabránilo načítání celých souborů do paměti. To snižuje využití haldy až o 80 % při zpracování dokumentů se stovkami stránek.

## Porozumění třídě Merger

Třída `Merger` je hlavní komponentou GroupDocs.Merger pro Java, která orchestruje kombinaci dokumentů, rozdělování a bezpečnostní operace. Poskytuje plynulé metody jako `addDocument()`, `split()`, `protect()` a `merge()`, které umožňují vytvářet stručné zpracovatelské pipeline.

### Přehled klíčových metod
- `addDocument(String path)`: Zařadí zdrojový soubor do fronty pro pozdější sloučení.  
- `split(String source, SplitOptions options)`: Rozdělí dokument na základě rozsahů stránek nebo limitů velikosti.  
- `protect(String output, ProtectionOptions options)`: Aplikuje ochranu heslem a omezení oprávnění.  
- `merge(String output)`: Provede zařazené operace a zapíše finální dokument.  

Tyto metody jsou bezpečné pro více vláken a lze je řetězit pro výstižný, čitelný kód.

## Časté problémy a řešení

| Problém | Příčina | Řešení |
|-------|-------|----------|
| **Chyby out‑of‑memory u velkých PDF** | Načítání celého souboru do paměti | Povolte režim streamování (`Merger.setStreaming(true)`) nebo rozdělte soubor na menší úseky před sloučením. |
| **Neshoda orientace stránek** | Zdrojové PDF mají smíšené portrétové/landscape stránky | Použijte `rotatePage(int pageNumber, RotationAngle angle)` před sloučením pro standardizaci orientace. |
| **Zdroj chráněný heslem nelze otevřít** | Chybí dešifrovací heslo | Poskytněte heslo pomocí `DocumentLoadOptions.setPassword("yourPwd")` při přidávání dokumentu. |
| **Metadata ztracena po sloučení** | Výchozí sloučení zahazuje vlastní metadata | Zavolejte `setPreserveMetadata(true)` na instanci `Merger`, aby se zachovaly původní vlastnosti. |

## Často kladené otázky

**Q: Jak rozděluji PDF pomocí GroupDocs.Merger v Javě?**  
A: Vytvořte instanci `Merger`, zavolejte `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))` a určete výstupní složku — každý rozsah se stane samostatným PDF souborem.

**Q: Mohu sloučit PDF a Excel tabulky dohromady?**  
A: Ano — GroupDocs.Merger podporuje cross‑format sloučení, což vám umožní kombinovat PDF s Excel soubory (`merge excel files java`) do jednoho PDF výstupu.

**Q: Jak přidám ochranu heslem po sloučení?**  
A: Po zavolání `merge()` použijte `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))` k zašifrování finálního dokumentu.

**Q: Je možné sloučit PDF bez načtení celého souboru do paměti?**  
A: Povolte streamování (`Merger.setStreaming(true)`) pro zpracování souborů v bufferovaném režimu, což výrazně snižuje spotřebu paměti u velkých dokumentů.

**Q: Jaká licence je vyžadována pro produkční použití?**  
A: Pro produkční nasazení je povinná komerční licence GroupDocs.Merger; k dispozici je bezplatná 30‑denní zkušební verze pro vývoj a testování.

---

**Poslední aktualizace:** 2026-06-16  
**Testováno s:** GroupDocs.Merger for Java 23.12 (nejnovější v době psaní)  
**Autor:** GroupDocs

## Související tutoriály

- [Efektivně sloučit PDF pomocí GroupDocs.Merger pro Java: Průvodce krok za krokem](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [Jak snadno sloučit DOCX soubory s GroupDocs.Merger pro Java: Průvodce krok za krokem](/merger/java/format-specific-merging/merge-docx-files-groupdocs-merger-java/)
- [Jak sloučit PowerPoint soubory v Javě pomocí GroupDocs.Merger: Průvodce krok za krokem](/merger/java/format-specific-merging/merge-powerpoint-files-java-groupdocs-merger-guide/)