---
date: '2026-09-21'
description: Узнайте, как встроить PDF в электронные таблицы Excel с помощью GroupDocs.Merger
  for .NET, улучшая представление данных и их функциональность.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Узнайте, как встроить PDF в Excel с помощью GroupDocs.Merger for .NET.
  Следуйте пошаговым инструкциям, получайте быстрые ответы и избегайте распространённых
  ошибок.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Как встроить PDF в Excel с помощью GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: Как встроить PDF в Excel с помощью GroupDocs.Merger for .NET
type: docs
url: /ru/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Как встроить PDF в Excel с помощью GroupDocs.Merger для .NET

## Введение

Встраивание PDF в Excel позволяет хранить вспомогательные документы — такие как контракты, отчёты или спецификации — прямо там, где находятся данные. С помощью **GroupDocs.Merger for .NET** вы можете добавлять OLE‑объекты в ячейки всего в несколько строк кода, превращая обычную таблицу в интерактивную, автономную книгу. Этот учебник проведёт вас через всё, что нужно знать, от установки до устранения неполадок.

**Что вы узнаете**

- Как настроить GroupDocs.Merger for .NET в проекте C#  
- Точные шаги по встраиванию PDF (или любого совместимого с OLE файла) в ячейку Excel  
- Параметры конфигурации, советы по производительности и распространённые подводные камни  

Убедимся, что у вас всё готово, прежде чем начать.

## Быстрые ответы
- **Можно ли встроить любой тип файла?** Да — любой формат, поддерживаемый как OLE‑объект (PDF, Word, изображение и т.д.).  
- **Нужна ли лицензия для разработки?** Бесплатная пробная версия подходит для тестирования; постоянная лицензия требуется для продакшн.  
- **Какие версии .NET поддерживаются?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **Увеличится ли размер файла Excel существенно?** Только на размер встроенного документа; держите файлы размером до нескольких МБ для лучшей производительности.  
- **Есть ли ограничение на количество OLE‑объектов?** Практически нет, но очень большие книги могут влиять на время загрузки.

## Что такое встраивание PDF в Excel?

Встраивание PDF в Excel вставляет весь PDF как OLE‑объект, который можно открыть непосредственно из таблицы. Пользователи нажимают на иконку и просматривают оригинальный документ, не покидая Excel. Такой подход сохраняет оригинальное оформление, обеспечивает быстрый доступ и устраняет необходимость управлять отдельными файлами. Встроенный PDF ведёт себя как любой другой OLE‑объект, позволяя пользователям двойным щелчком запускать просмотрщик PDF, оставаясь в среде Excel.

## Почему встраивать OLE‑объекты в Excel?

GroupDocs.Merger поддерживает **120+ входных и выходных форматов** и может встраивать объекты без загрузки всего файла в память, обеспечивая быструю обработку PDF‑документов со сотнями страниц. Это уменьшает необходимость в отдельных хранилищах файлов и держит связанные данные вместе. Также упрощается управление версиями и гарантируется, что вся необходимая документация перемещается вместе с книгой, улучшая совместную работу команд.

## Предварительные требования

- **GroupDocs.Merger for .NET** (последний пакет NuGet)  
- **.NET Framework** 4.5+ **или** **.NET Core/5+/6+**  
- Visual Studio 2022 или новее  
- Базовые знания C# и знакомство с вводом‑выводом файлов  

## Настройка GroupDocs.Merger for .NET

### Установка

Add the package using one of the following methods:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Найдите “GroupDocs.Merger” и установите последнюю версию.

### Получение лицензии

1. **Бесплатная пробная версия** — тестировать библиотеку бесплатно.  
2. **Временная лицензия** — запросите временную лицензию на странице [temporary‑license page](https://purchase.groupdocs.com/temporary-license/).  
3. **Покупка** — рассмотрите покупку лицензии на странице [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

### Базовая инициализация

`Merger` — точка входа для всех операций.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Как встраивать OLE‑объекты в Excel?

Load your source workbook, configure the OLE options, and let `Merger` insert the object. The following sections give you a concise, ready‑to‑run workflow.

### Обзор функции
Embedding OLE objects lets you store a complete PDF inside a cell, preserving the original layout and enabling one‑click access from Excel.

### Пошаговая реализация

#### 1. Установите пути и номер страницы
Укажите таблицу, файл для встраивания и адрес целевой ячейки.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Настройте OleSpreadsheetOptions
`OleSpreadsheetOptions` определяет, где OLE‑объект будет размещён в листе и как будет выглядеть его иконка.

```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Инициализируйте Merger и выполните встраивание
Класс `Merger` осуществляет фактическую вставку. После вызова книга содержит иконку OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Общие советы по устранению неполадок
- Убедитесь, что все пути к файлам являются абсолютными или правильно разрешаются относительно исполняемого файла.  
- Убедитесь, что указанный номер страницы существует в исходном PDF; иначе будет выброшено исключение.  
- Если встроенный объект не отображается, проверьте, поддерживает ли целевая версия Excel OLE (большинство современных версий поддерживают).

## Практические применения

Встраивание PDF в Excel полезно для:

1. **Финансовые отчёты** — прикрепляйте аудированные отчёты непосредственно рядом с таблицами‑резюмэ.  
2. **Документация проекта** — храните спецификации дизайна, анализ рисков или контракты в главном трекере.  
3. **Обучающие панели** — встраивайте руководства пользователя или политики в виде PDF для быстрого доступа сотрудникам.

## Соображения по производительности

- **Размер файла** — держите встроенные PDF размером менее 5 МБ, чтобы не раздувать книгу.  
- **Использование памяти** — `GroupDocs.Merger` передаёт данные потоково, поэтому потребление памяти остаётся низким даже при больших исходных файлах.  
- **Освобождение объектов** — всегда вызывайте `Dispose()` у экземпляров `Merger`, чтобы быстро освобождать файловые дескрипторы.

## Часто задаваемые вопросы

**В: Что такое OLE‑объект?**  
OLE (Object Linking and Embedding) объект хранит другой файл (PDF, Word, изображение и т.д.) внутри хост‑документа, позволяя редактировать или открывать его на месте.

**В: Можно ли встраивать OLE‑объекты в другие форматы Office?**  
Да — GroupDocs.Merger также поддерживает файлы Word, PowerPoint и Visio.

**В: Как работать с PDF, защищёнными паролем?**  
Укажите пароль при создании экземпляра `OleSpreadsheetOptions`; библиотека автоматически расшифрует файл.

**В: Есть ли ограничение размера для встроенных PDF?**  
Технически жёсткого ограничения нет, но файлы более 10 МБ могут заметно увеличить время загрузки книги.

**В: Где можно найти больше примеров?**  
Посетите официальную [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) для дополнительных примеров кода и справки по API.

## Дополнительные ресурсы
- **Документация**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **Ссылка на API**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Загрузки**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Покупка лицензии**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Бесплатная пробная версия**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Временная лицензия**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Форум поддержки**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Последнее обновление:** 2026-09-21  
**Тестировано с:** GroupDocs.Merger 23.12 for .NET  
**Автор:** GroupDocs

## Связанные учебники

- [Встраивание PDF как OLE в PowerPoint с помощью GroupDocs.Merger for .NET: пошаговое руководство](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Встраивание PDF в Word с помощью GroupDocs.Merger for .NET: пошаговое руководство](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Загрузка PDF по URL в .NET с помощью GroupDocs.Merger: подробное руководство](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}