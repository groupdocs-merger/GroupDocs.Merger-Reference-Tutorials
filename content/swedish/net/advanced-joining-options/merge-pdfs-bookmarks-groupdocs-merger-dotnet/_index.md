---
date: '2026-08-20'
description: Lär dig hur du slår ihop PDF-filer med bokmärken med GroupDocs.Merger
  for .NET, inklusive installation, kodexempel och bästa praxis för att kombinera
  PDF-dokument.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Lär dig hur du slår ihop PDF-filer med bokmärken med GroupDocs.Merger
  for .NET. Följ steg‑för‑steg‑kod för att kombinera PDF-dokument samtidigt som du
  bevarar navigering.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Hur du slår ihop PDF-filer med bokmärken med GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Hur du slår ihop PDF-filer med bokmärken med GroupDocs.Merger for .NET
type: docs
url: /sv/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Hur man slår ihop pdf-filer med bokmärken med GroupDocs.Merger för .NET

Att slå ihop flera PDF-filer samtidigt som deras ursprungliga bokmärken bevaras kan spara dig timmar av manuell omorganisering. I den här handledningen kommer du att lära dig hur du **slår ihop pdf-filer med bokmärken** med GroupDocs.Merger för .NET, från projektuppsättning till ett komplett, produktionsklart kodexempel.

## Snabba svar
- **Vilket bibliotek stödjer sammanslagningar som bevarar bokmärken?** GroupDocs.Merger för .NET.  
- **Kan jag slå ihop mer än två PDF-filer samtidigt?** Ja – lägg till så många källfiler du behöver.  
- **Behöver jag en licens för utveckling?** En gratis provversion fungerar för testning; en permanent licens krävs för produktion.  
- **Stöds .NET Core?** Absolut – biblioteket fungerar med .NET Core, .NET 5/6 och hela .NET Framework.  
- **Vad är den största filstorleken som den kan hantera?** Upp till 2 GB per dokument, bearbetat utan att ladda hela filen i minnet.

## Vad är sammanslagning av pdf-filer med bokmärken?
**Att slå ihop pdf-filer med bokmärken** betyder att ta flera PDF-dokument och kombinera dem till en enda fil samtidigt som varje källdokuments bokmärkeshierarki bevaras. Den resulterande PDF-filen behåller den ursprungliga navigationsstrukturen, vilket låter läsare hoppa direkt till de sektioner som kommer från varje enskild fil, vilket är viktigt för stora rapporter eller sammansatta manualer.

## Varför slå ihop pdf-filer med bokmärken?
Att bevara bokmärken när PDF-filer slås ihop förbättrar navigeringen i konsoliderade dokument, så att användare snabbt kan hitta specifika kapitel eller sektioner utan att behöva bläddra igenom hela filen. GroupDocs.Merger behåller den ursprungliga strukturen, minskar manuellt omorganiseringsarbete och stödjer stora filer upp till 2 GB med minimal minnesanvändning, vilket gör det idealiskt för arbetsflöden i företagsstorlek.

## Förutsättningar
- **.NET Core SDK** (3.1 eller senare) eller **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** eller någon IDE som stödjer .NET-utveckling.  
- Grundläggande kunskaper i C# och erfarenhet av fil‑I/O.  

## Konfigurera GroupDocs.Merger för .NET

### Installation
Lägg till biblioteket i ditt projekt med ett av följande kommandon:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Sök efter “GroupDocs.Merger” och installera den senaste versionen.

### Licensanskaffning
- **Gratis provversion:** Ladda ner från sidan [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Tillfällig licens:** Skaffa en via [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Full licens:** Köp på [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).  

### Grundläggande initiering
`Merger`-klassen är ingångspunkten för alla sammanslagningsoperationer.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Detta namnrymd ger dig åtkomst till hela uppsättningen av PDF-manipuleringsfunktioner.

## Hur man slår ihop pdf-filer med bokmärken i .NET

Läs in din primära PDF, konfigurera bokmärkeshantering, lägg till ytterligare filer och spara resultatet – allt i några korta kodrader.

**Direkt svar (40‑70 ord):** Skapa en `Merger`-instans med den första PDF-filen, aktivera `PdfJoinOptions.UseBookmarks`, lägg till varje efterföljande PDF via `Join` och anropa `Save` för att skriva den kombinerade filen. Detta tillvägagångssätt bevarar varje ursprunglig bokmärkeshierarki och körs i ett enda pass, vilket minimerar minnesanvändningen.

### Steg 1: definiera katalogvägar
Ställ in käll- och utmatningsmappar så att koden kan hitta de PDF-filer du vill slå ihop.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Steg 2: läs in den primära PDF-filen
`Merger` representerar huvuddokumentet som du kommer att lägga till andra i.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Steg 3: konfigurera alternativ för att bevara bokmärken
`PdfJoinOptions` styr hur sammanslagningen beter sig; flaggan `UseBookmarks` talar om för motorn att behålla befintliga bokmärken.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Steg 4: lägg till ytterligare PDF-filer
Anropa `Join` för varje extra fil. Biblioteket slår automatiskt ihop deras bokmärkes‑träd under huvuddokumentets struktur.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Steg 5: spara den sammanslagna PDF-filen
Ange utmatningssökvägen och formatet; biblioteket skriver en enda PDF som behåller alla bokmärkespunkter.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Vanliga problem och lösningar
- **Saknade bokmärken:** Verifiera att `UseBookmarks = true` i `PdfJoinOptions`.  
- **Sökvägsfel:** Använd `Path.Combine` och kontrollera att filen finns innan sammanslagning.  
- **Stora filer orsakar minnesspikar:** Processa PDF-filer sekventiellt och frigör `Merger`-objektet efter varje sparning.

## Praktiska tillämpningar
1. **Konsolidera finansiella rapporter** – håll kvartalssektioner omedelbart åtkomliga via bokmärken.  
2. **Kursmaterialpaket** – slå ihop föreläsnings‑PDF:er samtidigt som kapitelnavigering bevaras för studenter.  
3. **Projekt‑dokumentationspaket** – kombinera designspecifikationer, testplaner och versionsnoteringar till en enda, sökbar fil.

## Prestandaöverväganden
- Processa en fil åt gången när du slår ihop mer än 20 PDF-filer för att hålla RAM-användningen låg.  
- Använd den senaste .NET-runtime (t.ex. .NET 6) för optimal JIT-kompilering och skräpsamlingsprestanda.  
- För PDF-filer större än 500 MB, aktivera streamingläge via `MergerSettings` för att undvika att ladda hela dokumentet i minnet.

## Vanliga frågor

**Q: Vad är GroupDocs.Merger?**  
A: GroupDocs.Merger är ett .NET-bibliotek som låter dig slå ihop, dela, rotera och på annat sätt manipulera PDF- och andra dokumentformat programmässigt.

**Q: Kan jag slå ihop mer än två PDF-filer åt gången?**  
A: Ja – anropa `Join` upprepade gånger eller skicka en samling av filsökvägar för att slå ihop valfritt antal PDF-filer i en operation.

**Q: Hur hanterar jag licensiering för produktionsanvändning?**  
A: Skaffa en permanent licens från GroupDocs köp‑sida; provlicensen fungerar endast för utvärdering och går ut efter 30 dagar.

**Q: Min sammanslagna PDF visar inga bokmärken – vad gick fel?**  
A: Se till att `PdfJoinOptions.UseBookmarks` är satt till `true` och att varje käll‑PDF faktiskt innehåller bokmärken innan sammanslagning.

**Q: Är biblioteket kompatibelt med .NET Core och .NET Framework?**  
A: Absolut – det stödjer .NET Core 3.1+, .NET 5/6 och hela .NET Framework 4.6.1+.

## Resurser
- [Dokumentation](https://docs.groupdocs.com/merger/net/)  
- [API‑referens](https://reference.groupdocs.com/merger/net/)  
- [Ladda ner GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Köp licens](https://purchase.groupdocs.com/buy)  
- [Gratis provversion](https://releases.groupdocs.com/merger/net/)  
- [Tillfällig licens](https://purchase.groupdocs.com/temporary-license/)  
- [Supportforum](https://forum.groupdocs.com/c/merger/)  

---

**Senast uppdaterad:** 2026-08-20  
**Testat med:** GroupDocs.Merger 23.11 for .NET  
**Författare:** GroupDocs

## Relaterade handledningar

- [Hur man slår ihop specifika PDF-sidor med GroupDocs.Merger för .NET: En omfattande guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Hur man enkelt förenar dokument med GroupDocs.Merger för .NET: En omfattande guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Lägg till bilagor i PDF-filer med GroupDocs.Merger för .NET: En steg‑för‑steg‑guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)