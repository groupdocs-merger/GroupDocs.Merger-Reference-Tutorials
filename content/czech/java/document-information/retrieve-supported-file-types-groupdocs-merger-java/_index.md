---
date: '2026-07-06'
description: Zjistěte, jak získat podporované typy souborů pomocí GroupDocs.Merger
  pro Javu, zkontrolujte podporované přípony java a integrujte seznam do svého pracovního
  postupu.
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: Podporované formáty GroupDocs.Merger – Získání typů v Javě
type: docs
url: /cs/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger podporované formáty – Získání typů v Javě

Práce s širokou škálou formátů dokumentů v Javě může rychle přerůst v bolest hlavy, pokud nevíte, které z nich vaše knihovna skutečně podporuje. **GroupDocs.Merger podporované formáty** vám poskytují spolehlivý referenční bod, umožňují ověřovat nahrávané soubory, vyhnout se chybám za běhu a navrhovat chytřejší pipeline pro správu dokumentů. V tomto tutoriálu uvidíte přesně, jak získat seznam podporovaných typů souborů pomocí GroupDocs.Merger pro Javu, proč je to důležité a jak začlenit tyto informace do reálných aplikací.

### Rychlé odpovědi
- **Co dělá „retrieve supported file types“?**  
  Vrací seznam všech formátů dokumentů, které GroupDocs.Merger dokáže zpracovat.
- **Která metoda poskytuje seznam?**  
  `FileType.getSupportedFileTypes()` from the `com.groupdocs.merger.domain` package.
- **Potřebuji licenci pro volání této metody?**  
  Pro produkční použití je vyžadována zkušební nebo plná licence; metoda funguje v režimu hodnocení.
- **Mohu filtrovat seznam pouze na rozšíření, která potřebuji?**  
  Ano – projděte vrácený seznam a ponechte pouze rozšíření, která vás zajímají.
- **Je tato operace náročná na výkon?**  
  Ne, pouze čte statickou kolekci, takže běží okamžitě.

## Jaké jsou podporované formáty GroupDocs.Merger?

GroupDocs.Merger podporuje **70+** vstupních a výstupních formátů – včetně PDF, DOCX, PPTX, XLSX, HTML a běžných typů obrázků – což vám umožňuje pracovat prakticky s jakýmkoli obchodním dokumentem. Tabulka formátů knihovny je uložena interně jako statická kolekce, takže její načtení je operace O(1), která dokončí během několika milisekund i na skromném hardwaru.

## Jak mohu v Javě zkontrolovat podporovaná rozšíření?

Zavolejte statickou metodu `FileType.getSupportedFileTypes()`, poté projděte vrácenou kolekci a přečtěte každé rozšíření. Toto jednorázové volání vám poskytne připravený `List<FileType>`, který můžete filtrovat, zobrazovat nebo uložit pro pozdější ověření.

## Proč bych měl získat podporované typy souborů před zpracováním?

Znalost přesného seznamu formátů zabraňuje vyhnutelným výjimkám, snižuje potřebu obranného programování a umožňuje vám uživatelům zobrazit jasnou zprávu o „povolených typech souborů“. Také vám to umožní vytvořit dynamické UI komponenty – například filtry pro výběr souborů – které zobrazují jen kompatibilní rozšíření, čímž zlepšují celkový uživatelský zážitek.

## Předpoklady

- **Java Development Kit (JDK):** Doporučena verze 8 nebo vyšší.  
- **Integrated Development Environment (IDE):** Jakékoli IDE jako IntelliJ IDEA nebo Eclipse bude fungovat.  
- **GroupDocs.Merger Library:** Zařaďte tuto knihovnu do závislostí projektu.  

Znalost základních konceptů programování v Javě a zkušenosti s prací s knihovnami v prostředí Maven nebo Gradle jsou také užitečné. Pokud jste s těmito nástroji noví, zvažte nejprve prostudování jejich dokumentace.

## Nastavení GroupDocs.Merger pro Javu

Pro použití GroupDocs.Merger pro Javu nastavte knihovnu ve svém projektu pomocí Maven, Gradle nebo stažením přímo z oficiálního webu.

### Instalace pomocí Maven

Add the following dependency to your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Instalace pomocí Gradle

Include this line in your `build.gradle` file:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Přímé stažení

Alternativně stáhněte nejnovější verzi z [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Kroky získání licence
1. **Free Trial:** Začněte s bezplatnou zkušební verzí a prozkoumejte funkce knihovny.  
2. **Temporary License:** Získejte dočasnou licenci, pokud potřebujete prodloužený přístup bez omezení.  
3. **Purchase:** Zvažte zakoupení plné licence pro dlouhodobé používání.

## Základní inicializace a nastavení

To initialize GroupDocs.Merger in your Java application, import the necessary classes:

```java
import com.groupdocs.merger.domain.FileType;
```

Nyní přejdeme k implementaci funkce, která získává podporované typy souborů.

## Co je třída FileType?

Třída `FileType` je základní model v GroupDocs.Merger, který představuje jeden formát dokumentu a poskytuje jeho rozšíření, MIME typ a přátelský zobrazovaný název. S touto třídou pracujete, když voláte `FileType.getSupportedFileTypes()`, abyste získali kompletní katalog formátů.

## Jak získat podporované typy souborů?

Pro získání podporovaných formátů jednoduše zavolejte statickou metodu `FileType.getSupportedFileTypes()` poskytovanou knihovnou GroupDocs.Merger. Toto volání vrátí `List<FileType>` obsahující každý formát, který knihovna dokáže zpracovat. Operace je nenáročná a může být provedena při spuštění aplikace nebo kdykoli potřebujete ověřit nahrávané soubory.

### Krok 1: Získání podporovaných typů souborů

First, retrieve the list of supported file types from the `FileType` class:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

### Krok 2: Zobrazení podporovaných rozšíření

Next, iterate through each `FileType` object and print its extension. This is the part where we **display supported extensions** for developers or end‑users:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

### Krok 3: Potvrzovací zpráva

Finally, output a confirmation message indicating successful retrieval:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Praktické aplikace

Porozumění podporovaným typům souborů je zásadní pro různé aplikace:
1. **Document Management Systems:** Automaticky kategorizovat dokumenty podle jejich typu.  
2. **File Conversion Tools:** Zajistit kompatibilitu před konverzí souborů mezi formáty.  
3. **Merging Applications:** Ověřit vstupní soubory před sloučením, aby se předešlo chybám.  

Integrace s dalšími systémy – například cloudovým úložištěm nebo službami pro zpracování dokumentů – může dále rozšířit funkčnost.

## Úvahy o výkonu

When working with GroupDocs.Merger in Java, consider the following performance tips:
- **Optimize Memory Usage:** Uvolňujte objekty, když již nejsou potřeba.  
- **Batch Processing:** Zpracovávejte soubory po dávkách, aby se snížila spotřeba zdrojů.  
- **Asynchronous Operations:** Používejte asynchronní metody pro neblokující operace.  

## Časté problémy a řešení

- **Dependency Issues:** Ověřte, že Maven nebo Gradle závislosti jsou správně deklarovány; nesoulad verzí způsobuje chyby typu class‑not‑found.  
- **Library Version:** Vždy používejte nejnovější verzi GroupDocs.Merger, abyste získali nově přidané formáty a opravy chyb.  
- **License Errors:** Pokud vidíte výjimky související s licencí, potvrďte, že soubor s trial nebo trvalou licencí je ve vašem kódu správně odkazován.

## Často kladené otázky

**Q: Co je GroupDocs.Merger pro Javu?**  
A: Jedná se o Java knihovnu, která umožňuje slučování, rozdělování a konverzi široké škály formátů dokumentů bez potřeby Microsoft Office.

**Q: Jak začít s GroupDocs.Merger?**  
A: Přidejte Maven nebo Gradle závislost, získejte trial nebo plnou licenci a inicializujte knihovnu podle ukázky v sekci nastavení.

**Q: Mohu používat GroupDocs.Merger zdarma?**  
A: Ano, je k dispozici bezplatná zkušební verze pro hodnocení; pro produkční nasazení je vyžadována plná licence.

**Q: Jaké typy souborů GroupDocs.Merger podporuje?**  
A: Použijte metodu `FileType.getSupportedFileTypes()`, která vrátí seznam **70+** podporovaných formátů, včetně PDF, DOCX, PPTX, XLSX, HTML a typů obrázků.

**Q: Jak zacházet s nepodporovanými typy souborů?**  
A: Ověřte nahrávané soubory vůči seznamu podporovaných před zpracováním; odmítněte nebo převádějte nepodporované soubory včas, aby se předešlo chybám za běhu.

**Q: Mohu filtrovat seznam tak, aby zobrazoval jen rozšíření, která potřebuji?**  
A: Ano. Po zavolání `getSupportedFileTypes()` projděte seznam a ponechte jen rozšíření, která vás zajímají.

**Q: Je licence vyžadována pro vývojové sestavení?**  
A: Trial licence funguje pro vývoj a testování; pro komerční produkční použití je vyžadována plná licence.

**Q: Ovlivňuje tato metoda čas spuštění aplikace?**  
A: Ne. Seznam podporovaných typů souborů je statický, takže jeho načtení je prakticky okamžité.

**Q: Změní se seznam s novými verzemi knihovny?**  
A: Nová vydání mohou přidávat nebo rušit formáty; vždy používejte nejnovější verzi, abyste získali nejaktuálnější seznam.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Stáhnout](https://releases.groupdocs.com/merger/java/)
- [Koupit](https://purchase.groupdocs.com/buy)
- [Bezplatná zkušební verze](https://releases.groupdocs.com/merger/java/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)
- [Podpora](https://forum.groupdocs.com/c/merger/) 

Neváhejte prozkoumat tyto zdroje pro podrobnější informace a podporu. Šťastné programování!

---

**Last Updated:** 2026-07-06  
**Testováno s:** GroupDocs.Merger latest version (as of 2026)  
**Autor:** GroupDocs  

## Související tutoriály

- [GroupDocs.Merger pro Javu: Průvodce nastavením licence a kontrolou existence souboru](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Načtení lokálního dokumentu v Javě pomocí GroupDocs.Merger – Průvodce](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Sloučení konkrétních stránek v Javě – Tutoriály pro spojování dokumentů v GroupDocs.Merger](/merger/java/document-joining/)