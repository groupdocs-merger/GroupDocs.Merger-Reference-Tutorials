---
date: '2025-12-19'
description: Dowiedz się, jak osadzać pliki PDF w dokumentach Word i dodawać PDF do
  plików Word przy użyciu GroupDocs.Merger dla Javy. Szczegółowy poradnik krok po
  kroku, umożliwiający płynne osadzanie OLE.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: Jak osadzić plik PDF w Wordzie przy użyciu GroupDocs.Merger dla Javy – Kompletny
  przewodnik
type: docs
url: /pl/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# Jak osadzić PDF w Wordzie przy użyciu GroupDocs.Merger dla Javy

Osadzenie pliku PDF bezpośrednio w dokumencie Word może znacznie poprawić współpracę, ponieważ czytelnicy nie muszą już przełączać się między plikami. W tym przewodniku odkryjesz **jak osadzić PDF w Wordzie** przy użyciu GroupDocs.Merger dla Javy oraz zobaczysz praktyczne wskazówki dotyczące **dodawania PDF do Worda** w przepływach pracy. Przejdziemy przez wszystko, od konfiguracji biblioteki po dostosowanie rozmiaru i położenia obiektu OLE.

## Szybkie odpowiedzi
- **Jakiej biblioteki wymaga?** GroupDocs.Merger for Java (latest version)  
- **Czy mogę osadzić dowolny typ pliku?** Tak – PDFs, images, spreadsheets, etc., as OLE objects  
- **Czy potrzebuję licencji?** Darmowa wersja próbna działa w środowisku deweloperskim; licencja komercyjna jest wymagana w produkcji  
- **Które IDE Java działa najlepiej?** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **Jak długo trwa implementacja?** Około 10‑15 minut dla podstawowego osadzenia  

## Co to jest osadzanie PDF w Wordzie?
Osadzenie PDF tworzy obiekt OLE (Object Linking and Embedding) wewnątrz pliku Word. PDF pozostaje w pełni funkcjonalny — użytkownicy mogą dwukrotnie kliknąć ikonę, aby otworzyć go w przeglądarce PDF, podczas gdy dokument Word pozostaje samodzielny.

## Dlaczego dodawać PDF do Worda przy użyciu GroupDocs.Merger?
- **Dokumentacja z jednego źródła:** Trzymaj umowy, podręczniki lub raporty razem, bez zewnętrznych linków.  
- **Poprawiona dostępność:** Czytelnicy mogą przeglądać PDF bez opuszczania środowiska Word.  
- **Przyjazne automatyzacji:** Idealne do programowego generowania raportów zbiorczych lub pakietów prawnych.  

## Wymagania wstępne
- **Biblioteki i zależności:** Include the GroupDocs.Merger library via Maven or Gradle.  
- **Środowisko programistyczne:** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **Podstawowa wiedza:** Familiarity with Java and document manipulation concepts.  

## Konfiguracja GroupDocs.Merger dla Javy
Aby osadzić obiekty OLE, najpierw dodaj bibliotekę do swojego projektu.

### Maven
Dodaj tę zależność do pliku `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Umieść to w pliku `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Bezpośrednie pobranie
Alternatywnie, pobierz najnowszą wersję ze [strony wydań GroupDocs.Merger dla Javy](https://releases.groupdocs.com/merger/java/).

**Pozyskanie licencji:** Możesz rozpocząć od darmowej wersji próbnej lub uzyskać tymczasową licencję, aby ocenić funkcje przed zakupem. Odwiedź [Purchase GroupDocs](https://purchase.groupdocs.com/buy) po więcej szczegółów.

## Podstawowa inicjalizacja
Zaimportuj wymagane klasy, aby móc pracować z obiektami OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Przewodnik krok po kroku, jak osadzić PDF w Wordzie

### Krok 1: Zdefiniuj ścieżki plików i docelową stronę
Ustaw źródłowy dokument Word, PDF, który chcesz osadzić, oraz miejsce, w którym ma pojawić się obiekt OLE.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – ścieżka do istniejącego pliku Word.  
- **`embeddedFilePath`** – PDF, który chcesz **dodać PDF do Worda**.  
- **`outputFilePath`** – miejsce, w którym zostanie zapisany nowy dokument.  
- **`pageNumber`** – strona, na której będzie znajdował się obiekt OLE.  

### Krok 2: Skonfiguruj OleWordProcessingOptions
Dostosuj wygląd osadzonego PDF, ustawiając jego wymiary.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – kontrolują, jak duża ikona PDF pojawia się w dokumencie Word.  

### Krok 3: Zainicjalizuj Merger i zaimportuj obiekt OLE
Utwórz instancję `Merger` dla dokumentu źródłowego, zaimportuj obiekt OLE i zapisz wynik.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – przyjmuje `OleWordProcessingOptions` i wstawia PDF jako obiekt OLE.  
- **`save()`** – zapisuje zmodyfikowany dokument do `outputFilePath`.  

### Krok 4: (Opcjonalnie) Ponownie zastosuj konfigurację dla dodatkowych obiektów
Jeśli potrzebujesz osadzić więcej PDF‑ów, powtórz **Krok 1‑3** z nowymi ścieżkami plików i numerami stron. Ta sama klasa `OleWordProcessingOptions` pozwala kontrolować każdy obiekt indywidualnie.

## Konfigurowanie OleWordProcessingOptions (Zaawansowane)
Możesz dodatkowo dostosować położenie, np. wyrównując obiekt lub dodając podpis. Poniższy fragment kodu powtarza podstawową konfigurację dla przejrzystości:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Praktyczne zastosowania
Osadzanie PDF‑ów jest przydatne w wielu rzeczywistych scenariuszach:

1. **Podręczniki techniczne** – Wstaw szczegółowe schematy lub referencyjne PDF‑y bezpośrednio do przewodnika.  
2. **Raporty finansowe** – Dodaj dodatkowe PDF‑y z audytu, nie przerywając przepływu głównego raportu.  
3. **Umowy prawne** – Dołącz aneksy lub załączniki jako obiekty OLE, aby łatwo uzyskać do nich dostęp podczas przeglądu.  

## Wskazówki dotyczące wydajności
Podczas pracy z dużymi dokumentami lub wieloma obiektami OLE, pamiętaj o następujących wskazówkach:

- **Usuń niepotrzebną zawartość** – osadzaj tylko te strony, które naprawdę potrzebujesz.  
- **Zarządzaj pamięcią** – użyj flagi `-Xmx` Javy, aby przydzielić wystarczającą pamięć stosu dla dużych plików.  
- **Bądź na bieżąco** – nowsze wersje GroupDocs.Merger często zawierają optymalizacje wydajności.  

## Najczęściej zadawane pytania

**Q: Czym jest osadzanie OLE?**  
A: Osadzanie pozwala wstawiać obiekty, takie jak PDF‑y, do dokumentów Word jako linki, które zachowują swoją pierwotną funkcjonalność.

**Q: Czy mogę osadzić wiele obiektów OLE w jednym dokumencie?**  
A: Tak, każdy może być skonfigurowany dla różnych stron i rozmiarów przy użyciu osobnych `OleWordProcessingOptions`.

**Q: Czy istnieje limit rozmiaru osadzonych plików?**  
A: Limit jest zazwyczaj określany przez własne ograniczenia Worda, ale GroupDocs.Merger radzi sobie efektywnie z dużymi plikami.

**Q: Jak rozwiązać błędy osadzania?**  
A: Sprawdź, czy ścieżki plików są poprawne i czy JVM ma wystarczającą pamięć. Upewnij się, że źródłowy PDF nie jest uszkodzony.

**Q: Czy mogę modyfikować osadzone obiekty po wstawieniu?**  
A: Możesz ponownie otworzyć plik Word w Microsoft Word i edytować obiekt OLE, lub ponownie uruchomić kod Merger z zaktualizowanymi opcjami.

## Dodatkowe zasoby
- [Dokumentacja GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Referencja API](https://reference.groupdocs.com/merger/java/)
- [Pobierz najnowszą wersję](https://releases.groupdocs.com/merger/java/)
- [Zakup GroupDocs](https://purchase.groupdocs.com/buy)
- [Bezpłatna wersja próbna](https://releases.groupdocs.com/merger/java/)
- [Licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/)
- [Forum wsparcia](https://forum.groupdocs.com/c/merger/)

---

**Ostatnia aktualizacja:** 2025-12-19  
**Testowano z:** GroupDocs.Merger for Java latest version  
**Autor:** GroupDocs  

---