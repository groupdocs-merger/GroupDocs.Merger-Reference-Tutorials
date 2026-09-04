---
date: 2026-08-31
description: Узнайте, как извлекать определённые страницы pdf с помощью GroupDocs.Merger
  для .NET. Пошаговые руководства охватывают сценарии извлечения из Word, PDF и DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Узнайте, как извлекать определённые страницы pdf с помощью GroupDocs.Merger
  для .NET. Подробные руководства помогут эффективно извлекать страницы из файлов
  PDF, Word и DOCX.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Как извлечь определённые страницы pdf с помощью GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Как извлечь определённые страницы pdf с помощью GroupDocs.Merger
type: docs
url: /ru/net/document-extraction/
weight: 9
---

# Как извлечь отдельные страницы PDF с помощью GroupDocs.Merger

Извлечение отдельных страниц PDF является распространённой задачей, когда необходимо повторно использовать, поделиться или архивировать только часть большого документа. С помощью GroupDocs.Merger для .NET вы можете программно извлекать отдельные страницы, диапазоны страниц или произвольные выборки из файлов PDF, Word и DOCX без ручного редактирования. Этот учебник проведёт вас через концепции, предварительные требования и пошаговый процесс, чтобы вы могли интегрировать извлечение страниц в любое .NET‑приложение.

## Быстрые ответы
- **Что означает «извлечение отдельных страниц PDF»?** Это означает выбор отдельных страниц или диапазонов из PDF (или другого поддерживаемого формата) и сохранение их в виде нового, более небольшого документа.  
- **Какие форматы поддерживаются?** GroupDocs.Merger поддерживает более 50 форматов ввода и вывода, включая PDF, DOCX, PPTX и изображения.  
- **Нужна ли лицензия?** Временная лицензия подходит для тестирования; полная лицензия требуется для использования в продакшене.  
- **Можно ли обрабатывать большие файлы?** Да — библиотека обрабатывает файлы со сотнями страниц, используя потоковую передачу, что сохраняет низкое потребление памяти.  
- **Поддерживается ли .NET Core?** Абсолютно — API работает с .NET Framework 4.6+, .NET Core 3.1+ и .NET 6/7.

## Что такое извлечение отдельных страниц PDF?
`extract specific pages pdf` относится к операции взятия одной или нескольких страниц из существующего PDF (или поддерживаемого документа) и создания нового PDF, содержащего только эти страницы. Это позволяет делиться только нужными разделами, сохраняя оригинальный файл неизменным.

## Почему извлекать отдельные страницы PDF с помощью GroupDocs.Merger?
GroupDocs.Merger обрабатывает более **50 форматов файлов** и может извлекать страницы из документов, содержащих **более 500 страниц**, менее чем за **2 секунды** на типичном серверном процессоре. API работает без необходимости установки Microsoft Office или Adobe Acrobat, что уменьшает сложность развертывания и затраты на лицензирование.

## Предварительные требования
- .NET 6 SDK (или .NET Core 3.1 / .NET Framework 4.6+) установлен на вашей машине разработки.  
- Действительный NuGet‑пакет GroupDocs.Merger for .NET (`GroupDocs.Merger`) добавлен в ваш проект.  
- (Опционально) Временный или полный файл лицензии, если вы планируете запускать код после периода оценки.

## Как извлечь отдельные страницы PDF в C# с помощью GroupDocs.Merger

Загрузите исходный документ, укажите нужные страницы и сохраните результат. Библиотека абстрагирует все детали, зависящие от формата, поэтому один и тот же код работает с PDF, DOCX, PPTX и другими типами.

### Шаг 1: создать экземпляр Merger
Класс `Merger` является точкой входа для загрузки и манипулирования документами. Создайте экземпляр `Merger`, передав путь к исходному файлу. Этот объект представляет документ, с которым вы будете работать.

### Шаг 2: указать страницы для извлечения
Укажите список индексов страниц (нумерация с 1) или строку диапазона, например `"1-3,5"`, чтобы сообщить библиотеке, какие страницы сохранить.

### Шаг 3: сохранить извлечённый документ
Вызовите `Save` у объекта `Document`, указав путь вывода и желаемый формат (например, `SaveFormat.Pdf`). `SaveFormat` — это перечисление, определяющее тип выходного файла, например PDF. Операция записывает новый файл, содержащий только выбранные страницы.

## Распространённые проблемы и решения
- **Страницы смещены на один:** GroupDocs.Merger использует нумерацию страниц, начинающуюся с 1. Убедитесь, что ваш список начинается с 1, а не с 0.  
- **Файлы, защищённые паролем:** Передайте пароль в конструктор `Merger` или используйте объект `LoadOptions`. `LoadOptions` предоставляет настройки, контролирующие процесс загрузки документа, например включение кэширования в памяти.  
- **Большие файлы вызывают тайм‑ауты:** Включите потоковую передачу, установив `LoadOptions.UseMemoryCache = true`, чтобы снизить потребление памяти.

## Часто задаваемые вопросы

**В: Можно ли извлечь страницы из документа Word в виде PDF?**  
О: Да — тот же вызов `Extract` работает с DOCX, и вы можете сразу сохранить результат как PDF, используя `SaveFormat.Pdf`.

**В: Можно ли извлечь несмежные страницы?**  
О: Абсолютно. Укажите список через запятую, например `"2,4,7"`, или смешанный диапазон `"1-2,5,8-10"`.

**В: Поддерживает ли библиотека зашифрованные PDF?**  
О: Да. Передайте пароль при открытии документа; API автоматически его расшифрует.

**В: Как GroupDocs.Merger обрабатывает изображения внутри PDF?**  
О: Изображения сохраняются точно в том виде, в каком они находятся на выбранных страницах; дополнительные шаги конвертации не требуются.

**В: Какие версии .NET официально поддерживаются?**  
О: .NET Framework 4.6+, .NET Core 3.1+ и .NET 5/6/7 полностью поддерживаются.

## Доступные учебные материалы

### [Извлечение отдельных страниц из документов с помощью GroupDocs.Merger для .NET](./extract-pages-groupdocs-merger-net/)
Learn how to efficiently extract specific pages using GroupDocs.Merger for .NET. Ideal for managing Word, PDF, and more in professional environments.

### [Как извлечь отдельные страницы из документа с помощью GroupDocs.Merger для .NET на C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Learn how to extract specific pages from documents using GroupDocs.Merger for .NET with this comprehensive guide. Streamline your document management tasks effortlessly.

## Дополнительные ресурсы

- [GroupDocs.Merger для .net Документация](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger для .net Справочник API](https://reference.groupdocs.com/merger/net/)
- [Скачать GroupDocs.Merger для .net](https://releases.groupdocs.com/merger/net/)
- [Форум GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Бесплатная поддержка](https://forum.groupdocs.com/)
- [Временная лицензия](https://purchase.groupdocs.com/temporary-license/)

---

**Последнее обновление:** 2026-08-31  
**Тестировано с:** GroupDocs.Merger 23.9 for .NET  
**Автор:** GroupDocs

## Связанные учебные материалы

- [Как объединять отдельные страницы PDF с помощью GroupDocs.Merger для .NET: Полное руководство](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Как объединять отдельные страницы из нескольких документов с помощью GroupDocs.Merger для .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Поворот страниц PDF в .NET с помощью GroupDocs.Merger: Пошаговое руководство](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)