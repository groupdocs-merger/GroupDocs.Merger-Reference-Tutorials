---
date: '2026-09-26'
description: Узнайте, как извлекать конкретные страницы PDF с помощью GroupDocs.Merger
  для .NET, включая извлечение страниц из Word и эффективную работу с большими документами.
keywords:
- extract specific pages pdf
- extract pages from word
- extract pages from large document
lastmod: '2026-09-26'
og_description: Узнайте, как извлекать конкретные страницы PDF с помощью GroupDocs.Merger
  для .NET. Это руководство демонстрирует пошаговую настройку, конфигурацию без кода
  и рекомендации по производительности для Word, PDF и больших документов.
og_image_alt: Guide showing how to extract specific pages pdf using GroupDocs.Merger
  for .NET
og_title: Извлечение конкретных страниц PDF с помощью GroupDocs.Merger для .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  headline: Extract specific pages pdf with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  name: Extract specific pages pdf with GroupDocs.Merger for .NET
  steps:
  - name: install the NuGet package
    text: 'Open a terminal in your project folder and run one of the following commands:
      **.NET CLI** **Package Manager Console** **NuGet Package Manager UI** – use
      the UI to search for “GroupDocs.Merger” and click **Install**.'
  - name: define file paths
    text: Specify absolute or relative paths for the input and the output document
      you want to create. **Definition anchor** `ExtractOptions` is the configuration
      object that tells the library which pages to pull out and how to treat them.
  - name: set extraction options
    text: Create an `ExtractOptions` instance, set `StartPageNumber`, `EndPageNumber`,
      and choose `RangeMode` (e.g., `Even`). This tells the engine to pick every second
      page within the range. **Definition anchor** `Merger` is the core class that
      orchestrates all document‑manipulation operations, including ext
  - name: extract and save
    text: Invoke the `Extract` method on the `Merger` instance, passing the options
      and the output path. The library writes the new file without loading the whole
      source into memory, which is ideal for large documents.
  type: HowTo
- questions:
  - answer: GroupDocs.Merger supports more than 30 formats, including PDF, DOCX, XLSX,
      PPTX, HTML, and image types like PNG and JPEG.
    question: What file formats can I extract pages from?
  - answer: Yes, you can pass a list of individual page numbers or multiple ranges
      to `ExtractOptions`.
    question: Can I extract non‑contiguous pages (e.g., 1, 3, 5)?
  - answer: Provide the password through `LoadOptions` when constructing the `Merger`
      instance; the extraction will then proceed normally.
    question: How do I work with password‑protected PDFs?
  - answer: No hard limit; the only practical constraint is the available memory,
      which remains low thanks to streaming.
    question: Is there a limit on the number of pages I can extract in one call?
  - answer: No external applications are needed; all processing happens inside the
      .NET runtime.
    question: Does the library require Microsoft Office or Adobe Acrobat to be installed?
  type: FAQPage
tags:
- extract specific pages pdf
- GroupDocs.Merger
- .NET document processing
title: Извлечение конкретных страниц PDF с помощью GroupDocs.Merger для .NET
type: docs
url: /ru/net/document-extraction/extract-pages-groupdocs-merger-net/
weight: 1
---

# Извлечение конкретных страниц PDF с помощью GroupDocs.Merger для .NET

Извлечение конкретных страниц PDF из многостраничного документа — распространённая задача, когда нужно поделиться только нужными разделами, уменьшить размер файла или автоматизировать процессы рецензирования. В этом руководстве вы узнаете, как GroupDocs.Merger для .NET позволяет вытаскивать точные страницы — будь то PDF, файл Word или любой из более чем 30 поддерживаемых форматов — используя простой программный подход.

## Быстрые ответы
- **Может ли GroupDocs.Merger извлекать страницы из документов Word?** Да, он работает с DOCX, DOC и другими форматами Office.  
- **Есть ли ограничение по размеру файла?** Библиотека может обрабатывать файлы до 2 ГБ без загрузки всего документа в память.  
- **Нужна ли лицензия для разработки?** Доступна бесплатная пробная версия; лицензия требуется для использования в продакшене.  
- **Будет ли работать на .NET 6?** Абсолютно — GroupDocs.Merger поддерживает .NET Framework 4.5+, .NET Core 3.1+, и .NET 5/6+.  
- **Сколько страниц можно извлечь за один раз?** Можно указать отдельные страницы, диапазоны или выбор чётных/нечётных страниц в одном вызове.

## Что такое GroupDocs.Merger для .NET?
GroupDocs.Merger для .NET — это серверная библиотека, позволяющая объединять, разделять, вращать и извлекать страницы из более чем 30 форматов документов без необходимости установки Microsoft Office или Adobe Acrobat. Она обрабатывает файлы потоково, что сохраняет низкое потребление памяти даже для PDF‑файлов со сотнями страниц.

## Зачем извлекать конкретные страницы PDF?
Извлечение конкретных страниц PDF уменьшает пропускную способность, ускоряет совместную работу и гарантирует, что конфиденциальные разделы останутся скрытыми. Оцененный эффект: организации сообщают о до 40 % ускорении циклов обзора документов, когда делятся только нужными страницами вместо целых файлов. Кроме того, меньшие файлы ускоряют загрузку в веб‑просмотрщиках и снижают затраты на хранение.

## Необходимые условия
- Visual Studio 2022 или любой совместимый с .NET IDE.  
- .NET 6 SDK (или .NET Framework 4.7.2+).  
- Доступ к NuGet‑ленте для установки **GroupDocs.Merger**.  
- Базовые знания C# и права доступа к файловой системе.

## Как извлечь конкретные страницы PDF пошагово

Загрузите исходный файл, укажите нужные страницы и сохраните результат — всё это занимает несколько строк кода.

### Прямой ответ
`Merger` — основной класс, который оркестрирует операции манипуляции документами. `ExtractOptions` задаёт, какие страницы извлекать и как их обрабатывать. `Extract` выполняет извлечение согласно указанным параметрам и записывает результат в новый файл. Чтобы извлечь конкретные страницы PDF, создайте экземпляр `Merger` с исходным файлом, сконфигурируйте объект `ExtractOptions`, определяющий диапазон страниц и режим (чётные, нечётные или пользовательский), затем вызовите `Extract` и сохраните выходной файл. Весь процесс занимает менее секунды для типичных 100‑страничных PDF на стандартном сервере.

### Шаг 1: установить пакет NuGet
Откройте терминал в папке проекта и выполните одну из следующих команд:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager Console**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – используйте интерфейс для поиска “GroupDocs.Merger” и нажмите **Install**.

### Шаг 2: определить пути к файлам
Укажите абсолютные или относительные пути к входному и выходному документу, который вы хотите создать.

**Definition anchor**  
`ExtractOptions` — объект конфигурации, который сообщает библиотеке, какие страницы вытаскивать и как с ними обращаться.  
```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY\\Sample.docx"; // Input document path
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "ExtractedPages.docx"); // Output document path
```  

### Шаг 3: установить параметры извлечения
Создайте экземпляр `ExtractOptions`, задайте `StartPageNumber`, `EndPageNumber` и выберите `RangeMode` (например, `Even`). Это указывает движку выбирать каждую вторую страницу в указанном диапазоне.

**Definition anchor**  
`Merger` — основной класс, который оркестрирует все операции манипуляции документами, включая извлечение, объединение и вращение страниц.  
```csharp
ExtractOptions extractOptions = new ExtractOptions(1, 3, RangeMode.EvenPages);
```  

### Шаг 4: извлечь и сохранить
Вызовите метод `Extract` у экземпляра `Merger`, передав параметры и путь к выходному файлу. Библиотека записывает новый файл без загрузки всего источника в память, что идеально подходит для больших документов.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ExtractPages(extractOptions);
    merger.Save(filePathOut); // Save the result to a specified path
}
```  

## Распространённые проблемы и решения
- **Страницы не извлечены** – проверьте, что `StartPageNumber` и `EndPageNumber` указаны с 1‑го и что исходный файл действительно содержит запрошенный диапазон.  
- **Ошибки «Out‑of‑memory» при работе с огромными файлами** – убедитесь, что используете потоковый API (по умолчанию) и что процесс имеет достаточно виртуальной памяти; рассмотрите возможность увеличения настройки `maxMemory` в конфигурации библиотеки.  
- **Файлы, защищённые паролем** – `LoadOptions` позволяет задать параметры, такие как пароли, при загрузке защищённого документа. Передайте пароль через `LoadOptions` перед созданием экземпляра `Merger`.

## Практические применения
1. **Обзор документов** – вытаскивайте только те пункты, которые нужны рецензенту, оставляя остальное конфиденциальным.  
2. **Образование** – создавайте индивидуальные раздаточные материалы, извлекая слайды лекций или главы учебников.  
3. **Юридические процессы** – изолируйте страницы‑экспонаты для судебных подач без раскрытия полного дела.

## Соображения по производительности
GroupDocs.Merger обрабатывает документы потоково, позволяя работать с файлами до **2 GB**, удерживая пиковое потребление памяти ниже **150 MB**. Для лучшего результата оборачивайте объект `Merger` в оператор `using`, чтобы гарантировать его освобождение, и переиспользуйте один экземпляр при извлечении нескольких диапазонов из одного источника.

## Заключение
Теперь у вас есть полностью готовый к продакшену метод извлечения конкретных страниц PDF с помощью GroupDocs.Merger для .NET. Настроив `ExtractOptions` и используя потоковый движок библиотеки, вы можете автоматизировать нарезку документов любого поддерживаемого формата, ускорить совместную работу и держать конфиденциальную информацию под контролем.

**Следующие шаги** – изучите другие возможности библиотеки, такие как объединение документов, вращение страниц и наложение водяных знаков, чтобы создать полностью автоматизированные конвейеры обработки документов.

## Часто задаваемые вопросы

**Q: Какие форматы файлов поддерживают извлечение страниц?**  
A: GroupDocs.Merger поддерживает более 30 форматов, включая PDF, DOCX, XLSX, PPTX, HTML и типы изображений, такие как PNG и JPEG.

**Q: Можно ли извлекать не подряд идущие страницы (например, 1, 3, 5)?**  
A: Да, вы можете передать список отдельных номеров страниц или несколько диапазонов в `ExtractOptions`.

**Q: Как работать с PDF‑файлами, защищёнными паролем?**  
A: Укажите пароль через `LoadOptions` при создании экземпляра `Merger`; после этого извлечение будет выполнено обычным образом.

**Q: Есть ли ограничение на количество страниц, которые можно извлечь за один вызов?**  
A: Жёсткого ограничения нет; единственное практическое ограничение — доступная память, которая остаётся низкой благодаря потоковой обработке.

**Q: Требуется ли для работы библиотеки установка Microsoft Office или Adobe Acrobat?**  
A: Нет, внешние приложения не нужны; вся обработка происходит внутри среды выполнения .NET.

## Ресурсы
- [Документация](https://docs.groupdocs.com/merger/net/)
- [Справочник API](https://reference.groupdocs.com/merger/net/)
- [Скачать GroupDocs.Merger для .NET](https://releases.groupdocs.com/merger/net/)
- [Купить лицензию](https://purchase.groupdocs.com/buy)
- [Бесплатная пробная версия](httpshttps://releases.groupdocs.com/merger/net/)
- [Запрос временной лицензии](https://purchase.groupdocs.com/temporary-license/)
- [Форум поддержки](https://forum.groupdocs.com/c/merger/)

---

**Последнее обновление:** 2026-09-26  
**Тестировано с:** GroupDocs.Merger 23.11 for .NET  
**Автор:** GroupDocs

## Связанные руководства

- [Как объединить конкретные страницы PDF с помощью GroupDocs.Merger для .NET: Полное руководство](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Как удалить страницы из документов с помощью GroupDocs.Merger для .NET: Пошаговое руководство](/merger/net/page-operations/groupdocs-merger-remove-pages-net-tutorial/)
- [Как переместить страницы внутри документа с помощью GroupDocs.Merger для .NET: Полное руководство](/merger/net/page-operations/move-pages-groupdocs-merger-dotnet/)