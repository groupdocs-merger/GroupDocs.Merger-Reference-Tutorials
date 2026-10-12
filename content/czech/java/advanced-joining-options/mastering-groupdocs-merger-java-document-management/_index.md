---
date: '2026-10-11'
description: Naučte se, jak sloučit soubory PDF a DOCX a převést DOCX na PDF v Javě
  pomocí GroupDocs.Merger, včetně zpracování streamu a tipů pro práci s velkými dokumenty.
keywords:
- convert docx to pdf java
- handle large documents java
- GroupDocs.Merger Java
- PDF DOCX merging Java
lastmod: '2026-10-11'
og_description: Naučte se, jak sloučit soubory PDF a DOCX a převést DOCX na PDF v
  Javě s GroupDocs.Merger. Obsahuje načítání streamu a zpracování velkých dokumentů.
og_image_alt: Developer guide showing Java code to merge PDF and DOCX and convert
  DOCX to PDF using GroupDocs.Merger
og_title: Jak sloučit PDF a DOCX a převést DOCX na PDF v Javě
schemas:
- author: GroupDocs
  dateModified: '2026-10-11'
  description: Learn how to merge PDF and DOCX files and convert DOCX to PDF in Java
    using GroupDocs.Merger, with stream handling and large document tips.
  headline: How to merge PDF and DOCX and convert DOCX to PDF in Java
  type: TechArticle
- description: Learn how to merge PDF and DOCX files and convert DOCX to PDF in Java
    using GroupDocs.Merger, with stream handling and large document tips.
  name: How to merge PDF and DOCX and convert DOCX to PDF in Java
  steps:
  - name: '**Free trial** – explore core features without a credit card.'
    text: '**Free trial** – explore core features without a credit card.'
  - name: '**Temporary license** – request a short‑term key on the *temporary license
      page* ([temporary license page](https://purchase.groupdocs.com/temporary-license/)).'
    text: '**Temporary license** – request a short‑term key on the *temporary license
      page* ([temporary license page](https://purchase.groupdocs.com/temporary-license/)).'
  - name: '**Full purchase** – obtain an unlimited production license for commercial
      deployments. You can purchase a full license directly from **GroupDocs** ([GroupDocs](https://purchase.groupdocs.com/buy)).'
    text: '**Full purchase** – obtain an unlimited production license for commercial
      deployments. You can purchase a full license directly from **GroupDocs** ([GroupDocs](https://purchase.groupdocs.com/buy)).'
  - name: '**Batch report generation** – combine daily Excel exports (XLSX) and Word
      summaries (DOCX) into a single PDF for archiving.'
    text: '**Batch report generation** – combine daily Excel exports (XLSX) and Word
      summaries (DOCX) into a single PDF for archiving.'
  - name: '**Dynamic invoice creation** – merge a PDF invoice template with a DOCX
      terms‑and‑conditions document, then deliver the final PDF to the client.'
    text: '**Dynamic invoice creation** – merge a PDF invoice template with a DOCX
      terms‑and‑conditions document, then deliver the final PDF to the client.'
  - name: '**Cross‑platform services** – expose a REST endpoint that accepts mixed‑format
      uploads, merges them, and streams the result back without storing temporary
      files.'
    text: '**Cross‑platform services** – expose a REST endpoint that accepts mixed‑format
      uploads, merges them, and streams the result back without storing temporary
      files.'
  type: HowTo
- questions:
  - answer: Call `Merger.save(OutputStream)` after adding all source files.
    question: What is the primary way to save a merged document in Java?
  - answer: Yes – it supports 30+ input and output formats, including DOCX, PDF, PPTX,
      XLSX, and many image types.
    question: Can GroupDocs.Merger merge different file formats?
  - answer: 'Instantiate `Merger` with the stream: `new Merger(stream)`.'
    question: How do I load a document from an InputStream?
  - answer: Use buffered streams, process files in batches, and close each stream
      as soon as possible to keep memory usage low.
    question: What should I do with large documents?
  - answer: Yes – a valid GroupDocs license unlocks full functionality and removes
      evaluation watermarks.
    question: Is a license required for production use?
  type: FAQPage
tags:
- convert docx to pdf
- GroupDocs.Merger
- Java document processing
- PDF merging
title: Jak sloučit PDF a DOCX a převést DOCX na PDF v Javě
type: docs
url: /cs/java/advanced-joining-options/mastering-groupdocs-merger-java-document-management/
weight: 1
---

# Jak sloučit PDF a DOCX a převést DOCX na PDF v Javě

V tomto tutoriálu se dozvíte, jak **sloučit PDF a DOCX soubory** a také **převést DOCX na PDF** pomocí GroupDocs.Merger pro Java. Uvidíte, jak načíst dokumenty ze streamů, zpracovat vícegigabajtové payloady a vytvořit jeden výstup, který lze uložit na disk, odeslat klientovi nebo uložit do cloudového úložiště. Na konci budete mít připravený úryvek kódu, který se hodí do jakékoli webové služby, dávkového úkolu nebo mikroservisní architektury.

## Rychlé odpovědi
- **Jaký je hlavní způsob uložení sloučeného dokumentu v Javě?** Zavolejte `Merger.save(OutputStream)` po přidání všech zdrojových souborů.  
- **Může GroupDocs.Merger sloučit různé formáty souborů?** Ano – podporuje více než 30 vstupních a výstupních formátů, včetně DOCX, PDF, PPTX, XLSX a mnoha typů obrázků.  
- **Jak načíst dokument ze `InputStream`?** Vytvořte instanci `Merger` s proudem: `new Merger(stream)`.  
- **Co dělat s velkými dokumenty?** Používejte bufferované streamy, zpracovávejte soubory po dávkách a co nejdříve uzavírejte každý stream, aby byl paměťový výdej nízký.  
- **Je pro produkční použití vyžadována licence?** Ano – platná licence GroupDocs odemkne plnou funkčnost a odstraní evaluační vodoznaky.

## Co je sloučení PDF a DOCX?
Sloučení PDF a DOCX znamená kombinaci jednoho nebo více PDF a Word dokumentů do jediného souboru při zachování pořadí stránek, metadat a vizuální věrnosti každého zdroje. S GroupDocs.Merger můžete operaci sloučení také použít jako rychlý způsob **převodu DOCX na PDF** tím, že přidáte obsah DOCX do PDF kontejneru a poté výsledek uložíte jako PDF.

## Proč použít GroupDocs.Merger ke sloučení různých formátů souborů?
GroupDocs.Merger abstrahuje nízkoúrovňové detaily každého formátu, což vám umožní soustředit se na obchodní pravidla. Knihovna dokáže zpracovat **více než 30 formátů**, pracovat se soubory až do **500 MB** bez načítání celého dokumentu do paměti a zaručuje, že číslování stránek, záhlaví a zápatí zůstane v sloučeném výstupu nedotčeno.

## Předpoklady

- Knihovna GroupDocs.Merger pro Java
- Java 8+ (JDK 8 nebo vyšší)
- Maven nebo Gradle pro správu závislostí
- IDE, např. IntelliJ IDEA nebo Eclipse
- Platná licence GroupDocs pro produkci (k dispozici je bezplatná zkušební verze)

## Nastavení GroupDocs.Merger pro Java

### Maven

Přidejte následující závislost do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle

Ve vašem `build.gradle` zahrňte:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Přímé stažení

Alternativně stáhněte nejnovější verzi z [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) a ručně ji přidejte do classpath vašeho projektu.

#### Kroky získání licence
1. **Free trial** – vyzkoušejte základní funkce bez kreditní karty.  
2. **Temporary license** – požádejte o krátkodobý klíč na *stránce dočasné licence* ([temporary license page](https://purchase.groupdocs.com/temporary-license/)).  
3. **Full purchase** – získejte neomezenou produkční licenci pro komerční nasazení. Plnou licenci můžete zakoupit přímo od **GroupDocs** ([GroupDocs](https://purchase.groupdocs.com/buy)).

#### Základní inicializace

Třída `Merger` je vstupním bodem pro všechny operace; představuje jedinou sloučovací relaci. Po přidání knihovny vytvořte instanci `Merger`:

```java
import com.groupdocs.merger.Merger;

// Initialize GroupDocs Merger
erMerger = new Merger("YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX");
```

## Jak načíst dokument ze streamu?

Načtení dokumentu z `InputStream` vám umožní pracovat se soubory, které pocházejí z HTTP nahrávek, cloudových úložišť nebo generování v paměti. `InputStream` je Java abstrakce, která čte bajty ze zdroje, jako je soubor, síťový socket nebo paměťový buffer, což knihovně umožňuje zpracovávat data bez vytváření dočasných souborů na disku. Tento přístup snižuje režii I/O a zlepšuje výkon ve službách s vysokou propustností.

### Krok 1 – vytvořte vstupní stream

```java
import java.io.FileInputStream;
import java.io.InputStream;

InputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX");
```

*Proč?* Stream převádí fyzický soubor na sekvenci bajtů, kterou Merger může číst, aniž by jej ukládal na disk.

### Krok 2 – inicializujte Merger se streamem

```java
Merger merger = new Merger(stream);
```

*Proč?* Poskytnutí streamu umožňuje zpracování v paměti, což je ideální pro serverless funkce nebo API s vysokou propustností.

## Jak uložit sloučený dokument v Javě?

Po sloučení musíte uložit kombinovaný obsah na cílové místo dle vašeho výběru. `OutputStream` je Java abstrakce, která zapisuje bajty do cíle, jako je soubor, síťový socket nebo paměťový buffer, což vám poskytuje flexibilitu v tom, jak je sloučený dokument doručen. Poskytnutí `OutputStream` metodě `Merger.save` zajišťuje, že finální PDF nebo DOCX bude zapsáno efektivně a bezpečně.

### Krok 1 – definujte výstupní stream

```java
import java.io.FileOutputStream;
import java.io.OutputStream;

OutputStream outputStream = new FileOutputStream("YOUR_OUTPUT_DIRECTORY/merged_output.docx");
```

*Proč?* `OutputStream` říká Javě, kam má být sloučený soubor zapsán, ať už na disk, do těla odpovědi nebo do cloudového úložiště.

### Krok 2 – uložte dokument

```java
merger.save(outputStream);
```

*Proč?* `save()` dokončuje sloučení, vyprázdní buffery a zajišťuje, že výstup odpovídá specifikacím vybraného formátu.

### Krok 3 – zavřete stream

```java
outputStream.close();
```

*Proč?* Zavření uvolní OS handly a zaručí, že všechny bufferované bajty jsou uloženy, čímž se předejde poškození souboru.

## Jak zacházet s velkými dokumenty v Javě?

Velké PDF nebo vícegigabajtové Word soubory mohou vyčerpat haldu JVM, pokud jsou načteny nešikovně. Pro udržení paměťové spotřeby pod kontrolou zabalte surové streamy do `BufferedInputStream` a `BufferedOutputStream`, zpracovávejte soubory po dávkách a po každé operaci zavolejte `Merger.close()`, aby se uvolnily nativní zdroje. Sledování využití haldy a nastavení vhodného příznaku `-Xmx` (cílová hodnota ≤70 % dostupné paměti) dále chrání před chybami nedostatku paměti.

## Praktické aplikace

GroupDocs.Merger je ideální pro reálné úkoly, jako jsou:

1. **Dávková generace reportů** – kombinujte denní exporty z Excelu (XLSX) a Word souhrny (DOCX) do jednoho PDF pro archivaci.  
2. **Dynamické vytváření faktur** – sloučte PDF šablonu faktury s DOCX dokumentem podmínek, a poté doručte finální PDF klientovi.  
3. **Cross‑platform služby** – vystavte REST endpoint, který přijímá nahrané soubory různých formátů, sloučí je a streamuje výsledek zpět bez ukládání dočasných souborů.

## Úvahy o výkonu

- **Správa paměti** – vždy zavírejte streamy; knihovna používá nativní buffery, které je třeba uvolnit.  
- **Dávkové operace** – seskupování souborů snižuje počet diskových seeků a zvyšuje propustnost až o 30 %.  
- **Efektivní I/O** – pro soubory větší než 10 MB může bufferované I/O zkrátit dobu zpracování přibližně na polovinu.

## Časté problémy a řešení

| Problém | Důvod | Řešení |
|---------|-------|--------|
| `FileNotFoundException` | Špatná cesta nebo nedostatečná oprávnění | Ověřte absolutní/relativní cesty a zajistěte, aby aplikace měla práva čtení/zápisu |
| `IOException` během ukládání | Stream není uzavřen nebo je disk plný | Použijte try‑with‑resources, zavřete streamy a zkontrolujte dostupné místo na disku |
| Nárazové zvýšení paměti u velkých PDF | Celý soubor načten do paměti | Přepněte na bufferované streamy a zpracovávejte v menších dávkách |

## Často kladené otázky

**Q:** Můžu sloučit různé formáty souborů pomocí GroupDocs.Merger?  
**A:** Ano, knihovna podporuje více než 30 formátů – včetně DOCX, PDF, PPTX, XLSX a běžných typů obrázků – což umožňuje plynulé cross‑format sloučení.

**Q:** Jak efektivně zacházet s velkými dokumenty?  
**A:** Zabalte své souborové streamy do `BufferedInputStream`/`BufferedOutputStream`, sloučujte soubory po dávkách a po použití okamžitě zavřete každý stream.

**Q:** Existuje podpora pro soubory chráněné heslem?  
**A:** Ano. Zadejte heslo při vytváření instance `Merger`, aby se otevřely šifrované PDF nebo DOCX soubory.

**Q:** Mohu tuto knihovnu použít v komerčním produktu?  
**A:** Ano, platná licence GroupDocs odemkne plné produkční funkce bez evaluačních vodoznaků.

**Q:** Co mám dělat, pokud narazím na `IOException`?  
**A:** Zkontrolujte cesty k souborům, ujistěte se, že proces má dostatečná oprávnění, ověřte volné místo na disku a obalte I/O volání do try‑catch bloků nebo použijte try‑with‑resources.

## Zdroje

- **Documentation**: [GroupDocs Documentation](https://docs.groupdocs.com/merger/java/)  
- **API reference**: [API Reference Guide](https://reference.groupdocs.com/merger/java/)  
- **Download library**: [GroupDocs Downloads](https://releases.groupdocs.com/merger/java/)  
- **Purchase license**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Free trial & temporary license**: [Try Out GroupDocs](https://releases.groupdocs.com/merger/java/) a [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Poslední aktualizace:** 2026-10-11  
**Testováno s:** GroupDocs.Merger latest version (as of 2026)  
**Autor:** GroupDocs  

---

## Související tutoriály

- [sloučit docx soubory java – Správa dokumentů s GroupDocs.Merger](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Sloučit PDF Java: Načíst lokální dokument pomocí GroupDocs.Merger – Průvodce](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [sloučit konkrétní stránky java – Spojit dokumenty s GroupDocs.Merger](/merger/java/document-joining/join-pages-groupdocs-merger-java-tutorial/)