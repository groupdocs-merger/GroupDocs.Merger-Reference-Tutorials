---
date: '2026-02-13'
description: Tanulja meg, hogyan lehet függőlegesen egyesíteni a képeket a GroupDocs.Merger
  for Java segítségével. Ez az útmutató bemutatja, hogyan lehet függőlegesen összekapcsolni
  a képeket, függőleges fotó kollázst létrehozni, és hatékonyan képeket hozzáadni
  a fájlhoz.
keywords:
- join multiple images vertically
- GroupDocs.Merger for Java
- image merging tutorial
title: Hogyan lehet függőlegesen egyesíteni a képeket a GroupDocs.Merger Java használatával
type: docs
url: /hu/java/format-specific-merging/join-multiple-images-vertically-groupdocs-merger-java/
weight: 1
---

# Képek függőleges egyesítése a GroupDocs.Merger for Java segítségével

Több kép egyetlen fájlba egyesítése gyakori igény, amikor **how to merge images** szeretnénk fotó kollázsokhoz, jelentésekhez vagy marketing anyagokhoz. Ebben az útmutatóban lépésről lépésre bemutatjuk a képek függőleges összekapcsolását a GroupDocs.Merger for Java-val, elmagyarázzuk, miért értékes ez a megközelítés, és gyakorlati tippeket adunk a gyakori buktatók elkerüléséhez.

## Gyors válaszok
- **Milyen könyvtárat használhatok?** GroupDocs.Merger for Java.
- **Csatlakoztathatok háromnál több képet?** Igen – annyit adhat hozzá, amennyire szüksége van.
- **Mely képformátumok támogatottak?** PNG, BMP, JPG és más gyakori statikus formátumok.
- **Szükségem van licencre a fejlesztéshez?** Egy ingyenes próba a teszteléshez működik; a termeléshez fizetett licenc szükséges.
- **A folyamat memóriahatékony?** Töltsön be csak a szükséges képeket, és mentse el gyorsan a memóriahasználat alacsonyan tartásához.

## Mi az a képek egyesítése?
A kép egyesítés egy olyan technika, amely két vagy több különálló képfájlt egyetlen összetett képpé kombinál. Ha a képeket **vertikálisan** halmozzuk, az eredmény egy magas fotószalagként jelenik meg – tökéletes **vertikális fotó kollázs** létrehozásához vagy egy jelentés vizuális szekcióinak összeállításához.

## Miért használjuk a GroupDocs.Merger for Java-t?
- **Egyszerű API** – csak néhány Java sorra van szükség.
- **Formátum rugalmasság** – PNG, BMP, JPG és további formátumok támogatottak.
- **Teljesítmény‑központú** – a képeket hatékonyan dolgozza fel a memóriában.
- **Vállalati‑kész** – licencelési lehetőségeket tartalmaz kereskedelmi projektekhez.

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg róla, hogy a következőkkel rendelkezik:

- **Java Development Kit (JDK)** telepítve (8-as vagy újabb verzió).
- Egy IDE, például **IntelliJ IDEA** vagy **Eclipse**.
- **Maven** vagy **Gradle** a függőségkezeléshez.
- Alapvető ismeretek a Java szintaxisról (mély kép‑feldolgozási tudás nem szükséges).

## A GroupDocs.Merger for Java beállítása

### Maven használata
Addja hozzá a függőséget a `pom.xml` fájlhoz:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle használata
Tegye bele a könyvtárat a `build.gradle` fájlba:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Közvetlen letöltés
Alternatívaként letöltheti a legújabb verziót innen: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Licenc beszerzési lépések
1. **Free Trial** – explore all features without a cost.  
2. **Temporary License** – obtain a short‑term key for extended testing.  
3. **Purchase** – buy a permanent license for production use.

Miután a könyvtár hozzá lett adva, importálja a fő osztályt a Java fájljában:

```java
import com.groupdocs.merger.Merger;
```

## Képek függőleges egyesítése

### 1. lépés: Útvonalak meghatározása és a Merger inicializálása
Először mutassa meg a könyvtárnak a forrásképet, és döntse el, hová menti az egyesített eredményt.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PNG";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "CrossJoinMultipleDocuments-" + Paths.get(filePath).getFileName().toString()).getPath();

// Initialize Merger with the first image file.
Merger merger = new Merger(filePath);
```

### 2. lépés: Csatlakozási beállítások konfigurálása
Mondja meg a GroupDocs.Mergernek, hogy **vertikális** elrendezést szeretne.

```java
ImageJoinOptions imageJoinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
```

### 3. lépés: További képek hozzáadása
Használja a `join` metódust minden egyes extra képhez, amelyet az előző alá szeretne halmozni.

```java
merger.join("YOUR_DOCUMENT_DIRECTORY/SAMPLE_BMP", imageJoinOptions); // Second image.
merger.join("YOUR_DOCUMENT_DIRECTORY/SAMPLE_JPG", imageJoinOptions); // Third image.
```

Ezt a hívást annyiszor megismételheti, amennyire szüksége van, hogy **add images to file** és egy hosszú függőleges kollázst hozzon létre.

### 4. lépés: Az egyesített kép mentése
Végül írja a kombinált képet a lemezre.

```java
merger.save(filePathOut);
```

### Várható eredmény
A kimeneti fájl tartalmazni fogja az összes megadott képet egymás alá, felülről lefelé rendezve, egyetlen magas képet alkotva, amely jelentésekben, prezentációkban vagy webes galériákban használható.

## Gyakori problémák és megoldások
- **Helytelen fájlútvonalak** – ellenőrizze, hogy minden útvonal egy létező képre mutat, és hogy az alkalmazásnak van‑e olvasási/írási jogosultsága.
- **Nem támogatott formátum** – győződjön meg róla, hogy a kép típusa a támogatott statikus formátumok (PNG, BMP, JPG) között van. Az animált GIF-eket ez a funkció nem dolgozza fel.
- **Memória‑hiány hibák** – sok nagy felbontású kép egyesítésekor fontolja meg a képek átméretezését a csatlakoztatás előtt, vagy növelje a JVM heap méretét (`-Xmx` zászló).

## Gyakorlati alkalmazások

| Alkalmazási eset | Hogyan segít |
|------------------|--------------|
| **Vertikális fotó kollázs létrehozása** | Kombinálja a nyaralási fényképeket egyetlen görgethető képpé. |
| **Vizuális jelentés szekciók összeállítása** | Egyesítse a diagramokat, ábrákat és képernyőképeket egy egységes PDF exporthoz. |
| **Marketing anyagok előkészítése** | Rendezze egymásra a termékképeket egy elegáns, görgetés‑barát webes bannerhez. |

## Teljesítmény tippek
- Töltsön be egyszerre csak a szükséges képeket; a `save` után szabadítsa fel a referenciákat, hogy a szemétgyűjtő felszabadítsa a memóriát.
- Használjon SSD tárolót a forrás- és célmappákhoz az I/O felgyorsításához.
- Nagy kötegek feldolgozásakor futtassa az egyesítést háttérszálon, hogy a felhasználói felület reagálók maradjon.

## Összegzés
Most már rendelkezik egy teljes, lépésről‑lépésre megoldással a **how to merge images** függőlegesen történő egyesítéséhez a GroupDocs.Merger for Java használatával. Kísérletezzen különböző képkészletekkel, próbáljon ki más csatlakozási módokat (horizontális, rács), és integrálja ezt a logikát nagyobb automatizálási folyamatokba.

**Következő lépések**
- Fedezze fel az **ImageJoinMode.Horizontal** opciót az oldal‑mellé‑oldal kollázsokhoz.
- Kombinálja az egyesített képet PDF generálással a GroupDocs.PDF segítségével a teljes dokumentumkészítéshez.

## Gyakran Ismételt Kérdések

**K: Milyen képformátumokat kombinálhatok ezzel a módszerrel?**  
V: PNG, BMP, JPG és más gyakori statikus formátumok támogatottak.

**K: Van korláta a csatlakoztatható képek számának?**  
V: Nincs szigorú korlát; a gyakorlati határ a memória rendelkezésre állása. Képeket sorban adjon hozzá a `join` segítségével.

**K: A kimeneti fájlom túl nagy – mit tehetek?**  
V: Méretezze át vagy tömörítse a forrásképeket a egyesítés előtt, vagy használja a Java `ImageIO`‑ját a minőség csökkentéséhez.

**K: Egyesíthetek animált GIF-eket függőlegesen?**  
V: A jelenlegi API statikus képekre fókuszál; animált GIF-ek nem támogatottak a függőleges egyesítéshez.

**K: Hogyan szerezhetek termelési licencet?**  
V: Vásároljon licencet a GroupDocs portálon keresztül; teszteléshez elérhető egy ideiglenes licenc.

**Last Updated:** 2026-02-13  
**Tested With:** GroupDocs.Merger latest version (as of 2026)  
**Author:** GroupDocs  

**Resources**  
- [Documentation](https://docs.groupdocs.com/merger/java/)  
- [API Reference](https://reference.groupdocs.com/merger/java/)  
- [Download](https://releases.groupdocs.com/merger/java/)  
- [Purchase](https://purchase.groupdocs.com/buy)  
- [Free trial](https://releases.groupdocs.com/merger/java/)  
- [Temporary license](https://purchase.groupdocs.com/temporary-license/)  
- [Support](https://forum.groupdocs.com/c/merger/)