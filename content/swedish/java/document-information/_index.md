---
date: 2026-10-27
description: Lär dig hur du konverterar PDF till PNG i Java med GroupDocs.Merger,
  genererar PDF‑förhandsgranskningar, hanterar lösenordsskyddade filer och listar
  stödda format.
keywords:
- convert pdf to png java
- merge images java
- generate pdf previews java
- create pdf thumbnails java
- preview password protected pdf
lastmod: 2026-10-27
og_description: Konvertera PDF till PNG i Java med GroupDocs.Merger. Lär dig snabb
  förhandsgranskningsgenerering, hantering av lösenordsskyddade filer och lista över
  stödda format.
og_image_alt: Developer guide showing PDF to PNG conversion using GroupDocs.Merger
  for Java
og_title: Konvertera PDF till PNG i Java – GroupDocs.Merger‑guide
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  headline: How to convert PDF to PNG in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  name: How to convert PDF to PNG in Java with GroupDocs.Merger
  steps:
  - name: '**Create a `Merger` instance** – this class is the entry point for all
      document operations.'
    text: '**Create a `Merger` instance** – this class is the entry point for all
      document operations.'
  - name: '**Load the PDF** using `Document` (the class that represents a single PDF
      in memory).'
    text: '**Load the PDF** using `Document` (the class that represents a single PDF
      in memory).'
  - name: '**Configure `PreviewOptions`** to set the image format to PNG and optionally
      define DPI for higher quality.'
    text: '**Configure `PreviewOptions`** to set the image format to PNG and optionally
      define DPI for higher quality.'
  - name: '**Call `preview`** – the method writes one PNG per page to the output directory.'
    text: '**Call `preview`** – the method writes one PNG per page to the output directory.'
  type: HowTo
- questions:
  - answer: Yes. The library streams pages one at a time, so memory consumption stays
      low even for very large files.
    question: Can I generate previews for large PDFs (hundreds of pages)?
  - answer: You can specify PNG, JPEG, or BMP when configuring the preview options
      in the API.
    question: How do I change the image format of the preview?
  - answer: Absolutely. Provide the password in the load options, and the preview
      generation will work as expected.
    question: Is it possible to generate previews for encrypted documents?
  - answer: No. The core GroupDocs.Merger library includes image‑merging capabilities
      out of the box.
    question: Does “merge images java” require a special module?
  - answer: Use the “retrieve supported file types” tutorial above, which calls the
      API method that returns the complete list of over 50 formats.
    question: Where can I find the full list of formats supported by “list supported
      formats java”?
  type: FAQPage
tags:
- convert PDF
- GroupDocs.Merger
- Java document processing
- PDF preview
- image conversion
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  headline: How to convert PDF to PNG in Java with GroupDocs.Merger
  type: TechArticle
- questions:
  - answer: Yes. The library streams pages one at a time, so memory consumption stays
      low even for very large files.
    question: Can I generate previews for large PDFs (hundreds of pages)?
  - answer: You can specify PNG, JPEG, or BMP when configuring the preview options
      in the API.
    question: How do I change the image format of the preview?
  - answer: Absolutely. Provide the password in the load options, and the preview
      generation will work as expected.
    question: Is it possible to generate previews for encrypted documents?
  - answer: No. The core GroupDocs.Merger library includes image‑merging capabilities
      out of the box.
    question: Does “merge images java” require a special module?
  - answer: Use the “retrieve supported file types” tutorial above, which calls the
      API method that returns the complete list of over 50 formats.
    question: Where can I find the full list of formats supported by “list supported
      formats java”?
  type: FAQPage
title: Hur man konverterar PDF till PNG i Java med GroupDocs.Merger
type: docs
url: /sv/java/document-information/
weight: 3
---

# Hur man konverterar PDF till PNG i Java med GroupDocs.Merger

I den här omfattande guiden kommer du att lära dig **hur man konverterar PDF till PNG i Java** med GroupDocs.Merger. Oavsett om du behöver miniatyrbilder för en dokumenthanteringsportal, snabba visuella kontroller innan du slår ihop filer, eller batch‑processar stora arkiv, så guidar stegen nedan dig genom allt från grundläggande installation till hantering av lösenordsskyddade PDF‑filer. Handledningen pekar också på relaterade operationer såsom att slå ihop PNG‑bilder, lista stödjade format och hämta dokumentmetadata.

## Snabba svar
- **Vad betyder “generate previews”?** Det skapar bildrepresentationer (t.ex. PNG, JPEG) av varje sida i ett källdokument.  
- **Vilka format stöds?** Alla format som listas under “list supported formats Java” för GroupDocs.Merger, inklusive PDF, DOCX, PPTX och bildfiler.  
- **Behöver jag en licens?** En tillfällig licens fungerar för utvärdering; en full licens krävs för produktion.  
- **Kan jag generera förhandsvisningar för lösenordsskyddade filer?** Ja – ange bara lösenordet när du öppnar dokumentet.  
- **Är förhandsvisningsgenereringen snabb?** Ja, biblioteket strömmar sidor, så även stora filer behandlas effektivt.

## Vad betyder konvertera PDF till PNG i Java?
`convert PDF to PNG in Java` betyder att transformera varje sida i ett PDF‑dokument till en raster‑PNG‑bild som kan visas i webbläsare, mobilappar eller filutforskare. Denna konvertering ger användarna en visuell ögonblicksbild innan de bestämmer sig för att slå ihop, redigera eller ladda ner en fil.

## Varför generera PDF‑förhandsvisningar med GroupDocs.Merger för Java?
GroupDocs.Merger stödjer **50+ in‑ och utdataformat** och kan generera förhandsvisningar för dokument upp till **500 sidor** samtidigt som minnesanvändningen hålls under **50 MB**. Biblioteket bearbetar sidor på begäran och levererar förhandsvisningsgenerering på under **2 sekunder per sida** på en typisk 2 GHz‑CPU. Att använda GroupDocs.Merger eliminerar tredjeparts‑bildkonverterare och garanterar konsekvent rendering på Windows-, Linux‑ och macOS‑miljöer.

## Förutsättningar
- Java 8 eller högre installerat.  
- GroupDocs.Merger för Java‑biblioteket tillagt i ditt projekt (Maven/Gradle).  
- En giltig GroupDocs‑tillfällig eller fullständig licensnyckel.  

## Hur man konverterar PDF till PNG i Java?
Läs in käll‑PDF‑filen, konfigurera `PreviewOptions` för att begära PNG‑utdata och anropa förhandsvisnings‑API‑et. Biblioteket strömmar varje sida, skriver en PNG‑fil till mål‑mappen och frigör minnet omedelbart efter att varje sida har bearbetats.

### Steg‑för‑steg konvertering

1. **Create a `Merger` instance** – den här klassen är ingångspunkten för alla dokumentoperationer.  
2. **Load the PDF** using `Document` (klassen som representerar en enskild PDF i minnet).  
3. **Configure `PreviewOptions`** för att ställa in bildformatet till PNG och eventuellt definiera DPI för högre kvalitet.  
4. **Call `preview`** – metoden skriver en PNG per sida till utdata‑katalogen.  

> **Direct answer:** För att konvertera en PDF till PNG i Java med GroupDocs.Merger, skapa ett `Merger`‑objekt, läs in PDF‑filen via `Document`, sätt `PreviewOptions` till PNG och anropa `preview`. Biblioteket strömmar varje sida och skapar en separat PNG‑fil för varje sida utan att ladda hela dokumentet i minnet.

### Definition av ankare
`Merger` är den primära klassen i GroupDocs.Merger för att ladda, slå ihop och förhandsvisa dokument.  
`Document` representerar en inläst fil och ger åtkomst till dess sidor, metadata och strömhantering.  
`PreviewOptions` konfigurerar hur förhandsvisningsbilder genereras, inklusive format, DPI och sidintervall.

## Hur man förhandsvisar lösenordsskyddade PDF‑filer i Java?
`LoadOptions` är en konfigurationsklass som låter dig ange dokumentladdningsparametrar såsom lösenord, skrivskyddat läge och anpassad strömhantering. Ange lösenordet i `LoadOptions` när du konstruerar `Document`. Förhandsvisningsmotorn kommer att dekryptera filen i realtid och producera PNG‑bilder exakt som för en icke‑skyddad PDF. Detta tillvägagångssätt fungerar för alla krypterade PDF‑filer som stöds av GroupDocs.Merger och kräver ingen extra kod.

## Hur man slår ihop bilder i Java?
GroupDocs.Merger innehåller inbyggda bild‑slå‑ihop‑funktioner, så du kan kombinera flera PNG‑filer till ett enda dokument utan extra beroenden. Använd `merge`‑metoden på ett `Merger`‑objekt, lägg till varje PNG som ett separat `Document` och ange önskat utdataformat såsom PDF eller en kombinerad bild. Denna process bevarar bildkvaliteten och kräver bara några få rader kod.

## Generera pdf‑förhandsvisningar java – vanliga mönster
- **Single‑page preview:** Ställ in `PreviewOptions.setPageNumber(1)` för att bara generera den första sidans PNG.  
- **Batch preview:** Loopa igenom en katalog med PDF‑filer och tillämpa samma förhandsvisningslogik på varje fil.  
- **High‑resolution thumbnails:** Öka DPI i `PreviewOptions` till 300 för skarpa miniatyrer som är lämpliga för utskrift.

## Vanliga problem och lösningar

| Problem | Orsak | Lösning |
|-------|-------|----------|
| Out‑of‑memory‑fel på stora PDF‑filer | Laddar hela dokumentet på en gång | Se till att du använder streaming‑förhandsvisnings‑API:et (standard) och undvik att anropa `Document.getPages().size()` onödigt. |
| Tomma bilder för krypterade PDF‑filer | Saknar lösenord i `LoadOptions` | Ange alltid rätt lösenord när du konstruerar `Document`. |
| Lågt kvalitativa miniatyrer | Standard‑DPI (72) är för låg för ditt UI | Ställ in `PreviewOptions.setDpi(150)` eller högre innan du anropar `preview`. |

## Vanliga frågor

**Q: Kan jag generera förhandsvisningar för stora PDF‑filer (hundratals sidor)?**  
A: Ja. Biblioteket strömmar sidor en i taget, så minnesförbrukningen förblir låg även för mycket stora filer.

**Q: Hur ändrar jag bildformatet för förhandsvisningen?**  
A: Du kan ange PNG, JPEG eller BMP när du konfigurerar förhandsvisningsalternativen i API‑et.

**Q: Är det möjligt att generera förhandsvisningar för krypterade dokument?**  
A: Absolut. Ange lösenordet i laddningsalternativen, så fungerar förhandsvisningsgenereringen som förväntat.

**Q: Kräver “merge images java” en speciell modul?**  
A: Nej. Kärnbiblioteket GroupDocs.Merger innehåller bild‑slå‑ihop‑funktioner direkt ur lådan.

**Q: Var kan jag hitta den fullständiga listan över format som stöds av “list supported formats java”?**  
A: Använd handledningen “retrieve supported file types” ovan, som anropar API‑metoden som returnerar den kompletta listan med över 50 format.

## Tillgängliga handledningar

### [Hur man genererar dokument sidoförhandsvisningar med GroupDocs.Merger för Java](./generate-document-page-previews-groupdocs-merger-java/)
Lär dig hur du skapar dokument sidoförhandsvisningar med GroupDocs.Merger för Java. Förbättra dina applikationer genom att effektivt generera visuella representationer av dokument.

### [Hur man slår ihop PNG‑bilder med GroupDocs.Merger för Java&#58; En steg‑för‑steg‑guide](./merge-png-images-groupdocs-merger-java/)
Lär dig hur du sömlöst slår ihop PNG‑bilder med GroupDocs.Merger för Java. Denna guide täcker installation, implementering och praktiska tillämpningar med tydliga exempel.

### [Hur man hämtar stödjade filtyper med GroupDocs.Merger för Java](./retrieve-supported-file-types-groupdocs-merger-java/)
Lär dig hur du använder GroupDocs.Merger för Java för att hämta stödjade filtyper. Denna guide ger steg‑för‑steg‑instruktioner och bästa praxis.

### [Hämtning av dokumentinformation med GroupDocs.Merger för Java&#58; Steg‑för‑steg‑guide](./groupdocs-merger-java-retrieve-document-info-guide/)
Lär dig hur du använder GroupDocs.Merger för Java för att effektivt hämta dokumentmetadata, inklusive sidantal och författardetaljer. Förbättra dina Java‑applikationer idag!

## Ytterligare resurser

- [GroupDocs.Merger för Java Dokumentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger för Java API‑referens](https://reference.groupdocs.com/merger/java/)
- [Ladda ner GroupDocs.Merger för Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger‑forum](https://forum.groupdocs.com/c/merger)
- [Gratis support](https://forum.groupdocs.com/)
- [Tillfällig licens](https://purchase.groupdocs.com/temporary-license/)

## Relaterade handledningar

- [Hur man laddar en PDF från en URL med GroupDocs.Merger för Java: En omfattande guide](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [Batch‑processa dokument – Ladda lösenordsskyddade filer med GroupDocs.Merger för Java](/merger/java/document-loading/load-password-protected-docs-groupdocs-java/)
- [Hur man hämtar stödjade filtyper med GroupDocs.Merger för Java](/merger/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/)

---

**Senast uppdaterad:** 2026-10-27  
**Testad med:** GroupDocs.Merger 23.12 för Java  
**Författare:** GroupDocs