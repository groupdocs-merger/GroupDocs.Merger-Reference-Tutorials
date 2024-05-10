---
title: Руководство по объединению файлов XLSM
linktitle: Руководство по объединению файлов XLSM
second_title: GroupDocs.Merger .NET API
description: Легко объединяйте файлы XLSM с помощью GroupDocs.Merger для .NET. Эффективно объединяйте книги Excel программно. Расширьте свои возможности манипулирования документами.
type: docs
weight: 13
url: /ru/net/spreadsheet-merging/guide-merging-xlsm-files/
---
## Введение
В этом уроке мы рассмотрим, как объединить файлы XLSM (книга Excel с поддержкой макросов). GroupDocs.Merger — это мощная библиотека, которая позволяет разработчикам манипулировать форматами документов, включая программное слияние, разделение и изменение файлов.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующее:
-  GroupDocs.Merger для .NET: загрузите и установите библиотеку с сайта[здесь](https://releases.groupdocs.com/merger/net/).
- Среда разработки: установите Visual Studio или любую совместимую среду разработки .NET.
- Файлы XLSM: подготовьте файлы XLSM, которые вы хотите объединить.

## Импортировать пространства имен
Сначала включите необходимые пространства имен в свой проект .NET:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Шаг 1. Определите выходную папку и имя файла
Начните с определения выходной папки и имени объединенного файла XLSM:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Шаг 2. Загрузите и объедините файлы XLSM
Затем загрузите исходные файлы XLSM и объедините их в один файл:
```csharp
// Загрузите исходный файл XLSM
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Добавьте еще один файл XLSM для объединения.
    merger.Join("Your Sample File");
    // Объедините файлы XLSM и сохраните результат
    merger.Save(outputFile);
}
```
## Шаг 3. Проверьте завершение слияния
Наконец, уведомите пользователя об успешном завершении слияния и отобразите путь вывода:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Заключение
Вы узнали, как программно объединять файлы XLSM. Эта библиотека упрощает задачи манипулирования документами, обеспечивая эффективное объединение файлов в ваших приложениях .NET.

## Часто задаваемые вопросы
### Может ли GroupDocs.Merger обрабатывать большие файлы XLSM?
Да, GroupDocs.Merger эффективно обрабатывает большие файлы XLSM без проблем с производительностью.
### Поддерживает ли GroupDocs.Merger другие форматы файлов, кроме XLSM?
Да, GroupDocs.Merger поддерживает различные форматы документов, такие как DOCX, PDF, PPTX и другие.
### Совместим ли GroupDocs.Merger с приложениями .NET Core?
Да, GroupDocs.Merger совместим со средами .NET Framework и .NET Core.
### Могу ли я объединить зашифрованные файлы XLSM с помощью GroupDocs.Merger?
Да, GroupDocs.Merger поддерживает объединение зашифрованных файлов XLSM с правильными учетными данными.
### Предоставляет ли GroupDocs.Merger возможности пакетной обработки?
Да, GroupDocs.Merger позволяет выполнять пакетную обработку для одновременного объединения нескольких файлов XLSM.