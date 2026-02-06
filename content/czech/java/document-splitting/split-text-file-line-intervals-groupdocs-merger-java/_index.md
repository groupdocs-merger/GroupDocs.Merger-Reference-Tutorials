---
date: '2026-02-06'
description: Naučte se, jak rozdělit textový soubor po řádcích pomocí GroupDocs.Merger
  pro Javu. Průvodce krok za krokem pro efektivní rozdělování dokumentů v projektech
  v Javě.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Jak rozdělit soubor po řádcích pomocí GroupDocs.Merger pro Java
type: docs
url: /cs/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Jak rozdělit soubor po řádcích pomocí GroupDocs.Merger pro Java

Rozdělení velkého textového souboru na menší, lépe zvládnutelné části **po řádcích** je běžná potřeba, například při zpracování logů, hromadném importu dat nebo reorganizaci rozsáhlých zpráv. V tomto tutoriálu se přesně naučíte, jak **rozdělit soubor po řádcích** pomocí GroupDocs.Merger pro Java, proč tento přístup šetří čas a získáte připravený ukázkový kód.

## Rychlé odpovědi
- **Co znamená „rozdělit soubor po řádcích“?** Vytváří samostatné textové soubory, z nichž každý obsahuje definovaný rozsah čísel řádků z původního dokumentu.  
- **Která knihovna provádí rozdělení?** GroupDocs.Merger pro Java poskytuje jednoduché API pro rozdělení po intervalech řádků.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkční použití je vyžadována trvalá licence.  
- **Mohu místo toho rozdělovat podle počtu znaků?** Ne přímo — použijte předzpracovatelský krok k přeformátování souboru před rozdělením.  
- **Jaká verze Javy je podporována?** Jakékoli prostředí Java 8+ je kompatibilní.

## Co je „rozdělit soubor po řádcích“?
Rozdělení souboru po řádcích znamená vzít jeden textový dokument a rozdělit jej na více souborů, z nichž každý obsahuje konkrétní rozsah po sobě jdoucích řádků (např. řádky 1‑3, 4‑6, atd.). Tato technika je ideální pro dávkové zpracování, paralelní analýzu nebo jednoduše pro zlepšení čitelnosti.

## Proč použít GroupDocs.Merger pro Java?
GroupDocs.Merger abstrahuje nízkoúrovňovou práci se soubory, což vám umožní soustředit se na obchodní logiku. Efektivně pracuje s velkými soubory, podporuje mnoho formátů dokumentů a nabízí čisté, plynulé API, které se dobře integruje s Maven nebo Gradle buildy.

## Předpoklady
- **Java Development Kit (JDK) 8 nebo vyšší** – ujistěte se, že `java` a `javac` jsou ve vaší PATH.  
- **GroupDocs.Merger pro Java** – přidejte knihovnu pomocí Maven, Gradle nebo přímého stažení.  
- **Základní znalost Javy** – měli byste být obeznámeni s třídami, metodami a zpracováním výjimek.

## Nastavení GroupDocs.Merger pro Java
Přidejte knihovnu do svého projektu pomocí jedné z níže uvedených metod.

**Maven** – vložte tuto závislost do svého `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – zahrňte následující řádek do `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Přímé stažení** – můžete také stáhnout JAR z oficiální stránky vydání: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Získání licence
Začněte s bezplatnou zkušební verzí, abyste prozkoumali API. Pro produkční zatížení získáte dočasnou nebo plnou licenci z portálu GroupDocs.

## Jak rozdělit textový soubor po řádcích (implementace v Javě)

Níže je stručný, krok za krokem průvodce. Každý krok je vysvětlen jednoduchým jazykem před blokem kódu, abyste přesně věděli, co se děje.

### Krok 1: Definujte vstupní a výstupní cesty
Nejprve řekněte knihovně, kde se nachází váš původní soubor a kam mají být zapsány rozdělené fragmenty.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Krok 2: Nakonfigurujte možnosti rozdělení
Vytvořte instanci `TextSplitOptions`, která popisuje požadované intervaly řádků. Pole `new int[] { 3, 6 }` říká API, aby ořízlo po řádku 3 a řádku 6, čímž vzniknou dvě části: řádky 1‑3 a řádky 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Krok 3: Inicializujte Merger a proveďte rozdělení
Nakonec vytvořte instanci `Merger` se zdrojovým souborem a zavolejte `split()` s možnostmi, které jste právě vytvořili.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

A to je vše! Po dokončení volání najdete dva nové soubory v `YOUR_OUTPUT_DIRECTORY`, z nichž každý obsahuje určené rozsahy řádků.

## Praktické aplikace (Proč je to důležité)
1. **Datové zpracovatelské pipeline** – Rozdělte obrovské soubory logů na menší části pro paralelní parsování.  
2. **Správa dokumentů** – Přeměňte jedinou zprávu na soubory na úrovni kapitol pro snadnější distribuci.  
3. **Segmentace obsahu** – Připravte sekce velkého článku pro cílené publikovací platformy.

## Tipy pro výkon
- **Optimalizujte I/O** – Upřednostněte `Files.newBufferedReader` při práci s velmi velkými soubory, aby se snížila spotřeba paměti.  
- **Uzavírejte zdroje** – I když GroupDocs.Merger provádí většinu úklidu, explicitní uzavření vlastních streamů zabraňuje únikům.  
- **Sledujte paměť** – Rozdělení souborů o velikosti gigabajtů může být náročné na paměť; při potřebe přidělte dostatečný hald (`-Xmx2g` nebo vyšší).

## Časté problémy a řešení
| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| `OutOfMemoryError` | Velký zdrojový soubor překračuje haldu. | Zvyšte haldu JVM nebo rozdělujte pomocí menších intervalů. |
| `FileNotFoundException` | Nesprávná cesta nebo chybějící oprávnění. | Ověřte, že `filePath` a `filePathOut` jsou absolutní a zapisovatelné. |
| Empty output files | Pole intervalů nepokrývá celý dokument. | Ujistěte se, že poslední interval končí na nebo za celkovým počtem řádků. |

## Sekce FAQ

**Q: Mohu rozdělovat soubory na základě počtu znaků místo čísel řádků?**  
A: V současnosti se GroupDocs.Merger pro Java zaměřuje na intervaly řádků. Nicméně můžete předzpracovat svůj text tak, aby odpovídal požadovanému počtu znaků na řádek před použitím této funkce.

**Q: Existuje limit na počet intervalů, které mohu pro rozdělení zadat?**  
A: V samotné knihovně neexistuje konkrétní limit; však výkon může klesat při nadměrném počtu rozdělení kvůli zvýšeným požadavkům na zpracování.

**Q: Jak mohu zvládat chyby během rozdělování souboru?**  
A: Implementujte bloky try‑catch kolem svého kódu, abyste efektivně zachytili a spravovali výjimky. GroupDocs.Merger poskytuje podrobné chybové zprávy, které mohou pomoci při řešení problémů.

**Q: Podporuje knihovna i jiné textové formáty, jako CSV nebo TSV?**  
A: Ano, protože CSV a TSV jsou prosté textové soubory, platí stejná logika intervalů řádků. Stačí je v API zacházet jako s `.txt` soubory.

**Q: Mohu automatizovat rozdělování pro více souborů ve složce?**  
A: Rozhodně. Zabalte výše uvedenou logiku do smyčky, která iteruje přes `Files.list(Paths.get("folder"))` a použije stejný `TextSplitOptions` na každý soubor.

## Zdroje
- **Dokumentace:** [GroupDocs.Merger pro Java Dokumentace](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Stáhnout:** [Nejnovější vydání](https://releases.groupdocs.com/merger/java/)  
- **Nákup a licence:** [Koupit GroupDocs](https://purchase.groupdocs.com/buy)  
- **Bezplatná zkušební verze:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Dočasná licence:** [Získat dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)  
- **Fórum podpory:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Poslední aktualizace:** 2026-02-06  
**Testováno s:** GroupDocs.Merger 23.12 pro Java  
**Autor:** GroupDocs