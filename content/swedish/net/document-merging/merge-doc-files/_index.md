---
title: Slå samman DOC-filer med GroupDocs.Merger för .NET
linktitle: Slå samman DOC-filer med GroupDocs.Merger för .NET
second_title: GroupDocs.Merger .NET API
description: Lär dig hur du sammanfogar DOC-filer programmatiskt med GroupDocs.Merger för .NET. Följ vår steg-för-steg-guide för att sömlöst kombinera flera dokument till ett.
type: docs
weight: 10
url: /sv/net/document-merging/merge-doc-files/
---
## Introduktion
I den här handledningen kommer vi att utforska hur man slår samman DOC-filer med GroupDocs.Merger för .NET. GroupDocs.Merger för .NET är ett kraftfullt API som låter utvecklare kombinera, dela upp och manipulera olika dokumentformat programmatiskt. Genom att utnyttja detta API kan du sömlöst sammanfoga flera DOC-filer till ett enda dokument. Vi kommer att tillhandahålla steg-för-steg-instruktioner för att guida dig genom processen att slå samman DOC-filer med GroupDocs.Merger för .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1. Visual Studio: Installera Visual Studio på din utvecklingsmaskin.
2.  GroupDocs.Merger for .NET: Skaffa GroupDocs.Merger for .NET-biblioteket. Du kan ladda ner den från[hemsida](https://releases.groupdocs.com/merger/net/).
3. Kunskaper i C#: Grundläggande förståelse för programmeringsspråket C#.
## Importera namnområden
För att börja arbeta med GroupDocs.Merger för .NET, importera de nödvändiga namnrymden till ditt C#-projekt:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Steg 1: Konfigurera utdatakatalog
Börja med att ange utdatakatalogen där den sammanslagna DOC-filen ska sparas:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
 Byta ut`"Your Output Directory"` med sökvägen till önskad utdatamapp.
## Steg 2: Ladda käll-DOC-filer
Läs sedan in källdok-filerna som du vill slå samman med GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // Lägg till ytterligare en DOC-fil för att slå samman
    merger.Join("Your Sample Document File 2");
    // Slå samman DOC-filer och spara resultatet
    merger.Save(outputFile);
}
```
I det här kodavsnittet:
- `"Your Sample Document File"` och`"Your Sample Document File 2"` representerar sökvägarna till de DOC-filer du vill slå samman.
- `merger.Join(...)` används för att lägga till ytterligare en DOC-fil till sammanfogningsoperationen.
- `merger.Save(outputFile)` kombinerar de laddade DOC-filerna och sparar det sammanslagna dokumentet till den angivna utdatafilen (`merged.doc`).
 Se till att du byter ut`"Your Sample Document File"` och`"Your Sample Document File 2"` med de faktiska sökvägarna till dina DOC-filer.
## Slutsats
I den här handledningen har vi täckt processen att slå samman DOC-filer med GroupDocs.Merger för .NET. Genom att följa stegen som beskrivs ovan kan du effektivt kombinera flera DOC-filer till ett enda dokument programmatiskt. GroupDocs.Merger för .NET ger ett enkelt och effektivt sätt att manipulera dokumentformat i dina .NET-applikationer.

## FAQ's
### Kan GroupDocs.Merger för .NET hantera andra dokumentformat än DOC?
Ja, GroupDocs.Merger för .NET stöder sammanslagning av olika dokumentformat som DOCX, PDF, XLSX, PPTX och mer.
### Är GroupDocs.Merger for .NET kompatibel med .NET Core?
Ja, GroupDocs.Merger för .NET är kompatibel med .NET Core och .NET Framework.
### Kräver GroupDocs.Merger för .NET en licens för kommersiellt bruk?
 Ja, en giltig licens krävs för kommersiell användning. Du kan få en licens från[Gruppdokument](https://purchase.groupdocs.com/buy).
### Kan jag prova GroupDocs.Merger för .NET gratis?
 Ja, du kan utforska GroupDocs.Merger för .NET med en gratis provperiod tillgänglig[här](https://releases.groupdocs.com/).
### Var kan jag få teknisk support för GroupDocs.Merger för .NET?
 För teknisk assistans och gemenskapsstöd, besök[GroupDocs forum](https://forum.groupdocs.com/c/merger/32).