---
date: '2026-07-25'
description: Ismerje meg, hogyan lehet sorok szerint felosztani a fájlt a GroupDocs.Merger
  for Java használatával – egy step‑by‑step útmutató a hatékony dokumentumfelosztáshoz
  Java projektekben.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Fájl sorok szerint felosztása a GroupDocs.Merger for Java használatával.
  Ez az útmutató bemutatja, hogyan lehet nagy szöveges fájlokat gyorsan részekre bontani,
  code examples és best‑practice tippek segítségével.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Fájl sorok szerint felosztása a GroupDocs.Merger for Java segítségével –
  Gyors és egyszerű
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
title: Hogyan lehet sorok szerint felosztani a fájlt a GroupDocs.Merger for Java segítségével
type: docs
url: /hu/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Hogyan válasszuk szét a fájlt sorok szerint a GroupDocs.Merger for Java segítségével

Ha **split file by lines**‑ra van szükséged — például egy hatalmas naplófájlt kisebb darabokra bontani, adatcsomagokat egy csővezetékbe táplálni, vagy egy hosszú jelentést külön fejezetfájlokká alakítani — ez a bemutató pontosan megmutatja, hogyan teheted ezt a GroupDocs.Merger for Java segítségével. Megtudod, miért takarít időt a könyvtár, kapsz egy azonnal futtatható megvalósítást, és gyakorlati tippeket tanulsz, amelyek gyorsan és megbízhatóan tartják az alkalmazásodat.

## Gyors válaszok
- **Mi jelent a “split file by lines”?** Ez különálló szövegfájlokat hoz létre, amelyek mindegyike a forrásdokumentum meghatározott sorintervallumát tartalmazza.  
- **Melyik könyvtár kezeli a felosztást?** GroupDocs.Merger for Java provides a simple API for line‑interval splitting.  
- **Szükségem van licencre?** A free trial works for testing; a permanent license is required for production use.  
- **Választhatok-e karakterek száma szerint?** Not directly—use a pre‑processing step to reshape the file before splitting.  
- **Melyik Java verzió támogatott?** Any Java 8+ runtime is compatible.  

## Mi a “split file by lines”?
**Split file by lines** azt jelenti, hogy egyetlen szöveges dokumentumot több fájlra bontunk, amelyek mindegyike egy meghatározott, egymást követő sorintervallumot tartalmaz (például 1‑3., 4‑6. sorok stb.). Ez a megközelítés ideális, ha párhuzamosan szeretnél adatot feldolgozni, csökkenteni a memória terhelését, vagy egyszerűen csak könnyebben navigálhatóvá tenni a hosszú fájlokat.

## Miért használjuk a GroupDocs.Merger for Java-t?
GroupDocs.Merger elvonja a low‑level file‑I/O részleteit, lehetővé téve, hogy az üzleti logikára koncentrálj. Hatékonyan kezeli a legfeljebb 2 GB méretű fájlokat anélkül, hogy a teljes dokumentumot memóriába töltené, támogat **70+** bemeneti és kimeneti formátumot, és egy folyékony API-t biztosít, amely tisztán integrálódik a Maven vagy Gradle buildekkel. Ennek a könyvtárnak a használata akár **80 %**‑kal is csökkentheti a fejlesztési időt a kézi I/O ciklusokhoz képest.

## Előfeltételek
- **Java Development Kit (JDK) 8 vagy újabb** – ellenőrizd, hogy a `java` és `javac` a PATH‑on legyen.  
- **GroupDocs.Merger for Java** – add the library via Maven, Gradle, or a direct download.  
- **Basic Java knowledge** – you should be comfortable with classes, methods, and exception handling.  

## A GroupDocs.Merger for Java beállítása
Add the library to your project using one of the methods below.

**Maven** – illeszd be ezt a függőséget a `pom.xml` fájlodba:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – include the following line in `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – a JAR‑t letöltheted a hivatalos kiadási oldalról is: [GroupDocs.Merger for Java kiadások](https://releases.groupdocs.com/merger/java/).

### Licenc beszerzése
Kezdd egy ingyenes próbaverzióval az API felfedezéséhez. Gyártási feladatokhoz szerezz ideiglenes vagy teljes licencet a GroupDocs portálról.

## Hogyan válasszuk szét a szövegfájlt sorok szerint (Java megvalósítás)

Az alábbiakban egy tömör, lépésről‑lépésre útmutató található. Minden lépést egyszerű nyelven magyarázunk el, mielőtt a tényleges kódot jelző helyőrző megjelenik, így pontosan tudod, mi történik.

### 1. lépés: Forrás- és kimeneti útvonalak meghatározása
Először add meg a könyvtárnak, hogy hol található az eredeti fájl, és hová kell írni a felosztott darabokat.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### 2. lépés: A felosztási beállítások konfigurálása
Hozz létre egy `TextSplitOptions` példányt, amely leírja a kívánt sorintervallumokat. A `new int[] { 3, 6 }` tömb azt mondja az API‑nak, hogy vágjon a 3. és a 6. sor után, így két rész keletkezik: 1‑3. sorok és 4‑6. sorok.  
**Definition:** `TextSplitOptions` egy konfigurációs objektum, amely a sor‑intervallum tömböt és opcionális kimeneti elnevezési szabályokat tárol.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### 3. lépés: A Merger inicializálása és a felosztás végrehajtása
Végül példányosítsd a `Merger`‑t a forrásfájllal, és hívd meg a `split()`‑t a most létrehozott beállításokkal.  
**Definition:** `Merger` a GroupDocs.Merger központi osztálya, amely a dokumentumműveleteket, például a felosztást, egyesítést és oldalak kinyerését koordinálja.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Amikor a `split()` hívás befejeződik, két új fájlt találsz a `YOUR_OUTPUT_DIRECTORY` könyvtárban, amelyek mindegyike a megadott sorintervallumokat tartalmazza.

## Gyakorlati alkalmazások (Miért fontos)
1. **Data Processing Pipelines** – Törd fel a hatalmas naplófájlokat kisebb darabokra a párhuzamos elemzéshez, ezáltal drámaian csökkentve az összes feldolgozási időt.  
2. **Document Management** – Egyetlen jelentést fejezet‑szintű fájlokká alakíts, így megkönnyítve a különböző csapatok közötti terjesztést.  
3. **Content Segmentation** – Készíts elő egy nagy cikk szakaszait célzott kiadási platformokra, javítva az SEO‑t és az olvashatóságot.  

## Teljesítmény tippek
- **Stream‑line I/O** – Nagyon nagy fájlok esetén részesítsd előnyben a `Files.newBufferedReader` használatát, hogy alacsony maradjon a memóriahasználat.  
- **Close Resources** – Bár a GroupDocs.Merger a legtöbb takarítást elvégzi, a saját stream-ek explicit bezárása megakadályozza a szivárgásokat.  
- **Monitor Memory** – A gigabájt méretű fájlok felosztása memóriaigényes lehet; szükség esetén biztosíts elegendő heap‑et (`-Xmx2g` vagy nagyobb).  
- **Batch Processing** – Sok fájl felosztásakor használd újra ugyanazt a `Merger` példányt, hogy csökkentsd az objektum‑létrehozási terhelést.  

## Gyakori problémák és megoldások
| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| `OutOfMemoryError` | A nagy forrásfájl meghaladja a heap méretét. | Növeld a JVM heap‑et, vagy használj kisebb intervallumokat a felosztáshoz. |
| `FileNotFoundException` | Helytelen útvonal vagy hiányzó jogosultságok. | Ellenőrizd, hogy a `filePath` és `filePathOut` abszolút és írható legyen. |
| Üres kimeneti fájlok | Az intervallum tömb nem fedi le a teljes dokumentumot. | Győződj meg róla, hogy az utolsó intervallum a teljes sorok számánál végződik vagy azt meghaladja. |

## Gyakran feltett kérdések

**Q: Feloszthatok-e fájlokat karakterek száma alapján a sorok száma helyett?**  
A: Jelenleg a GroupDocs.Merger for Java a sorintervallumokra koncentrál. Azonban előfeldolgozhatod a szöveget, hogy a kívánt karakterek számát soronként elérd, mielőtt ezt a funkciót használnád.

**Q: Van korláta annak, hogy hány intervallumot adhatok meg a felosztáshoz?**  
A: Nincs szigorú korlát a könyvtárban; a teljesítmény romolhat, ha több ezer apró felosztást kérsz, mivel minden felosztás I/O terhet jelent.

**Q: Hogyan kezeljem a hibákat a fájl felosztása során?**  
A: Tekerd be a felosztási logikát egy try‑catch blokkba, és naplózd a `MergerException` részleteit. Az API egyértelmű üzeneteket ad, amelyek pontosan megmutatják a hiba pontját.

**Q: Támogatja a könyvtár a többi szöveges formátumot, például a CSV‑t vagy TSV‑t?**  
A: Igen, mivel a CSV és TSV egyszerű szövegfájlok, ugyanaz a sor‑intervallum logika érvényes. Kezeld őket `.txt` fájlokként az API hívásakor.

**Q: Automatizálhatom-e a felosztást több fájlra egy mappában?**  
A: Természetesen. Iterálj a `Files.list(Paths.get("folder"))` felett, alkalmazd ugyanazt a `TextSplitOptions`‑t minden fájlra, és gyűjtsd össze a létrehozott részeket.

## További források
- [GroupDocs.Merger for Java kiadások](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java dokumentáció](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API referencia](https://reference.groupdocs.com/merger/java/)
- [Legújabb kiadások](https://releases.groupdocs.com/merger/java/)
- [GroupDocs vásárlása](https://purchase.groupdocs.com/buy)
- [GroupDocs ingyenes próba](https://releases.groupdocs.com/merger/java/)
- [Ideiglenes licenc beszerzése](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs támogatás](https://forum.groupdocs.com/c/merger)

---

**Utolsó frissítés:** 2026-07-25  
**Tesztelve ezzel:** GroupDocs.Merger 23.12 for Java  
**Szerző:** GroupDocs

## Kapcsolódó bemutatók
- [Hogyan válasszuk szét egy szövegfájlt külön sor dokumentumokra a GroupDocs.Merger for Java használatával](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [pdf felosztása java: Dokumentum felosztás a GroupDocs.Merger-rel](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Helyi dokumentum betöltése Java-ban a GroupDocs.Merger segítségével – Útmutató](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)