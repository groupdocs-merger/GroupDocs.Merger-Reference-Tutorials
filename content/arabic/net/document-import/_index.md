---
date: 2026-09-11
description: تعلم كيفية استيراد PDF إلى Word وغيرها من الصيغ باستخدام GroupDocs.Merger
  for .NET، بما في ذلك تضمين PDF في Word وإضافة مرفقات PDF في بضع خطوات سهلة.
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: تعلم كيفية استيراد PDF إلى Word وغيرها من الصيغ باستخدام GroupDocs.Merger
  for .NET، مع تغطية تضمين PDF في Word، إضافة مرفقات PDF، وتضمين OLE.
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: كيفية استيراد PDF إلى Word باستخدام GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: كيفية استيراد PDF إلى Word باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/document-import/
weight: 10
---

# كيفية استيراد PDF إلى Word باستخدام GroupDocs.Merger لـ .NET

في هذا الدليل ستكتشف كيفية **استيراد PDF إلى Word** وأنواع مستندات أخرى باستخدام GroupDocs.Merger لـ .NET. سواء كنت بحاجة إلى تضمين PDF داخل ملف Word، أو إرفاق PDFs بالمستندات الحالية، أو نقل المحتوى بين المخططات، والعروض التقديمية، وجداول البيانات وملفات معالجة النصوص، فإن هذا البرنامج التعليمي يمرّ بك عبر أكثر السيناريوهات شيوعًا، يوضح لماذا هي مهمة، ويظهر لك الخطوات الدقيقة لإنجاز المهمة بسرعة.

## إجابات سريعة
- **هل يمكنني استيراد PDF إلى مستند Word؟** نعم – يتيح لك GroupDocs.Merger تضمين PDF ككائن OLE أو كمحتوى أصلي في ملف .docx.  
- **هل أحتاج إلى مكتبة PDF منفصلة؟** لا، يتعامل SDK الخاص بـ Merger مع استيراد PDF دون تبعيات إضافية.  
- **ما إصدارات .NET المدعومة؟** .NET Framework 4.5+، .NET Core 3.1+، .NET 5/6/7.  
- **هل يلزم ترخيص للإنتاج؟** يلزم وجود ترخيص تجاري للإنتاج؛ تتوفر نسخة تجريبية مجانية للتقييم.  
- **ما هو أقصى حجم PDF يمكنني استيراده؟** يدعم حتى 500 ميغابايت لكل ملف دون تحميل المستند بالكامل في الذاكرة.

## ما هو استيراد PDF إلى Word؟
استيراد PDF إلى Word يعني أخذ محتوى ملف PDF ووضعه داخل مستند Microsoft Word (.docx)، إما ككائن مدمج أو كعناصر أصلية محوّلة، مع الحفاظ على التخطيط والصور وتنسيق النص. يمكن للعملية الحفاظ على تدفق النص، والصور، والجداول، والرسومات المتجهية، مما يضمن أن يبدو ملف Word الناتج قريبًا قدر الإمكان من تخطيط PDF الأصلي.

## لماذا تستخدم GroupDocs.Merger لهذه المهمة؟
يدعم GroupDocs.Merger **أكثر من 30 تنسيقًا للإدخال والإخراج** ويمكنه معالجة المستندات حتى **500 ميغابايت** دون تحميلها بالكامل في الذاكرة RAM، مما يقلل من ضغط الذاكرة على تطبيقات الخادم. كما توفر المكتبة **تضمين OLE مدمج**، مما يتيح لك إرفاق PDFs مباشرةً بملفات Word أو Excel أو PowerPoint في استدعاء API واحد.

## المتطلبات المسبقة
- بيئة تطوير .NET (Visual Studio 2022 أو أحدث).  
- حزمة NuGet الخاصة بـ GroupDocs.Merger لـ .NET مثبتة (`Install-Package GroupDocs.Merger`).  
- ترخيص GroupDocs.Merger صالح للاستخدام في الإنتاج (ترخيص مؤقت متاح للاختبار).

## كيفية استيراد PDF إلى Word خطوة بخطوة

### كيف يمكنني تضمين ملف PDF في مستند Word؟
`Merger` هي الفئة الأساسية في SDK الخاص بـ GroupDocs.Merger التي توفر طرق معالجة المستندات.  
`Insert` يدرج مستندًا أو كائنًا مصدرًا في مستند هدف في موضع محدد.  

حمّل ملف PDF المصدر باستخدام `Merger` واستدعِ `Insert` لوضعه داخل ملف `.docx` الهدف. يتم تنفيذ العملية في سطرين من الشيفرة وتتعامل تلقائيًا مع حزم OLE، لذا يظهر PDF ككائن تفاعلي داخل Word.

### كيف يمكنني إضافة مرفقات PDF إلى ملف Word موجود؟
`AddAttachment` يرفق ملفًا خارجيًا إلى مستند الحاوية، ويخزنه داخل الحزمة لاسترجاعه لاحقًا.  

أنشئ مثالًا من `Merger`، افتح مستند Word، واستخدم طريقة `AddAttachment` لإرفاق PDF. يتم تخزين المرفق داخل حزمة Word ويمكن فتحه مباشرةً من حوار المستند “Insert > Object”.

### كيف يمكنني تضمين كائنات OLE (مثل PDFs) في جداول بيانات Excel؟
`InsertOleObject` يضمّن كائن OLE مثل PDF في خلية جدول بيانات، مما يسمح بفتح تفاعلي من Excel.  

استخدم طريقة `InsertOleObject` على مصنف Excel. تقبل الطريقة مسار ملف PDF وموقع الخلية، وتدرج PDF ككائن OLE يمكن النقر المزدوج عليه لفتحه.

## المشكلات الشائعة والحلول
- **PDF يظهر كأيقونة فقط:** تأكد من حفظ ملف Word الهدف بامتداد `.docx`؛ ملفات `.doc` القديمة لا تدعم كائنات OLE المدمجة.  
- **PDFs الكبيرة تسبب استيرادًا بطيئًا:** استدعِ `MergerSettings.EnableMemoryOptimization = true` قبل الاستيراد للحفاظ على انخفاض استهلاك الذاكرة.  
- **PDF المدمج غير قابل للنقر:** تحقق من أن ملف PDF غير محمي بكلمة مرور؛ لا يمكن لـ Merger تضمين PDFs المشفرة دون توفير كلمة المرور.

## الأسئلة المتكررة

**س: هل يمكنني استيراد صفحات محددة فقط من PDF إلى Word؟**  
ج: نعم – استخدم خيار `PageRange` عند استدعاء `Insert` لتحديد الصفحات التي تريد تضمينها.

**س: هل تحتفظ المكتبة بروابط التشعب داخل PDF عند الاستيراد؟**  
ج: عند التضمين ككائن OLE، تظل روابط التشعب فعّالة داخل عارض PDF؛ عند التحويل إلى محتوى Word أصلي، يتم الاحتفاظ بمعظم روابط التشعب.

**س: هل يمكن استيراد عدة PDFs دفعة واحدة إلى مستند Word واحد؟**  
ج: بالتأكيد. قم بالتكرار عبر مجموعة PDFs الخاصة بك واستدعِ `Insert` لكل ملف؛ تقوم المكتبة بدمجها بشكل متسلسل.

**س: ماذا لو كان PDF يحتوي على رسومات متجهية؟**  
ج: تُحافظ الرسومات المتجهية عند تضمين PDF ككائن OLE؛ تُظهر بوضوح عند أي مستوى تكبير.

**س: هل يعمل GroupDocs.Merger على حاويات Linux؟**  
ج: نعم – يعمل بناء .NET Standard على Linux و macOS و Windows دون أي تبعيات أصلية.

## الدروس المتاحة

### [إضافة مرفقات إلى ملفات PDF باستخدام GroupDocs.Merger لـ .NET&#58; دليل خطوة بخطوة](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Learn how to add attachments to PDFs with GroupDocs.Merger for .NET. This step‑by‑step guide covers setup, implementation, and practical applications.

### [تضمين PDF كـ OLE في PowerPoint باستخدام GroupDocs.Merger لـ .NET&#58; دليل خطوة بخطوة](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Learn how to seamlessly embed a PDF file as an OLE object into your PowerPoint presentation with GroupDocs.Merger for .NET. Follow this comprehensive guide.

### [تضمين PDF في Word باستخدام GroupDocs.Merger لـ .NET&#58; دليل خطوة بخطوة](./embed-pdf-word-groupdocs-merger-dotnet/)
Learn how to seamlessly embed a PDF into a Microsoft Word document using GroupDocs.Merger for .NET. Enhance your documents with dynamic content efficiently.

### [كيفية تضمين كائنات OLE في جداول بيانات Excel باستخدام GroupDocs.Merger لـ .NET](./embed-ole-objects-groupdocs-merger-net/)
Learn how to seamlessly embed OLE objects like PDFs into Excel spreadsheets using GroupDocs.Merger for .NET, enhancing data presentation and functionality.

## موارد إضافية

- [توثيق GroupDocs.Merger لـ .net](https://docs.groupdocs.com/merger/net/)
- [مرجع API لـ GroupDocs.Merger لـ .net](https://reference.groupdocs.com/merger/net/)
- [تحميل GroupDocs.Merger لـ .net](https://releases.groupdocs.com/merger/net/)
- [منتدى GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [دعم مجاني](https://forum.groupdocs.com/)
- [رخصة مؤقتة](https://purchase.groupdocs.com/temporary-license/)

**آخر تحديث:** 2026-09-11  
**تم الاختبار مع:** GroupDocs.Merger 23.12 for .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [تضمين PDF في Word باستخدام GroupDocs.Merger لـ .NET: دليل خطوة بخطوة](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [إضافة مرفقات إلى PDFs باستخدام GroupDocs.Merger لـ .NET: دليل خطوة بخطوة](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [تحميل PDF من URL في .NET باستخدام GroupDocs.Merger: دليل شامل](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)