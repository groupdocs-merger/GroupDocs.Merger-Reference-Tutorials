---
title: Guide för att slå samman XLSM-filer
linktitle: Guide för att slå samman XLSM-filer
second_title: GroupDocs.Merger .NET API
description: Slå samman XLSM-filer sömlöst med GroupDocs.Merger för .NET. Kombinera effektivt Excel-arbetsböcker programmatiskt. Förbättra dina dokumenthanteringsmöjligheter.
weight: 13
url: /sv/net/spreadsheet-merging/guide-merging-xlsm-files/
---
## Introduktion
I den här handledningen kommer vi att undersöka hur man slår ihop XLSM-filer (Excel Macro-Enabled Workbook). GroupDocs.Merger är ett kraftfullt bibliotek som gör det möjligt för utvecklare att manipulera dokumentformat, inklusive sammanslagning, delning och modifiering av filer programmatiskt.
## Förutsättningar
Innan du börjar, se till att du har följande:
-  GroupDocs.Merger för .NET: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/merger/net/).
- Utvecklingsmiljö: Installera Visual Studio eller någon kompatibel .NET-utvecklingsmiljö.
- XLSM-filer: Förbered de XLSM-filer du vill slå samman.

## Importera namnområden
Inkludera först de nödvändiga namnrymden i ditt .NET-projekt:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Steg 1: Definiera utdatamapp och filnamn
Börja med att definiera utdatamappen och namnet på den sammanslagna XLSM-filen:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Steg 2: Ladda och slå samman XLSM-filer
Ladda sedan XLSM-källfilerna och slå samman dem till en enda fil:
```csharp
// Ladda källfilen XLSM
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Lägg till ytterligare en XLSM-fil för att slå samman
    merger.Join("Your Sample File");
    // Slå samman XLSM-filer och spara resultatet
    merger.Save(outputFile);
}
```
## Steg 3: Kontrollera att sammanslagningen är klar
Slutligen, meddela användaren om den framgångsrika sammanslagningen och visa utdatasökvägen:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Slutsats
Du har lärt dig hur man sammanfogar XLSM-filer programmatiskt. Det här biblioteket förenklar dokumentmanipuleringsuppgifter, vilket möjliggör effektiv filsammanfogning i dina .NET-applikationer.

## FAQ's
### Kan GroupDocs.Merger hantera stora XLSM-filer?
Ja, GroupDocs.Merger hanterar effektivt stora XLSM-filer utan prestandaproblem.
### Stöder GroupDocs.Merger andra filformat än XLSM?
Ja, GroupDocs.Merger stöder olika dokumentformat som DOCX, PDF, PPTX och mer.
### Är GroupDocs.Merger kompatibel med .NET Core-applikationer?
Ja, GroupDocs.Merger är kompatibel med både .NET Framework- och .NET Core-miljöer.
### Kan jag slå samman krypterade XLSM-filer med GroupDocs.Merger?
Ja, GroupDocs.Merger stöder sammanslagning av krypterade XLSM-filer med rätt referenser.
### Tillhandahåller GroupDocs.Merger batchbehandlingsmöjligheter?
Ja, GroupDocs.Merger tillåter batchbearbetning för att slå samman flera XLSM-filer samtidigt.