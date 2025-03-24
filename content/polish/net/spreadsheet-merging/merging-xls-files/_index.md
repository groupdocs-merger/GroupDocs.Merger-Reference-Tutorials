---
title: Łączenie plików XLS
linktitle: Łączenie plików XLS
second_title: GroupDocs.Merger API .NET
description: Dowiedz się, jak scalać pliki Excel w platformie .NET przy użyciu narzędzia GroupDocs.Merger w celu płynnej manipulacji dokumentami. Postępuj zgodnie z naszym samouczkiem krok po kroku.
weight: 11
url: /pl/net/spreadsheet-merging/merging-xls-files/
---

# Łączenie plików XLS

## Wstęp
W tym samouczku omówimy, jak scalić pliki XLS (Excel). GroupDocs.Merger to potężny interfejs API do manipulacji dokumentami, który umożliwia programistom łatwe łączenie, dzielenie, zmienianie kolejności i manipulowanie dokumentami w aplikacjach .NET. W szczególności skupimy się na krok po kroku łączenia plików XLS przy użyciu intuicyjnych metod GroupDocs.Merger.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz skonfigurowane następujące wymagania wstępne:
- Visual Studio: Zainstaluj Visual Studio na swoim komputerze.
-  GroupDocs.Merger dla .NET: Pobierz i zainstaluj GroupDocs.Merger dla .NET z[Tutaj](https://releases.groupdocs.com/merger/net/).
- .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET Framework.
- Przykładowe pliki XLS: Przygotuj pliki XLS, które chcesz scalić.

## Importuj przestrzenie nazw
Zacznij od zaimportowania przestrzeni nazw niezbędnych do użycia GroupDocs.Merger w swoim projekcie:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Krok 1: Zainicjuj katalog wyjściowy
Najpierw określ katalog, w którym chcesz zapisać scalony plik XLS:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Krok 2: Załaduj i scal pliki XLS
Teraz załadujmy i połączmy pliki XLS za pomocą GroupDocs.Merger:
```csharp
// Załaduj źródłowy plik XLS
using (var merger = new Merger("Your Sample File"))
{
    // Dodaj kolejny plik XLS, aby go scalić
    merger.Join("Your Sample File");
    
    // Scal pliki XLS i zapisz wynik
    merger.Save(outputFile);
}
```
## Krok 3: Wyświetl lokalizację wyjściową
Na koniec wyświetl komunikat wskazujący zakończenie i lokalizację scalonego pliku XLS:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Wniosek
W tym samouczku nauczyliśmy się łączyć pliki XLS. Wykonując podane kroki, możesz efektywnie łączyć programowo wiele plików Excel w aplikacjach .NET.

## Często zadawane pytania
### Czy GroupDocs.Merger jest kompatybilny z innymi formatami dokumentów?
Tak, GroupDocs.Merger obsługuje różne formaty dokumentów, takie jak PDF, DOCX, XLSX, PPTX i inne.
### Czy mogę dzielić dokumenty za pomocą GroupDocs.Merger?
Absolutnie! GroupDocs.Merger umożliwia dzielenie dokumentów w oparciu o Twoje wymagania.
### Gdzie mogę znaleźć więcej zasobów i wsparcia dla GroupDocs.Merger?
Możesz przeglądać dokumentację i zadawać pytania na stronie[Forum GroupDocs](https://forum.groupdocs.com/c/merger/32).
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Merger?
 Tak, możesz zacząć od[bezpłatna wersja próbna](https://releases.groupdocs.com/) aby ocenić funkcjonalność.
### Jak mogę kupić licencję na GroupDocs.Merger?
 Odwiedzić[strona zakupu](https://purchase.groupdocs.com/buy) aby nabyć licencję dostosowaną do Twoich potrzeb.