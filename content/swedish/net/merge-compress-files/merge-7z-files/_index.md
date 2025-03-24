---
title: Hur man slår ihop 7z-filer
linktitle: Hur man slår ihop 7z-filer
second_title: GroupDocs.Merger .NET API
description: Slå enkelt samman 7z-filer med GroupDocs.Merger för .NET. Följ vår steg-för-steg-guide för att kombinera flera arkiv till ett sömlöst.
weight: 10
url: /sv/net/merge-compress-files/merge-7z-files/
---
## Introduktion
Sammanfogning av 7z-filer kan göras effektivt med GroupDocs.Merger för .NET, ett kraftfullt dokumentmanipuleringsbibliotek. Denna handledning guidar dig genom processen steg för steg, så att du enkelt kan sammanfoga dina 7z-filer.
## Förutsättningar
Innan du börjar, se till att du har följande:
- Visual Studio installerat på ditt system.
-  GroupDocs.Merger för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/merger/net/).
- Grundläggande förståelse för C#-programmering.

## Importera namnområden
Inkludera först de nödvändiga namnrymden i din C#-kod:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Steg 1: Ladda Source 7Z File
Börja med att ange utdatakatalogen och filnamnet för den sammanslagna 7z-filen:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Steg 2: Slå samman 7Z-filer
Ladda källfilen 7Z och lägg till ytterligare en 7Z-fil som du vill slå samman:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Steg 3: Spara sammanslagen 7Z-fil
Utför sammanfogningen och spara den resulterande sammanslagna 7Z-filen:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Slutsats
I den här handledningen undersökte vi hur man slår samman 7z-filer med GroupDocs.Merger för .NET. Genom att följa dessa enkla steg kan du effektivt kombinera flera 7z-filer till ett enda enhetligt arkiv.

## FAQ's
### Kan jag slå samman fler än två 7z-filer med GroupDocs.Merger?
 Ja, du kan slå ihop valfritt antal 7z-filer med detta bibliotek. Lägg bara till varje fil med hjälp av`Join` metod.
### Är GroupDocs.Merger för .NET kompatibelt med andra arkivformat?
Ja, GroupDocs.Merger stöder sammanslagning av olika dokumentformat, inklusive arkiv som ZIP, 7z och RAR.
### Var kan jag hitta ytterligare support eller hjälp med GroupDocs.Merger?
 För ytterligare hjälp, besök[GroupDocs.Merger-forum](https://forum.groupdocs.com/c/merger/32).
### Kan jag prova GroupDocs.Merger för .NET innan jag köper?
 Ja, du kan utforska funktionerna i GroupDocs.Merger genom att ladda ner[gratis testversion](https://releases.groupdocs.com/).
### Hur kan jag få en tillfällig licens för GroupDocs.Merger?
 Om du behöver en tillfällig licens, besök[här](https://purchase.groupdocs.com/temporary-license/).