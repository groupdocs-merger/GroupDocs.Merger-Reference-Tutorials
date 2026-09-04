---
date: '2026-08-31'
description: Lär dig hur du extraherar sidor från docx-, pdf- och Word-filer med GroupDocs.Merger
  för .NET. Följ den här steg‑för‑steg C#‑guiden för att effektivisera din dokumenthantering.
keywords:
- extract pages from docx
- how to extract pages
- extract pages from pdf
- extract pages from word
lastmod: '2026-08-31'
og_description: Lär dig hur du extraherar sidor från docx-, pdf- och Word-filer med
  GroupDocs.Merger för .NET. Följ den här steg‑för‑steg C#‑guiden.
og_image_alt: Guide to extracting specific pages from documents with GroupDocs.Merger
  in C#
og_title: Extrahera sidor från docx med GroupDocs.Merger för .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract pages from docx, pdf, and word files using GroupDocs.Merger
    for .NET. Follow this step‑by‑step C# guide to streamline your document management.
  headline: How to extract pages from docx with GroupDocs.Merger for .NET in C#
  type: TechArticle
- description: Learn how to extract pages from docx, pdf, and word files using GroupDocs.Merger
    for .NET. Follow this step‑by‑step C# guide to streamline your document management.
  name: How to extract pages from docx with GroupDocs.Merger for .NET in C#
  steps:
  - name: set up file paths
    text: Define where the source document lives and where the extracted file should
      be saved. **Explanation:** Replace `YOUR_DOCUMENT_DIRECTORY` and `YOUR_OUTPUT_DIRECTORY`
      with real folder paths on your machine or server.
  - name: specify pages to extract
    text: Create an `ExtractOptions` instance that tells the Merger which pages to
      pull out. **Explanation:** The `Pages` array lists the page numbers you want.
      Change the values to match your use case (e.g., `new[] {2, 5, 7}`).
  - name: create the Merger object
    text: Instantiate `Merger` inside a `using` block so resources are released automatically.
      **Explanation:** The `using` statement guarantees that file handles are closed,
      preventing file‑lock issues in multi‑threaded environments.
  - name: extract and save
    text: Call `ExtractPages` with your options, then persist the result with `Save`.
      **Explanation:** The `Save` method writes the new document to `outputPath`.
      You can choose any supported output format by changing the file extension (e.g.,
      `.pdf`).
  type: HowTo
- questions:
  - answer: Yes, list any page numbers in the `Pages` array of `ExtractOptions`; the
      library will pull them in the order you specify.
    question: Can I extract non‑sequential pages?
  - answer: Over 70 formats, including DOCX, PDF, PPTX, XLSX, HTML, SVG, and common
      image types like PNG and JPEG.
    question: What document formats does GroupDocs.Merger support?
  - answer: No hard limit; performance depends on system memory and CPU. The library
      can handle hundreds of pages efficiently.
    question: Is there a limit on how many pages I can extract at once?
  - answer: Yes. Supply the password via `LoadOptions.Password` when creating the
      `Merger` instance.
    question: Does GroupDocs.Merger work with password‑protected files?
  - answer: Enclose the extraction code in a `try‑catch` block and log `MergerException`
      details to diagnose issues such as unsupported formats or I/O errors.
    question: How should I handle exceptions during extraction?
  type: FAQPage
tags:
- extract pages
- GroupDocs.Merger
- .NET document processing
title: Hur man extraherar sidor från docx med GroupDocs.Merger för .NET i C#
type: docs
url: /sv/net/document-extraction/extract-pages-groupdocs-merger-dotnet-csharp/
weight: 1
---

# Hur man extraherar sidor från docx med GroupDocs.Merger för .NET i C#

## Snabba svar
- **Vilket bibliotek hanterar sidextrahering?** GroupDocs.Merger för .NET.
- **Kan jag extrahera icke‑sekventiella sidor?** Ja, ange valfria sidnummer i en array.
- **Stödda format?** Över 70 format, inklusive DOCX, PDF, PPTX, XLSX och bilder.
- **Behöver jag en licens för produktion?** En giltig GroupDocs.Merger‑licens krävs för kommersiell användning.
- **Typisk implementeringstid?** Ungefär 10‑15 minuter för ett grundläggande extraheringsförfarande.

## Vad är “extract pages from docx”?
`extract pages from docx` är operationen att välja enskilda sidor från ett DOCX‑dokument (eller något annat stödd format) och spara dem som ett nytt, mindre dokument. GroupDocs.Merger utför detta utan att ladda hela filen i minnet, vilket håller minnesanvändningen låg även för filer med flera hundra sidor.

## Varför använda GroupDocs.Merger för .NET?
GroupDocs.Merger stöder **70+ in‑ och utdataformat** och kan bearbeta dokument upp till **500 sidor** samtidigt som den använder mindre än **100 MB RAM** på en vanlig server. Biblioteket körs på .NET Core, .NET 5/6/7 och hela .NET Framework, vilket ger dig plattformsoberoende flexibilitet utan att behöva Microsoft Office installerat.

## Förutsättningar
- **GroupDocs.Merger‑bibliotek** installerat i ditt projekt (se installation nedan).  
- **.NET‑runtime**: .NET 6 eller senare rekommenderas; .NET Core 3.1 eller .NET Framework 4.7.2 fungerar också.  
- Grundläggande kunskap om C#‑syntax och filsökvägar.

## Så här ställer du in GroupDocs.Merger för .NET

### Installationsinstruktioner

**Med .NET CLI:**  

```shell
dotnet add package GroupDocs.Merger
```  

**Med Package Manager Console i Visual Studio:**  

```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI:**  
- Öppna ditt projekt i Visual Studio.  
- Navigera till *Manage NuGet Packages*.  
- Sök efter **GroupDocs.Merger** och installera den senaste stabila versionen.

### Licensanskaffning
GroupDocs erbjuder en gratis provperiod för att testa funktionerna. För produktionsmiljöer, skaffa en tillfällig eller fullständig licens genom att besöka [GroupDocs’ purchase page](https://purchase.groupdocs.com/buy).

När paketet har lagts till kan du börja använda API‑et:

```csharp
using GroupDocs.Merger;
```  

## Hur extraherar man specifika sidor från ett dokument?

För att extrahera specifika sidor, ladda först källdokumentet med Merger‑klassen, skapa sedan ett `ExtractOptions`‑objekt som listar de önskade sidnumren. Anropa `ExtractPages` med dessa alternativ och spara slutligen det resulterande dokumentet till mål‑sökvägen. Detta fungerar för alla stödda format och hanterar stora filer effektivt.

### Steg 1: ange filsökvägar
Definiera var källdokumentet finns och var den extraherade filen ska sparas.

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.docx");
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "extracted_pages.docx");
```  

**Förklaring:** Ersätt `YOUR_DOCUMENT_DIRECTORY` och `YOUR_OUTPUT_DIRECTORY` med faktiska mappvägar på din maskin eller server.

### Steg 2: ange sidor att extrahera
Skapa en `ExtractOptions`‑instans som talar om för Merger vilka sidor som ska tas ut.

```csharp
ExtractOptions extractOptions = new ExtractOptions(new int[] { 1, 4 });
```  

**Förklaring:** `Pages`‑arrayen listar de sidnummer du vill ha. Ändra värdena så de matchar ditt användningsfall (t.ex. `new[] {2, 5, 7}`).

### Steg 3: skapa Merger‑objektet
Instansiera `Merger` i ett `using`‑block så att resurser frigörs automatiskt.

```csharp
using (Merger merger = new Merger(filePath))
{
    // Code to extract pages will go here.
}
```  

**Förklaring:** `using`‑satsen garanterar att filhandtag stängs, vilket förhindrar lås‑problem i flertrådade miljöer.

### Steg 4: extrahera och spara
Anropa `ExtractPages` med dina alternativ och skriv sedan resultatet med `Save`.

```csharp
// Extract specified pages from the document
merger.ExtractPages(extractOptions);

// Save the resultant document with extracted pages
merger.Save(filePathOut);
```  

**Förklaring:** `Save`‑metoden skriver det nya dokumentet till `outputPath`. Du kan välja vilket stödd utdataformat som helst genom att ändra filändelsen (t.ex. `.pdf`).

## Vanliga problem och lösningar
- **Filsökvägsfel:** Dubbelkolla att mapparna finns och att applikationen har läs‑/skrivrättigheter.  
- **Ej stödd format:** Verifiera att källfilens typ finns listad i [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/net/).  
- **Krypterade dokument:** Ange lösenordet via `LoadOptions.Password` innan extrahering.  

## Praktiska tillämpningar
Att extrahera sidor är användbart i många verkliga scenarier:
1. **Juridiska underlag:** Ta bara ut relevanta klausuler för ärendegranskning.  
2. **Utbildning:** Skapa anpassade studiepaket från läroböcker.  
3. **Affärsintelligens:** Dela korta avsnitt av långa årsrapporter.  
4. **Hälsovård:** Isolera patient‑specifika sidor från stora medicinska journaler medan övrig data hålls säker.  

## Prestandaöverväganden
- **Resursoptimering:** Wrappa alltid `Merger` i ett `using`‑block för att snabbt frigöra ohanterade resurser.  
- **Minnesanvändning:** Biblioteket strömmar sidor, så även ett dokument med 1 000 sidor håller sig under 150 MB RAM.  
- **Asynkron bearbetning:** För batchjobb, överväg `Task.Run` eller `Parallel.ForEach` för att extrahera sidor parallellt, med hänsyn till CPU‑kärnor.

## Vanliga frågor

**Q: Kan jag extrahera icke‑sekventiella sidor?**  
A: Ja, lista valfria sidnummer i `Pages`‑arrayen i `ExtractOptions`; biblioteket hämtar dem i den ordning du anger.

**Q: Vilka dokumentformat stöder GroupDocs.Merger?**  
A: Över 70 format, inklusive DOCX, PDF, PPTX, XLSX, HTML, SVG och vanliga bildtyper som PNG och JPEG.

**Q: Finns det någon gräns för hur många sidor jag kan extrahera åt gången?**  
A: Ingen hård gräns; prestandan beror på systemets minne och CPU. Biblioteket kan hantera hundratals sidor effektivt.

**Q: Fungerar GroupDocs.Merger med lösenordsskyddade filer?**  
A: Ja. Ange lösenordet via `LoadOptions.Password` när du skapar `Merger`‑instansen.

**Q: Hur bör jag hantera undantag under extrahering?**  
A: Omge extraheringskoden med ett `try‑catch`‑block och logga detaljer från `MergerException` för att diagnostisera problem som ej stödda format eller I/O‑fel.

## Ytterligare resurser
- **Dokumentation:** [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/net/)  
- **API‑referens:** [API Reference](https://reference.groupdocs.com/merger/net/)  
- **Senaste releaser:** [Latest Releases](https://releases.groupdocs.com/merger/net/)  
- **Köpalternativ:** [Buy GroupDocs.Merger](https://purchase.groupdocs.com/buy)  
- **Gratis provperiod:** [Try for Free](https://releases.groupdocs.com/merger/net/)  
- **Tillfällig licens:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Community‑support:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/)

---

**Senast uppdaterad:** 2026-08-31  
**Testat med:** GroupDocs.Merger 23.12 för .NET  
**Författare:** GroupDocs

## Relaterade handledningar

- [How to Remove Pages from Documents Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/page-operations/groupdocs-merger-remove-pages-net-tutorial/)
- [How to Move Pages Within a Document Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/page-operations/move-pages-groupdocs-merger-dotnet/)
- [Rotate PDF Pages in .NET Using GroupDocs.Merger: A Step-by-Step Guide](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)