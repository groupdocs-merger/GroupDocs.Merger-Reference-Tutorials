---
date: '2026-07-06'
description: Узнайте, как получить поддерживаемые типы файлов с помощью GroupDocs.Merger
  для Java, проверьте поддерживаемые расширения Java и интегрируйте список в ваш рабочий
  процесс.
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: Поддерживаемые форматы GroupDocs.Merger – Получение типов в Java
type: docs
url: /ru/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# Поддерживаемые форматы GroupDocs.Merger – Получение типов в Java

Работа с широким спектром форматов документов в Java может быстро превратиться в головную боль, если вы не знаете, какие из них действительно поддерживает ваша библиотека. **GroupDocs.Merger поддерживаемые форматы** предоставляют надёжную справочную точку, позволяя проверять загрузки, избегать ошибок во время выполнения и проектировать более умные конвейеры управления документами. В этом руководстве вы точно увидите, как получить список поддерживаемых типов файлов с помощью GroupDocs.Merger для Java, почему это важно и как интегрировать эту информацию в реальные приложения.

### Быстрые ответы
- **Что делает “retrieve supported file types”?**  
  Возвращает список всех форматов документов, которые GroupDocs.Merger может обрабатывать.
- **Какой метод предоставляет список?**  
  `FileType.getSupportedFileTypes()` из пакета `com.groupdocs.merger.domain`.
- **Нужна ли лицензия для вызова этого метода?**  
  Для использования в продакшене требуется пробная или полная лицензия; метод работает в режиме оценки.
- **Могу ли я отфильтровать список, оставив только нужные расширения?**  
  Да – пройдите по возвращённому списку и оставьте только интересующие вас расширения.
- **Является ли эта операция ресурсоёмкой?**  
  Нет, она просто читает статическую коллекцию, поэтому выполняется мгновенно.

## Какие форматы поддерживает GroupDocs.Merger?

GroupDocs.Merger поддерживает **70+** входных и выходных форматов — включая PDF, DOCX, PPTX, XLSX, HTML и распространённые типы изображений — позволяя работать практически с любым бизнес‑документом. Таблица форматов библиотеки хранится внутри как статическая коллекция, поэтому её получение — операция O(1), завершающаяся за несколько миллисекунд даже на скромном оборудовании.

## Как проверить поддерживаемые расширения в Java?

Вызовите статический метод `FileType.getSupportedFileTypes()`, затем пройдите по возвращённой коллекции, чтобы прочитать каждое расширение. Этот однострочный вызов даёт готовый к использованию `List<FileType>`, который можно фильтровать, отображать или сохранять для последующей проверки.

## Почему следует получать поддерживаемые типы файлов перед обработкой?

Точное знание списка форматов предотвращает избежные исключения, уменьшает необходимость в избыточном коде защиты и позволяет показывать пользователям чёткое сообщение «разрешённые типы файлов». Это также даёт возможность создавать динамические UI‑компоненты — такие как фильтры в диалогах выбора файлов — которые отображают только совместимые расширения, улучшая общий пользовательский опыт.

## Предварительные требования

Перед началом убедитесь, что у вас есть:
- **Java Development Kit (JDK):** Рекомендуется версия 8 или выше.  
- **Integrated Development Environment (IDE):** Любая IDE, такая как IntelliJ IDEA или Eclipse, подойдет.  
- **GroupDocs.Merger Library:** Включите эту библиотеку в зависимости вашего проекта.  

Знание базовых концепций программирования на Java и опыт работы с библиотеками в среде Maven или Gradle также полезны. Если вы новичок в этих инструментах, рекомендуется сначала ознакомиться с их документацией.

## Настройка GroupDocs.Merger для Java

Чтобы использовать GroupDocs.Merger для Java, настройте библиотеку в проекте с помощью Maven, Gradle или загрузив её напрямую с официального сайта.

### Установка через Maven

Добавьте следующую зависимость в ваш файл `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Установка через Gradle

Включите эту строку в ваш файл `build.gradle`:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Прямое скачивание

Кроме того, скачайте последнюю версию по ссылке [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Шаги получения лицензии
1. **Free Trial:** Начните с бесплатного пробного периода, чтобы изучить возможности библиотеки.  
2. **Temporary License:** Получите временную лицензию, если нужен расширенный доступ без ограничений.  
3. **Purchase:** Рассмотрите возможность покупки полной лицензии для длительного использования.

## Базовая инициализация и настройка

Чтобы инициализировать GroupDocs.Merger в вашем Java‑приложении, импортируйте необходимые классы:

```java
import com.groupdocs.merger.domain.FileType;
```

Теперь перейдём к реализации функции, которая получает поддерживаемые типы файлов.

## Что такое класс FileType?

Класс `FileType` — это основная модель в GroupDocs.Merger, представляющая один формат документа, раскрывающая его расширение, MIME‑тип и удобочитаемое имя. Вы взаимодействуете с этим классом, вызывая `FileType.getSupportedFileTypes()`, чтобы получить полный каталог форматов.

## Как получить поддерживаемые типы файлов?

Чтобы получить поддерживаемые форматы, просто вызовите статический метод `FileType.getSupportedFileTypes()`, предоставляемый библиотекой GroupDocs.Merger. Этот вызов возвращает `List<FileType>`, содержащий каждый формат, с которым может работать библиотека. Операция лёгкая и может быть выполнена при запуске приложения или в любой момент, когда необходимо проверить загрузки файлов.

### Шаг 1: Получить поддерживаемые типы файлов

Сначала получите список поддерживаемых типов файлов из класса `FileType`:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

Этот метод возвращает список, содержащий все типы файлов, поддерживаемые GroupDocs.Merger.

### Шаг 2: Отобразить поддерживаемые расширения

Затем пройдите по каждому объекту `FileType` и выведите его расширение. Это часть, где мы **отображаем поддерживаемые расширения** для разработчиков или конечных пользователей:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

Цикл проходит по каждому поддерживаемому типу файла и выводит его расширение в консоль.

### Шаг 3: Сообщение подтверждения

Наконец, выведите сообщение подтверждения, указывающее на успешное получение списка:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Практические применения

Понимание поддерживаемых типов файлов необходимо для различных сценариев:
1. **Document Management Systems:** Автоматически классифицировать документы по типу.  
2. **File Conversion Tools:** Обеспечить совместимость перед конвертацией файлов между форматами.  
3. **Merging Applications:** Проверять входные файлы перед объединением, чтобы избежать ошибок.  

Интеграция с другими системами — такими как облачное хранилище или сервисы обработки документов — может дополнительно расширить функциональность.

## Соображения по производительности

При работе с GroupDocs.Merger в Java учитывайте следующие рекомендации:
- **Optimize Memory Usage:** Освобождайте объекты, когда они больше не нужны.  
- **Batch Processing:** Обрабатывайте файлы пакетами, чтобы снизить потребление ресурсов.  
- **Asynchronous Operations:** Используйте асинхронные методы для неблокирующих операций.  

## Распространённые проблемы и решения

- **Dependency Issues:** Убедитесь, что зависимости Maven или Gradle правильно объявлены; несоответствие версий вызывает ошибки class‑not‑found.  
- **Library Version:** Всегда используйте последнюю версию GroupDocs.Merger, чтобы получать новые форматы и исправления ошибок.  
- **License Errors:** Если появляются исключения лицензирования, проверьте, что файл пробной или постоянной лицензии правильно указан в коде.

## Часто задаваемые вопросы

**Q: Что такое GroupDocs.Merger для Java?**  
**A:** Это Java‑библиотека, позволяющая объединять, разделять и конвертировать широкий спектр форматов документов без необходимости установки Microsoft Office.

**Q: Как начать работу с GroupDocs.Merger?**  
**A:** Добавьте зависимость Maven или Gradle, получите пробную или полную лицензию и инициализируйте библиотеку, как показано в разделе настройки.

**Q: Можно ли использовать GroupDocs.Merger бесплатно?**  
**A:** Да, доступен бесплатный пробный период для оценки; полная лицензия требуется для продакшн‑развёртываний.

**Q: Какие типы файлов поддерживает GroupDocs.Merger?**  
**A:** Используйте метод `FileType.getSupportedFileTypes()`, чтобы получить список **70+** поддерживаемых форматов, включая PDF, DOCX, PPTX, XLSX, HTML и типы изображений.

**Q: Как обрабатывать неподдерживаемые типы файлов?**  
**A:** Проверяйте загрузки против поддерживаемого списка перед обработкой; отклоняйте или конвертируйте неподдерживаемые файлы заранее, чтобы избежать ошибок во время выполнения.

**Q: Можно ли отфильтровать список, показывая только нужные расширения?**  
**A:** Да. После вызова `getSupportedFileTypes()` пройдите по списку и оставьте только интересующие вас расширения.

**Q: Требуется ли лицензия для сборок разработки?**  
**A:** Пробная лицензия подходит для разработки и тестирования; полная лицензия необходима для коммерческого использования.

**Q: Влияет ли этот метод на время запуска приложения?**  
**A:** Нет. Список поддерживаемых типов файлов статичен, поэтому его получение практически мгновенно.

**Q: Будет ли список изменяться с новыми версиями библиотеки?**  
**A:** Новые релизы могут добавлять или удалять форматы; всегда используйте последнюю версию, чтобы иметь актуальный список.

## Ресурсы
- [Документация](https://docs.groupdocs.com/merger/java/)
- [Справочник API](https://reference.groupdocs.com/merger/java/)
- [Скачать](https://releases.groupdocs.com/merger/java/)
- [Купить](https://purchase.groupdocs.com/buy)
- [Бесплатный пробный период](https://releases.groupdocs.com/merger/java/)
- [Временная лицензия](https://purchase.groupdocs.com/temporary-license/)
- [Поддержка](https://forum.groupdocs.com/c/merger/)

Не стесняйтесь изучать эти ресурсы для получения более подробной информации и поддержки. Приятного кодинга!

---

**Последнее обновление:** 2026-07-06  
**Тестировано с:** GroupDocs.Merger последняя версия (по состоянию на 2026)  
**Автор:** GroupDocs  

---

## Связанные руководства

- [GroupDocs.Merger for Java: License Setup & File Existence Check Guide](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Load Local Document Java Using GroupDocs.Merger – Guide](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Merge Specific Pages Java – Document Joining Tutorials for GroupDocs.Merger](/merger/java/document-joining/)