---
date: 2026-08-31
description: تعلم كيفية استخراج صفحات محددة من ملف PDF باستخدام GroupDocs.Merger لـ
  .NET. تغطي الأدلة خطوة بخطوة سيناريوهات استخراج Word و PDF و DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: تعلم كيفية استخراج صفحات محددة من ملف PDF باستخدام GroupDocs.Merger
  لـ .NET. تساعدك الأدلة التفصيلية على سحب الصفحات من ملفات PDF و Word و DOCX بكفاءة.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: كيفية استخراج صفحات محددة من ملف PDF باستخدام GroupDocs.Merger
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
title: كيفية استخراج صفحات محددة من ملف PDF باستخدام GroupDocs.Merger
type: docs
url: /ar/net/document-extraction/
weight: 9
---

# كيفية استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger

استخراج صفحات محددة من PDF هو طلب شائع عندما تحتاج إلى إعادة استخدام أو مشاركة أو أرشفة جزء فقط من مستند أكبر. باستخدام GroupDocs.Merger لـ .NET يمكنك سحب صفحات فردية أو نطاقات صفحات أو اختيارات مخصصة من ملفات PDF وWord وDOCX برمجيًا دون تحرير يدوي. يشرح هذا البرنامج التعليمي المفاهيم والمتطلبات المسبقة وسير العمل خطوة بخطوة حتى تتمكن من دمج استخراج الصفحات في أي تطبيق .NET.

## إجابات سريعة
- **ماذا يعني “extract specific pages pdf”؟** يعني ذلك اختيار صفحات فردية أو نطاقات من ملف PDF (أو تنسيق مدعوم آخر) وحفظها كمستند جديد أصغر.  
- **ما هي الصيغ المدعومة؟** يتعامل GroupDocs.Merger مع أكثر من 50 صيغة إدخال وإخراج، بما في ذلك PDF وDOCX وPPTX والصور.  
- **هل أحتاج إلى ترخيص؟** رخصة مؤقتة تعمل للاختبار؛ الترخيص الكامل مطلوب للاستخدام في الإنتاج.  
- **هل يمكنني معالجة ملفات كبيرة؟** نعم – المكتبة تعالج ملفات مئات الصفحات باستخدام البث، مما يحافظ على انخفاض استهلاك الذاكرة.  
- **هل .NET Core مدعوم؟** بالطبع – API يعمل مع .NET Framework 4.6+، .NET Core 3.1+، و .NET 6/7.

## ما هو extract specific pages pdf؟
`extract specific pages pdf` يشير إلى عملية أخذ صفحة أو أكثر من ملف PDF موجود (أو مستند مدعوم) وإنشاء ملف PDF جديد يحتوي فقط على تلك الصفحات. يتيح لك ذلك مشاركة الأقسام ذات الصلة فقط مع الحفاظ على الملف الأصلي سليمًا.

## لماذا استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger؟
GroupDocs.Merger يعالج ما يصل إلى **50+ صيغ ملفات** ويمكنه استخراج الصفحات من مستندات تحتوي على **500+ صفحة** في أقل من **ثانيتين** على خادم عادي. API يعمل دون الحاجة إلى تثبيت Microsoft Office أو Adobe Acrobat، مما يقلل من تعقيد النشر وتكاليف الترخيص.

## المتطلبات المسبقة
- .NET 6 SDK (أو .NET Core 3.1 / .NET Framework 4.6+) مثبت على جهاز التطوير الخاص بك.  
- حزمة NuGet صالحة لـ GroupDocs.Merger for .NET (`GroupDocs.Merger`) مضافة إلى مشروعك.  
- (اختياري) ملف ترخيص مؤقت أو كامل إذا كنت تخطط لتشغيل الكود بعد فترة التقييم.

## كيفية استخراج صفحات محددة من PDF باستخدام C# مع GroupDocs.Merger

حمّل المستند المصدر، حدد الصفحات التي تحتاجها، واحفظ النتيجة. المكتبة تُجرد جميع التفاصيل الخاصة بالتنسيق، لذا يعمل نفس الكود مع PDF وDOCX وPPTX وغيرها.

حمّل ملف المصدر واستدعِ طريقة `Extract` مع أرقام الصفحات المطلوبة. تُنشئ طريقة `Extract` مستندًا جديدًا يحتوي فقط على الصفحات المحددة. تُعيد الطريقة كائن `Document` جديد يمكنك حفظه فورًا. كائن `Document` يمثل تمثيلًا في الذاكرة للملف الناتج.

### الخطوة 1: إنشاء كائن Merger
فئة `Merger` هي نقطة الدخول لتحميل ومعالجة المستندات. أنشئ كائن `Merger` بتمرير مسار ملف المصدر. هذا الكائن يمثل المستند الذي ستعمل عليه.

### الخطوة 2: تحديد الصفحات لاستخراجها
قدّم قائمة بأرقام الصفحات (بدءًا من 1) أو سلسلة نطاق مثل `"1-3,5"` لتخبر المكتبة بالصفحات التي يجب الاحتفاظ بها.

### الخطوة 3: حفظ المستند المستخرج
استدعِ `Save` على كائن `Document`، مع توفير مسار الإخراج والصيغة المطلوبة (مثال: `SaveFormat.Pdf`). `SaveFormat` هو تعداد يحدد نوع ملف الإخراج، مثل PDF. العملية تكتب ملفًا جديدًا يحتوي فقط على الصفحات المحددة.

## المشكلات الشائعة والحلول
- **الصفحات متأخرة بمقدار واحد:** يستخدم GroupDocs.Merger ترقيم الصفحات بدءًا من 1. تأكد أن القائمة تبدأ من 1، لا من 0.  
- **الملفات المحمية بكلمة مرور:** مرّر كلمة المرور إلى مُنشئ `Merger` أو استخدم كائن `LoadOptions`. يوفر `LoadOptions` إعدادات تتحكم في طريقة تحميل المستند، مثل تمكين التخزين المؤقت في الذاكرة.  
- **الملفات الكبيرة تسبب مهلات:** فعّل البث عن طريق ضبط `LoadOptions.UseMemoryCache = true` للحفاظ على انخفاض استهلاك الذاكرة.

## الأسئلة المتكررة

**س: هل يمكنني استخراج صفحات من مستند Word كملف PDF؟**  
ج: نعم – نفس استدعاء `Extract` يعمل مع DOCX، ويمكنك حفظ النتيجة مباشرة كملف PDF باستخدام `SaveFormat.Pdf`.

**س: هل من الممكن استخراج صفحات غير متتالية؟**  
ج: بالتأكيد. قدّم قائمة مفصولة بفواصل مثل `"2,4,7"` أو نطاق مختلط مثل `"1-2,5,8-10"`.

**س: هل تدعم المكتبة ملفات PDF المشفرة؟**  
ج: نعم. قدّم كلمة المرور عند فتح المستند؛ سيقوم الـ API بفك تشفيره تلقائيًا.

**س: كيف يتعامل GroupDocs.Merger مع الصور داخل ملفات PDF؟**  
ج: يتم الحفاظ على الصور كما هي على الصفحات المختارة؛ لا حاجة لخطوات تحويل إضافية.

**س: ما إصدارات .NET المدعومة رسميًا؟**  
ج: .NET Framework 4.6+، .NET Core 3.1+، و .NET 5/6/7 مدعومة بالكامل.

## الدروس المتاحة

### [استخراج صفحات محددة من المستندات باستخدام GroupDocs.Merger لـ .NET](./extract-pages-groupdocs-merger-net/)
Learn how to efficiently extract specific pages using GroupDocs.Merger for .NET. Ideal for managing Word, PDF, and more in professional environments.

### [كيفية استخراج صفحات محددة من مستند باستخدام GroupDocs.Merger لـ .NET في C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Learn how to extract specific pages from documents using GroupDocs.Merger for .NET with this comprehensive guide. Streamline your document management tasks effortlessly.

## موارد إضافية

- [توثيق GroupDocs.Merger لـ .net](https://docs.groupdocs.com/merger/net/)
- [مرجع API لـ GroupDocs.Merger لـ .net](https://reference.groupdocs.com/merger/net/)
- [تحميل GroupDocs.Merger لـ .net](https://releases.groupdocs.com/merger/net/)
- [منتدى GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [دعم مجاني](https://forum.groupdocs.com/)
- [رخصة مؤقتة](https://purchase.groupdocs.com/temporary-license/)

---

**آخر تحديث:** 2026-08-31  
**تم الاختبار مع:** GroupDocs.Merger 23.9 for .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية دمج صفحات PDF محددة باستخدام GroupDocs.Merger لـ .NET: دليل شامل](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [كيفية دمج صفحات محددة من مستندات متعددة باستخدام GroupDocs.Merger لـ .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [تدوير صفحات PDF في .NET باستخدام GroupDocs.Merger: دليل خطوة بخطوة](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)