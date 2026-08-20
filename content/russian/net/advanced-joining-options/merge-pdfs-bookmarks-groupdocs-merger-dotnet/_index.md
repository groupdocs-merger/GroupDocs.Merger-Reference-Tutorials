---
date: '2026-08-20'
description: Узнайте, как объединять PDF‑файлы с закладками с помощью GroupDocs.Merger
  for .NET, включая настройку, примеры кода и лучшие практики объединения PDF‑документов.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Узнайте, как объединять PDF‑файлы с закладками с помощью GroupDocs.Merger
  for .NET. Следуйте пошаговому коду для объединения PDF‑документов с сохранением
  навигации.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Как объединять PDF‑файлы с закладками с помощью GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Как объединять PDF‑файлы с закладками с помощью GroupDocs.Merger for .NET
type: docs
url: /ru/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Как объединить PDF с закладками с помощью GroupDocs.Merger для .NET

Объединение нескольких PDF‑файлов с сохранением их оригинальных закладок может сэкономить часы ручной реорганизации. В этом руководстве вы узнаете, как **объединять PDF с закладками** с помощью GroupDocs.Merger для .NET, от настройки проекта до полного, готового к использованию в продакшене примера кода.

## Быстрые ответы
- **Какая библиотека поддерживает объединение с сохранением закладок?** GroupDocs.Merger for .NET.  
- **Можно ли объединять более двух PDF одновременно?** Да — добавляйте столько исходных файлов, сколько нужно.  
- **Нужна ли лицензия для разработки?** Бесплатная пробная версия подходит для тестирования; для продакшена требуется постоянная лицензия.  
- **Поддерживается ли .NET Core?** Абсолютно — библиотека работает с .NET Core, .NET 5/6 и полной платформой .NET Framework.  
- **Какой максимальный размер файла она может обработать?** До 2 ГБ на документ, обрабатывается без загрузки всего файла в память.

## Что такое объединение PDF с закладками?
**Объединение PDF с закладками** означает взятие нескольких PDF‑документов и их комбинирование в один файл при сохранении иерархии закладок каждого исходного документа. Полученный PDF сохраняет оригинальную структуру навигации, позволяя читателям переходить непосредственно к разделам, пришедшим из каждого отдельного файла, что важно для больших отчётов или собранных руководств.

## Зачем объединять PDF с закладками?
Сохранение закладок при объединении PDF улучшает навигацию в объединённых документах, позволяя пользователям быстро находить конкретные главы или разделы без прокрутки всего файла. GroupDocs.Merger сохраняет оригинальную иерархию оглавления, уменьшает усилия по ручной реорганизации и поддерживает большие файлы до 2 ГБ при минимальном потреблении памяти, что делает её идеальной для корпоративных процессов.

## Предварительные требования
- **.NET Core SDK** (3.1 или новее) или **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** или любая IDE, поддерживающая разработку на .NET.  
- Базовые знания C# и знакомство с вводом‑выводом файлов.  

## Настройка GroupDocs.Merger для .NET

### Установка
Добавьте библиотеку в ваш проект с помощью одной из следующих команд:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

- Найдите “GroupDocs.Merger” и установите последнюю версию.

### Получение лицензии
- **Бесплатная пробная версия:** Скачайте со страницы [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Временная лицензия:** Получите её на странице [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Полная лицензия:** Приобретите на странице [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Базовая инициализация
Класс `Merger` является точкой входа для всех операций объединения.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Это пространство имён предоставляет доступ ко всему набору функций манипуляции PDF.

## Как объединить PDF с закладками в .NET

Загрузите основной PDF, настройте обработку закладок, добавьте дополнительные файлы и сохраните результат — всё это в нескольких лаконичных строках кода.

**Прямой ответ (40‑70 слов):**  
Создайте экземпляр `Merger` с первым PDF, включите `PdfJoinOptions.UseBookmarks`, добавьте каждый последующий PDF через `Join` и вызовите `Save` для записи объединённого файла. Этот подход сохраняет каждую оригинальную иерархию закладок и выполняется за один проход, минимизируя потребление памяти.

### Шаг 1: определить пути к каталогам
Настройте папки исходных и выходных файлов, чтобы код мог находить PDF, которые вы хотите объединить.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Шаг 2: загрузить основной PDF
`Merger` представляет основной документ, к которому будут добавляться остальные.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Шаг 3: настроить параметры сохранения закладок
`PdfJoinOptions` управляет поведением объединения; флаг `UseBookmarks` указывает движку сохранять существующие закладки.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Шаг 4: добавить дополнительные PDF
Вызовите `Join` для каждого дополнительного файла. Библиотека автоматически объединяет их деревья закладок под оглавлением основного документа.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Шаг 5: сохранить объединённый PDF
Укажите путь вывода и формат; библиотека записывает один PDF, сохраняющий все записи закладок.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Распространённые проблемы и решения
- **Отсутствуют закладки:** Убедитесь, что `UseBookmarks = true` в `PdfJoinOptions`.  
- **Ошибки путей:** Используйте `Path.Combine` и проверьте существование файлов перед объединением.  
- **Большие файлы вызывают всплески памяти:** Обрабатывайте PDF последовательно и освобождайте объект `Merger` после каждого сохранения.

## Практические применения
1. **Консолидация финансовых отчётов** — сохраняйте квартальные разделы мгновенно доступными через закладки.  
2. **Пакеты учебных материалов** — объединяйте лекционные PDF, сохраняя навигацию по главам для студентов.  
3. **Наборы проектной документации** — объединяйте спецификации дизайна, планы тестирования и примечания к релизам в один, удобный для поиска файл.

## Соображения по производительности
- Обрабатывайте по одному файлу при объединении более 20 PDF, чтобы снизить использование ОЗУ.  
- Используйте последнюю runtime .NET (например, .NET 6) для оптимальной JIT‑компиляции и эффективности сборки мусора.  
- Для PDF размером более 500 МБ включите режим потоковой передачи через `MergerSettings`, чтобы избежать загрузки всего документа в память.

## Часто задаваемые вопросы

**Q: Что такое GroupDocs.Merger?**  
A: GroupDocs.Merger — это .NET‑библиотека, позволяющая программно объединять, разделять, вращать и иначе манипулировать PDF и другими форматами документов.

**Q: Можно ли объединять более двух PDF‑файлов одновременно?**  
A: Да — вызывайте `Join` многократно или передайте коллекцию путей к файлам, чтобы объединить любое количество PDF за одну операцию.

**Q: Как управлять лицензированием для продакшн‑использования?**  
A: Получите постоянную лицензию на странице покупки GroupDocs; пробная лицензия подходит только для оценки и истекает через 30 дней.

**Q: В моём объединённом PDF нет закладок — в чём проблема?**  
A: Убедитесь, что `PdfJoinOptions.UseBookmarks` установлен в `true` и каждый исходный PDF действительно содержит закладки перед объединением.

**Q: Совместима ли библиотека с .NET Core и .NET Framework?**  
A: Абсолютно — она поддерживает .NET Core 3.1+, .NET 5/6 и полную .NET Framework 4.6.1+.

## Ресурсы
- [Документация](https://docs.groupdocs.com/merger/net/)  
- [Справочник API](https://reference.groupdocs.com/merger/net/)  
- [Скачать GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Приобрести лицензию](https://purchase.groupdocs.com/buy)  
- [Бесплатная пробная версия](https://releases.groupdocs.com/merger/net/)  
- [Временная лицензия](https://purchase.groupdocs.com/temporary-license/)  
- [Форум поддержки](https://forum.groupdocs.com/c/merger/)  

---

**Последнее обновление:** 2026-08-20  
**Тестировано с:** GroupDocs.Merger 23.11 for .NET  
**Автор:** GroupDocs

## Связанные руководства

- [Как объединить отдельные страницы PDF с помощью GroupDocs.Merger для .NET: Полное руководство](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Как легко объединять документы с помощью GroupDocs.Merger для .NET: Полное руководство](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Как добавить вложения в PDF с помощью GroupDocs.Merger для .NET: Пошаговое руководство](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)