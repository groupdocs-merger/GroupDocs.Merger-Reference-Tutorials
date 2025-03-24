---
title: Jak połączyć pliki 7z
linktitle: Jak połączyć pliki 7z
second_title: GroupDocs.Merger API .NET
description: Bezproblemowo łącz pliki 7z za pomocą GroupDocs.Merger dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby płynnie połączyć wiele archiwów w jedno.
weight: 10
url: /pl/net/merge-compress-files/merge-7z-files/
---

# Jak połączyć pliki 7z

## Wstęp
Scalanie plików 7z można efektywnie wykonać za pomocą GroupDocs.Merger dla .NET, potężnej biblioteki do manipulacji dokumentami. Ten samouczek poprowadzi Cię krok po kroku przez proces, umożliwiając bezproblemowe i łatwe scalanie plików 7z.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące elementy:
- Program Visual Studio zainstalowany w systemie.
-  Zainstalowana biblioteka GroupDocs.Merger for .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/merger/net/).
- Podstawowa znajomość programowania w języku C#.

## Importuj przestrzenie nazw
Najpierw uwzględnij niezbędne przestrzenie nazw w kodzie C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Krok 1: Załaduj plik źródłowy 7Z
Rozpocznij od określenia katalogu wyjściowego i nazwy pliku dla scalonego pliku 7z:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Krok 2: Połącz pliki 7Z
Załaduj źródłowy plik 7Z i dodaj kolejny plik 7Z, który chcesz scalić:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Krok 3: Zapisz scalony plik 7Z
Wykonaj operację scalania i zapisz wynikowy scalony plik 7Z:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Wniosek
W tym samouczku omówiliśmy, jak scalić pliki 7z przy użyciu programu GroupDocs.Merger dla platformy .NET. Wykonując te proste kroki, możesz efektywnie połączyć wiele plików 7z w jedno, ujednolicone archiwum.

## Często zadawane pytania
### Czy mogę połączyć więcej niż dwa pliki 7z za pomocą GroupDocs.Merger?
 Tak, za pomocą tej biblioteki możesz połączyć dowolną liczbę plików 7z. Po prostu dodaj każdy plik za pomocą`Join` metoda.
### Czy GroupDocs.Merger for .NET jest kompatybilny z innymi formatami archiwów?
Tak, GroupDocs.Merger obsługuje łączenie różnych formatów dokumentów, w tym archiwów takich jak ZIP, 7z i RAR.
### Gdzie mogę znaleźć dodatkowe wsparcie lub pomoc dotyczącą GroupDocs.Merger?
 Aby uzyskać dalszą pomoc, odwiedź stronę[Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### Czy przed zakupem mogę wypróbować GroupDocs.Merger dla .NET?
 Tak, możesz poznać funkcjonalność GroupDocs.Merger, pobierając plik[bezpłatna wersja próbna](https://releases.groupdocs.com/).
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Merger?
 Jeśli potrzebujesz licencji tymczasowej, odwiedź stronę[Tutaj](https://purchase.groupdocs.com/temporary-license/).