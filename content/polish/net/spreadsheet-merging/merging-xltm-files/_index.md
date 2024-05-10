---
title: Łączenie plików XLTM
linktitle: Łączenie plików XLTM
second_title: GroupDocs.Merger API .NET
description: Dowiedz się, jak programowo łączyć pliki XLTM. Przewodnik krok po kroku z przykładami kodu.
type: docs
weight: 16
url: /pl/net/spreadsheet-merging/merging-xltm-files/
---
## Wstęp
W tym samouczku przyjrzymy się, jak scalić pliki XLTM (szablon programu Excel z obsługą makr). GroupDocs.Merger dla .NET to potężna biblioteka, która umożliwia programistom programowe manipulowanie i łączenie różnych formatów dokumentów. Ten przewodnik przeprowadzi Cię krok po kroku przez proces łączenia plików XLTM przy użyciu języka C#.
## Warunki wstępne
Przed rozpoczęciem upewnij się, że spełnione są następujące wymagania wstępne:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość programowania w języku C#.
-  Zainstalowana biblioteka GroupDocs.Merger for .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/merger/net/).
- Dostęp do plików XLTM, które chcesz scalić.

## Importuj przestrzenie nazw
Rozpocznij od zaimportowania niezbędnych przestrzeni nazw do projektu C#.
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

Zajmijmy się teraz łączeniem plików XLTM.
## Krok 1: Zainicjuj katalog wyjściowy
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xltm");
```
 Zastępować`"Your Output Directory"` ze ścieżką, w której chcesz zapisać scalony plik XLTM.
## Krok 2: Połącz pliki XLTM
```csharp
// Załaduj źródłowy plik XLTM
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Dodaj kolejny plik XLTM do scalania
    merger.Join("Your Sample File");
    //Scal pliki XLTM i zapisz wynik
    merger.Save(outputFile);
}
```
W tym fragmencie kodu:
- „Twój przykładowy plik” i „Twój przykładowy plik” reprezentują ścieżki do wejściowych plików XLTM. Pamiętaj, aby zastąpić je rzeczywistymi ścieżkami plików.
## Krok 3: Wyświetl lokalizację wyjściową
```csharp
Console.WriteLine("\nXLTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
Ten kod wyświetli komunikat wskazujący pomyślne zakończenie operacji scalania wraz ze ścieżką do katalogu wyjściowego.

## Wniosek
Wykonując ten samouczek, nauczyłeś się łączyć pliki XLTM. Ta biblioteka oferuje szerokie możliwości manipulowania dokumentami, zapewniając programistom solidny zestaw narzędzi do programowej obsługi zadań związanych z dokumentami.

## Często zadawane pytania
### Czy GroupDocs.Merger może łączyć inne formaty dokumentów oprócz XLTM?
Tak, GroupDocs.Merger obsługuje łączenie różnych formatów dokumentów, takich jak DOCX, XLSX, PPTX, PDF i innych.
### Czy GroupDocs.Merger wymaga licencji do użytku komercyjnego?
 Tak, będziesz potrzebować ważnej licencji, aby używać GroupDocs.Merger w środowisku komercyjnym. Można uzyskać licencję[Tutaj](https://purchase.groupdocs.com/buy).
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Merger?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Merger[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację dotyczącą GroupDocs.Merger?
Możesz zapoznać się z pełną dokumentacją GroupDocs.Merger[Tutaj](https://reference.groupdocs.com/merger/net/).
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Merger?
 Aby uzyskać pomoc techniczną i wsparcie, odwiedź forum GroupDocs.Merger[Tutaj](https://forum.groupdocs.com/c/merger/32).