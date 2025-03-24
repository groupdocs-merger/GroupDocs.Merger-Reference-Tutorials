---
title: Jak sloučit soubory 7z
linktitle: Jak sloučit soubory 7z
second_title: GroupDocs.Merger .NET API
description: Bez námahy slučujte soubory 7z pomocí GroupDocs.Merger pro .NET. Postupujte podle našeho podrobného průvodce a plynule zkombinujte více archivů do jednoho.
weight: 10
url: /cs/net/merge-compress-files/merge-7z-files/
---

# Jak sloučit soubory 7z

## Úvod
Slučování souborů 7z lze efektivně provádět pomocí GroupDocs.Merger for .NET, výkonné knihovny pro manipulaci s dokumenty. Tento tutoriál vás provede procesem krok za krokem a umožní vám bezproblémově sloučit soubory 7z s lehkostí.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
- Visual Studio nainstalované ve vašem systému.
-  Nainstalovaná knihovna GroupDocs.Merger for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/merger/net/).
- Základní znalost programování v C#.

## Import jmenných prostorů
Nejprve do kódu C# zahrňte potřebné jmenné prostory:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Krok 1: Načtěte zdrojový soubor 7Z
Začněte zadáním výstupního adresáře a názvu souboru pro sloučený soubor 7z:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Krok 2: Sloučení souborů 7Z
Načtěte zdrojový soubor 7Z a přidejte další soubor 7Z, který chcete sloučit:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Krok 3: Uložte sloučený soubor 7Z
Proveďte operaci sloučení a uložte výsledný sloučený soubor 7Z:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Závěr
V tomto tutoriálu jsme prozkoumali, jak sloučit soubory 7z pomocí GroupDocs.Merger pro .NET. Dodržením těchto jednoduchých kroků můžete efektivně zkombinovat více souborů 7z do jediného sjednoceného archivu.

## FAQ
### Mohu sloučit více než dva soubory 7z pomocí GroupDocs.Merger?
 Ano, pomocí této knihovny můžete sloučit libovolný počet souborů 7z dohromady. Jednoduše přidejte každý soubor pomocí`Join` metoda.
### Je GroupDocs.Merger for .NET kompatibilní s jinými formáty archivů?
Ano, GroupDocs.Merger podporuje slučování různých formátů dokumentů, včetně archivů jako ZIP, 7z a RAR.
### Kde najdu další podporu nebo pomoc s GroupDocs.Merger?
 Pro další pomoc navštivte stránku[Fórum GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### Mohu vyzkoušet GroupDocs.Merger pro .NET před nákupem?
 Ano, funkce GroupDocs.Merger můžete prozkoumat stažením souboru[zkušební verze zdarma](https://releases.groupdocs.com/).
### Jak mohu získat dočasnou licenci pro GroupDocs.Merger?
 Pokud potřebujete dočasnou licenci, navštivte[tady](https://purchase.groupdocs.com/temporary-license/).