---
title: Slår ihop XLS-filer
linktitle: Slår ihop XLS-filer
second_title: GroupDocs.Merger .NET API
description: Lär dig hur du sammanfogar Excel-filer i .NET med GroupDocs.Merger för sömlös dokumenthantering. Följ vår steg-för-steg handledning.
weight: 11
url: /sv/net/spreadsheet-merging/merging-xls-files/
---

# Slår ihop XLS-filer

## Introduktion
I den här handledningen kommer vi att utforska hur man slår ihop XLS-filer (Excel). GroupDocs.Merger är ett kraftfullt API för dokumentmanipulering som gör det möjligt för utvecklare att slå samman, dela, ordna om och manipulera dokument utan ansträngning i sina .NET-applikationer. Specifikt kommer vi att fokusera på att slå samman XLS-filer steg för steg med hjälp av GroupDocs.Mergers intuitiva metoder.
## Förutsättningar
Innan vi börjar, se till att du har ställt in följande förutsättningar:
- Visual Studio: Installera Visual Studio på din dator.
-  GroupDocs.Merger for .NET: Ladda ner och installera GroupDocs.Merger for .NET från[här](https://releases.groupdocs.com/merger/net/).
- .NET Framework: Se till att du har .NET Framework installerat.
- Exempel på XLS-filer: Förbered XLS-filerna som du vill slå samman.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden för att använda GroupDocs.Merger i ditt projekt:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Steg 1: Initiera Output Directory
Ange först katalogen där du vill spara den sammanslagna XLS-filen:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Steg 2: Ladda och slå samman XLS-filer
Låt oss nu ladda och slå samman XLS-filerna med GroupDocs.Merger:
```csharp
// Ladda käll XLS-filen
using (var merger = new Merger("Your Sample File"))
{
    // Lägg till ytterligare en XLS-fil för att slå samman
    merger.Join("Your Sample File");
    
    // Slå samman XLS-filer och spara resultatet
    merger.Save(outputFile);
}
```
## Steg 3: Visa utdataplats
Visa slutligen ett meddelande som anger slutförandet och platsen för den sammanslagna XLS-filen:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Slutsats
I den här handledningen har vi lärt oss hur man slår samman XLS-filer. Genom att följa de medföljande stegen kan du effektivt kombinera flera Excel-filer programmatiskt i dina .NET-applikationer.

## FAQ's
### Är GroupDocs.Merger kompatibel med andra dokumentformat?
Ja, GroupDocs.Merger stöder olika dokumentformat som PDF, DOCX, XLSX, PPTX och mer.
### Kan jag dela upp dokument med GroupDocs.Merger?
Absolut! GroupDocs.Merger låter dig dela upp dokument baserat på dina krav.
### Var kan jag hitta fler resurser och support för GroupDocs.Merger?
Du kan utforska dokumentationen och ställa frågor om[GroupDocs forum](https://forum.groupdocs.com/c/merger/32).
### Finns det en gratis testversion tillgänglig för GroupDocs.Merger?
 Ja, du kan börja med en[gratis provperiod](https://releases.groupdocs.com/) för att utvärdera funktionaliteten.
### Hur kan jag köpa en licens för GroupDocs.Merger?
 Besök[köpsidan](https://purchase.groupdocs.com/buy) att skaffa en licens anpassad efter dina behov.