---
date: '2026-07-25'
description: Naučte se, jak rozdělit soubor po řádcích pomocí GroupDocs.Merger for
  Java – step‑by‑step guide pro efektivní rozdělování dokumentů v Java projektech.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Rozdělení souboru po řádcích pomocí GroupDocs.Merger for Java. Tento
  průvodce ukazuje, jak rychle rozdělit velké textové soubory na části, s code examples
  a best‑practice tips.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Rozdělení souboru po řádcích s GroupDocs.Merger for Java – Fast & Easy
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: Jak rozdělit soubor po řádcích pomocí GroupDocs.Merger for Java
type: docs
url: /cs/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Jak rozdělit soubor po řádcích pomocí GroupDocs.Merger pro Java

Pokud potřebujete **rozdělit soubor po řádcích** — například rozdělit obrovský soubor protokolu na menší úseky, předat dávky dat do pipeline nebo převést dlouhou zprávu na samostatné soubory kapitol — tento tutoriál vám ukáže, jak to provést pomocí GroupDocs.Merger pro Java. Uvidíte, proč je knihovna úsporná na čas, získáte připravenou implementaci a naučíte se praktické tipy, které udrží vaši aplikaci rychlou a spolehlivou.

## Rychlé odpovědi
- **Co znamená „split file by lines“?** Vytváří samostatné textové soubory, z nichž každý obsahuje definovaný rozsah čísel řádků z původního dokumentu.  
- **Která knihovna provádí rozdělení?** GroupDocs.Merger pro Java poskytuje jednoduché API pro rozdělení po řádcích.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkční použití je vyžadována trvalá licence.  
- **Mohu rozdělovat podle počtu znaků místo toho?** Ne přímo — použijte předzpracování k přeformátování souboru před rozdělením.  
- **Jaká verze Javy je podporována?** Jakékoli prostředí Java 8+ je kompatibilní.

## Co je „split file by lines“?
**Split file by lines** znamená vzít jeden textový dokument a rozdělit jej na více souborů, z nichž každý obsahuje konkrétní rozsah po sobě jdoucích řádků (například řádky 1‑3, 4‑6 atd.). Tento přístup je ideální, když chcete zpracovávat data paralelně, snížit zatížení paměti nebo prostě usnadnit navigaci v dlouhých souborech.

## Proč používat GroupDocs.Merger pro Java?
GroupDocs.Merger abstrahuje nízkoúrovňové I/O souborů, takže se můžete soustředit na obchodní logiku. Efektivně zvládá soubory až do 2 GB, aniž by načítal celý dokument do paměti, podporuje **70+** vstupních a výstupních formátů a poskytuje plynulé API, které se čistě integruje s Maven nebo Gradle buildy. Použití této knihovny snižuje vývojový čas až o **80 %** ve srovnání s ručně psanými I/O smyčkami.

## Požadavky
- **Java Development Kit (JDK) 8 nebo vyšší** – ujistěte se, že `java` a `javac` jsou ve vaší PATH.  
- **GroupDocs.Merger pro Java** – přidejte knihovnu pomocí Maven, Gradle nebo přímého stažení.  
- **Základní znalost Javy** – měli byste být obeznámeni s třídami, metodami a zpracováním výjimek.

## Nastavení GroupDocs.Merger pro Java
Přidejte knihovnu do svého projektu pomocí jedné z metod níže.

**Maven** – vložte tuto závislost do svého `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – zahrňte následující řádek v `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Přímé stažení** – můžete také stáhnout JAR z oficiální stránky vydání: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Získání licence
Začněte s bezplatnou zkušební verzí a prozkoumejte API. Pro produkční zatížení získáte dočasnou nebo plnou licenci z portálu GroupDocs.

## Jak rozdělit textový soubor po řádcích (implementace v Javě)

Níže je stručný krok‑za‑krokem průvodce. Každý krok je vysvětlen jednoduchým jazykem před zástupcem, který označuje, kde se nachází skutečný kód, takže přesně víte, co se děje.

### Krok 1: Definujte vstupní a výstupní cesty
Nejprve řekněte knihovně, kde se nachází váš původní soubor a kam mají být zapsány rozdělené fragmenty.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Krok 2: Nakonfigurujte možnosti rozdělení
Vytvořte instanci `TextSplitOptions`, která popisuje požadované intervaly řádků. Pole `new int[] { 3, 6 }` říká API, aby ořízl po řádku 3 a řádku 6, čímž vzniknou dva díly: řádky 1‑3 a řádky 4‑6.  
**Definition:** `TextSplitOptions` je konfigurační objekt, který drží pole intervalů řádků a volitelné pravidla pojmenování výstupu.  
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Krok 3: Inicializujte Merger a spusťte rozdělení
Nakonec vytvořte instanci `Merger` s výchozím souborem a zavolejte `split()` s možnostmi, které jste právě vytvořili.  
**Definition:** `Merger` je hlavní třída v GroupDocs.Merger, která koordinuje operace manipulace s dokumenty, jako je rozdělování, slučování a extrahování stránek.  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Když se volání `split()` dokončí, najdete dva nové soubory v `YOUR_OUTPUT_DIRECTORY`, z nichž každý obsahuje určené rozsahy řádků.

## Praktické aplikace (proč je to důležité)
1. **Data Processing Pipelines** – Rozdělte obrovské soubory protokolu na menší úseky pro paralelní parsování, čímž dramaticky snížíte celkový čas zpracování.  
2. **Document Management** – Přeměňte jedinou zprávu na soubory úrovně kapitol, což usnadní distribuci různým týmům.  
3. **Content Segmentation** – Připravte sekce velkého článku pro cílené publikování na platformách, zlepšující SEO a čitelnost.

## Tipy pro výkon
- **Stream‑line I/O** – Upřednostněte `Files.newBufferedReader` při práci s velmi velkými soubory, aby byl nízký odběr paměti.  
- **Close Resources** – I když GroupDocs.Merger řeší většinu úklidu, explicitní uzavření vlastních streamů zabraňuje únikům.  
- **Monitor Memory** – Rozdělování souborů o velikosti gigabajtů může být paměťově náročné; v případě potřeby alokujte dostatečnou haldu (`-Xmx2g` nebo vyšší).  
- **Batch Processing** – Při rozdělování mnoha souborů znovu použijte jedinou instanci `Merger`, aby se snížilo zatížení tvorbou objektů.

## Časté problémy a řešení
| Problém | Proč se to děje | Řešení |
|-------|----------------|-----|
| `OutOfMemoryError` | Velký zdrojový soubor překračuje velikost haldy. | Zvyšte haldu JVM nebo rozdělujte pomocí menších intervalů. |
| `FileNotFoundException` | Nesprávná cesta nebo chybějící oprávnění. | Ověřte, že `filePath` a `filePathOut` jsou absolutní a zapisovatelné. |
| Prázdné výstupní soubory | Pole intervalů nepokrývá celý dokument. | Ujistěte se, že poslední interval končí na nebo za celkovým počtem řádků. |

## Často kladené otázky

**Q: Mohu rozdělovat soubory podle počtu znaků místo řádků?**  
A: V současné době se GroupDocs.Merger pro Java zaměřuje na intervaly řádků. Můžete však předzpracovat text tak, aby odpovídal požadovanému počtu znaků na řádek, a pak tuto funkci použít.

**Q: Existuje limit na počet intervalů, které mohu zadat pro rozdělení?**  
A: V knihovně neexistuje pevný limit; výkon může klesat, pokud požadujete tisíce malých rozdělení, protože každé rozdělení vyvolává I/O režii.

**Q: Jak zacházet s chybami během rozdělování souboru?**  
A: Zabalte logiku rozdělení do bloku try‑catch a zaznamenejte podrobnosti `MergerException`. API poskytuje jasné zprávy, které přesně ukazují místo selhání.

**Q: Podporuje knihovna další textové formáty, jako CSV nebo TSV?**  
A: Ano, protože CSV a TSV jsou prosté textové soubory, stejná logika intervalů řádků platí. Při volání API je zacházejte jako s `.txt` soubory.

**Q: Mohu automatizovat rozdělování pro více souborů ve složce?**  
A: Rozhodně. Procházejte `Files.list(Paths.get("folder"))`, použijte stejný `TextSplitOptions` na každý soubor a shromážděte vygenerované části.

## Další zdroje
- [GroupDocs.Merger pro Java – vydání](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger pro Java – dokumentace](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)
- [Nejnovější vydání](https://releases.groupdocs.com/merger/java/)
- [Koupit GroupDocs](https://purchase.groupdocs.com/buy)
- [GroupDocs – bezplatná zkušební verze](https://releases.groupdocs.com/merger/java/)
- [Získat dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)
- [Podpora GroupDocs](https://forum.groupdocs.com/c/merger)

---

**Poslední aktualizace:** 2026-07-25  
**Testováno s:** GroupDocs.Merger 23.12 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Jak rozdělit textový soubor na samostatné dokumenty řádků pomocí GroupDocs.Merger pro Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [split pdf java: Rozdělování dokumentů s GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Načtení lokálního dokumentu v Javě pomocí GroupDocs.Merger – průvodce](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)