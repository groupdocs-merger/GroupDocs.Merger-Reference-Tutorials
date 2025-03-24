---
title: دمج ملفات XLS
linktitle: دمج ملفات XLS
second_title: GroupDocs.Merger .NET API
description: تعرف على كيفية دمج ملفات Excel في .NET باستخدام GroupDocs.Merger لمعالجة المستندات بسلاسة. اتبع البرنامج التعليمي خطوة بخطوة.
weight: 11
url: /ar/net/spreadsheet-merging/merging-xls-files/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية دمج ملفات XLS (Excel). GroupDocs.Merger عبارة عن واجهة برمجة تطبيقات قوية لمعالجة المستندات تمكن المطورين من دمج المستندات وتقسيمها وإعادة ترتيبها ومعالجتها بسهولة داخل تطبيقات .NET الخاصة بهم. على وجه التحديد، سوف نركز على دمج ملفات XLS خطوة بخطوة باستخدام أساليب GroupDocs.Merger البديهية.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من إعداد المتطلبات الأساسية التالية:
- Visual Studio: قم بتثبيت Visual Studio على جهازك.
-  GroupDocs.Merger لـ .NET: قم بتنزيل وتثبيت GroupDocs.Merger لـ .NET من[هنا](https://releases.groupdocs.com/merger/net/).
- .NET Framework: تأكد من تثبيت .NET Framework.
- نماذج ملفات XLS: قم بإعداد ملفات XLS التي تريد دمجها.

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء اللازمة لاستخدام GroupDocs.Merger في مشروعك:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## الخطوة 1: تهيئة دليل الإخراج
أولاً، حدد الدليل الذي تريد حفظ ملف XLS المدمج فيه:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## الخطوة 2: تحميل ودمج ملفات XLS
لنقم الآن بتحميل ودمج ملفات XLS باستخدام GroupDocs.Merger:
```csharp
// قم بتحميل ملف XLS المصدر
using (var merger = new Merger("Your Sample File"))
{
    // أضف ملف XLS آخر لدمجه
    merger.Join("Your Sample File");
    
    // دمج ملفات XLS وحفظ النتيجة
    merger.Save(outputFile);
}
```
## الخطوة 3: عرض موقع الإخراج
وأخيرًا، قم بعرض رسالة تشير إلى اكتمال ملف XLS المدمج وموقعه:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية دمج ملفات XLS. باتباع الخطوات المتوفرة، يمكنك دمج ملفات Excel المتعددة بكفاءة برمجيًا داخل تطبيقات .NET الخاصة بك.

## الأسئلة الشائعة
### هل GroupDocs.Merger متوافق مع تنسيقات المستندات الأخرى؟
نعم، يدعم GroupDocs.Merger تنسيقات المستندات المختلفة مثل PDF وDOCX وXLSX وPPTX والمزيد.
### هل يمكنني تقسيم المستندات باستخدام GroupDocs.Merger؟
قطعاً! يسمح لك GroupDocs.Merger بتقسيم المستندات بناءً على متطلباتك.
### أين يمكنني العثور على المزيد من الموارد والدعم لـ GroupDocs.Merger؟
يمكنك استكشاف الوثائق وطرح الأسئلة على[منتدى مستندات المجموعة](https://forum.groupdocs.com/c/merger/32).
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Merger؟
 نعم، يمكنك البدء بـ أ[تجربة مجانية](https://releases.groupdocs.com/) لتقييم الوظيفة.
### كيف يمكنني شراء ترخيص GroupDocs.Merger؟
 قم بزيارة[صفحة الشراء](https://purchase.groupdocs.com/buy) للحصول على ترخيص يناسب احتياجاتك.