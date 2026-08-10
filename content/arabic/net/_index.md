---
date: 2026-08-10
description: تعلم كيفية تقسيم ملفات PDF باستخدام GroupDocs.Merger for .NET. تقدم لك
  دروس C# إرشادات لتقسيم ملفات PDF الكبيرة، استخراج الصفحات، ودمج الصور في PDF بكفاءة.
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: دروس GroupDocs.Merger for .NET
og_description: تعلم كيفية تقسيم ملفات PDF باستخدام GroupDocs.Merger for .NET. تقدم
  لك دروس C# إرشادات لتقسيم ملفات PDF الكبيرة، استخراج الصفحات، ودمج الصور في PDF
  بكفاءة.
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: كيفية تقسيم ملفات PDF باستخدام GroupDocs.Merger for .NET – دليل
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  headline: How to split PDF with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  name: How to split PDF with GroupDocs.Merger for .NET
  steps:
  - name: load the PDF document
    text: Create a `PdfDocument` instance by passing the file path or a stream. The
      constructor reads the document header without loading all pages into memory.
  - name: split by page range
    text: Use the `Split` method, providing a `PageRange` object that defines the
      start and end pages. The method returns a collection of new `PdfDocument` objects,
      each representing the requested segment.
  - name: save the resulting files
    text: Iterate over the split documents and call `Save` with a unique file name.
      You can also apply compression or password protection before saving.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then use `Split` or
      `Extract` as you would with an unprotected file.
    question: Can I split a password‑protected PDF?
  - answer: There is no hard limit; the library streams pages, so you can split PDFs
      with thousands of pages as long as you have sufficient disk space for the output
      files.
    question: How many pages can I split at once?
  - answer: It supports cross‑format merging, allowing you to combine PPTX slides
      with PDF pages into a single PDF output.
    question: Does GroupDocs.Merger support merging PowerPoint files with PDFs?
  - answer: Enable streaming mode (`PdfLoadOptions.Stream = true`) to keep memory
      usage low while splitting or extracting pages.
    question: What is the recommended way to handle very large PDFs?
  - answer: Yes. Use the `Bookmarks` collection to identify chapter start pages and
      programmatically call `Split` for each range.
    question: Is there a way to automate splitting of every chapter in a PDF?
  type: FAQPage
tags:
- split PDF
- GroupDocs.Merger
- C# document processing
- PDF manipulation
- document merging
title: كيفية تقسيم ملفات PDF باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/
weight: 10
---

# كيفية تقسيم PDF باستخدام GroupDocs.Merger لـ .NET

## إدارة المستندات المتقدمة باستخدام GroupDocs.Merger

`GroupDocs.Merger for .NET` هي مكتبة .NET تمكّن المطورين من دمج، تقسيم، ومعالجة المستندات عبر أكثر من 50 تنسيق ملف. إذا كنت بحاجة إلى معرفة **كيفية تقسيم PDF**، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام GroupDocs.Merger for .NET، مع سيناريوهات واقعية ونصائح لأفضل الممارسات.

## إجابات سريعة
- **كيفية تقسيم PDF إلى صفحات منفردة؟** استدعِ `PdfDocument.Split` مع نطاق صفحات `1‑1` لكل صفحة.  
- **هل يمكن استخراج صفحات محددة فقط؟** نعم – مرّر أرقام الصفحات المطلوبة إلى `Split` أو `Extract`.  
- **هل يتم دعم حماية كلمة المرور؟** بالتأكيد؛ استخدم `PdfDocument.Protect` قبل الحفظ.  
- **كيفية دمج الصور في PDF؟** حمّل كل صورة كـ `PdfPage` وأضفها إلى مستند جديد.  
- **ماذا عن ملفات PDF الكبيرة؟** استخدم وضع البث لتجنب تحميل الملف بالكامل في الذاكرة.

## ما هو كيفية تقسيم PDF؟
**كيفية تقسيم PDF** تشير إلى عملية تقسيم ملف PDF متعدد الصفحات إلى مستندات PDF أصغر منفصلة — إما بواسطة صفحات فردية، نطاقات صفحات، أو معايير مخصصة — باستخدام واجهات برمجة التطبيقات البرمجية. يُستخدم عادةً لعزل الأقسام، تقليل حجم الملف، أو إعداد المستندات للتوزيع. يمكن تنفيذ العملية برمجيًا عبر مكتبات مثل GroupDocs.Merger، التي تُظهر طرقًا لتحديد نطاقات الصفحات الدقيقة وإعدادات الإخراج.

## لماذا تستخدم GroupDocs.Merger لتقسيم PDF؟
يعالج GroupDocs.Merger **55+** تنسيقًا للمدخلات والمخرجات، ويتعامل مع ملفات PDF تصل إلى **2 GB** دون تحميل كامل في الذاكرة، ويمكنه تقسيم PDF مكوّن من 500 صفحة في أقل من **3 ثوانٍ** على خادم عادي. تجعل هذه الأرقام الم quantified الأداء منه خيارًا موثوقًا لخطوط أنابيب المستندات ذات الإنتاجية العالية.

## كيفية تقسيم ملفات PDF باستخدام GroupDocs.Merger؟
`PdfDocument` هي الفئة الأساسية التي تمثل ملف PDF داخل GroupDocs.Merger. لتقسيم PDF، قم أولاً بتحميل ملف المصدر إلى كائن `PdfDocument`، ثم حدد الصفحات التي ترغب في استخراجها باستخدام طريقة `Split`. تُعيد الطريقة كائنات `PdfDocument` منفصلة لكل جزء، والتي يمكنك حفظها بشكل فردي. يعمل هذا النهج مع أي حجم مستند ويتطلب فقط بضع أسطر من الشيفرة.

### الخطوة 1: تحميل مستند PDF
أنشئ كائن `PdfDocument` بتمرير مسار الملف أو تدفق. يقرأ المُنشئ رأس المستند دون تحميل جميع الصفحات إلى الذاكرة.

### الخطوة 2: التقسيم حسب نطاق الصفحات
استخدم طريقة `Split`، مع توفير كائن `PageRange` الذي يحدد الصفحات البداية والنهاية. تُعيد الطريقة مجموعة من كائنات `PdfDocument` الجديدة، كل منها يمثل الجزء المطلوب.

### الخطوة 3: حفظ الملفات الناتجة
تجول عبر المستندات المقسمة واستدعِ `Save` مع اسم ملف فريد. يمكنك أيضًا تطبيق الضغط أو حماية كلمة المرور قبل الحفظ.

## كيفية دمج الصور في PDF؟
`PdfDocument` هي الفئة الأساسية المستخدمة لإنشاء ملفات PDF جديدة في GroupDocs.Merger. لدمج الصور، حمّل كل ملف صورة وأضفه كصفحة جديدة إلى كائن `PdfDocument` جديد باستخدام طريقة `AddPage`. بعد إضافة جميع الصور، احفظ المستند، مما يحافظ على الدقة الأصلية ويضمّن الصور كصفحات قائمة على المتجهات عندما يسمح التنسيق بذلك. ينتج عن ذلك PDF عالي الجودة يحتوي على جميع الصور المقدمة.

## كيفية تأمين PDF بكلمة مرور؟
`PdfDocument` هو الكائن الذي يمثل مستند PDF ويوفر ميزات الأمان. بعد تحميل أو إنشاء `PdfDocument`، استدعِ طريقة `Protect` مع كلمة مرور للمستخدم وعلامات صلاحية اختيارية مثل الطباعة أو النسخ. تقوم الطريقة بتشفير الملف، وعند استدعاء `Save` لاحقًا، لا يمكن فتح PDF الناتج إلا من قبل المستخدمين الذين يعرفون كلمة المرور، مما يضمن السرية.

## كيفية استخراج صفحات من PDF؟
`PdfDocument` هي الفئة الرئيسية التي تمثل ملف PDF في GroupDocs.Merger. لاستخراج الصفحات، أنشئ كائن `PdfDocument` باستخدام ملف المصدر، ثم استدعِ طريقة `Extract`، مع تمرير قائمة بأرقام الصفحات التي تريد الاحتفاظ بها. تُعيد الطريقة `PdfDocument` جديدًا يحتوي فقط على تلك الصفحات، والتي يمكنك حفظها كملف PDF منفصل. هذه التقنية مفيدة لإنشاء تقارير مخصصة أو مشاركة أقسام محددة.

## كيفية دمج عروض PowerPoint؟
`Merge` هي طريقة توفرها GroupDocs.Merger تقوم بربط مستندات متعددة في ملف إخراج واحد. لدمج عروض PowerPoint، حمّل كل ملف .pptx ككائن Document، ثم استدعِ طريقة `Merge` على `PdfDocument` أو `PresentationDocument` جديد، مع تمرير مجموعة المستندات المصدر. تحافظ المكتبة على تحريكات الشرائح، الانتقالات، والتنسيق، مما ينتج عرضًا موحدًا يمكن حفظه كملف PDF أو PPTX.

## كيفية تقسيم صفحات PDF الكبيرة؟
`PdfLoadOptions.Stream` هي خاصية تمكّن وضع البث، مما يسمح لـ GroupDocs.Merger بمعالجة ملفات PDF الكبيرة دون تحميل المستند بالكامل إلى الذاكرة. عند العمل مع ملفات PDF ضخمة جدًا، اضبط `PdfLoadOptions.Stream` على true قبل تحميل الملف. يقلل ذلك من استهلاك الذاكرة ويسمح لك بتقسيم أو استخراج الصفحات بفعالية، حتى للملفات التي يزيد حجمها عن 1 GB، مع الحفاظ على الأداء.

## الميزات والقدرات الرئيسية
- **دمج مستندات متعددة** عبر أكثر من 55 تنسيقًا في ملف موحد واحد
- **ضم صفحات أو نطاقات صفحات محددة** من مستندات مصدر مختلفة
- **تقسيم المستندات** حسب أرقام الصفحات، النطاقات، أو معايير الصفحات الزوجية/الفردية
- **التلاعب بترتيب الصفحات** عبر النقل، الحذف، الدوران، أو عمليات التبديل
- **تأمين المستندات** بحماية كلمة مرور وتحكم دقيق في الصلاحيات
- **استخراج صفحات محددة** لإنشاء مستندات جديدة مستهدفة
- **معالجة أكثر من 55 تنسيقًا** بما في ذلك PDF، Office، الصور، والأرشيفات باستخدام واجهة برمجة تطبيقات موحدة

## فئات دروس GroupDocs.Merger لـ .NET

### [دمج وضغط الملفات](./merge-compress-files/)
تعلم دمج وضغط صيغ الأرشيف مثل 7z و TAR و ZIP بكفاءة. تقودك دروسنا عبر دمج الأرشيفات باستخدام GroupDocs.Merger for .NET مع أمثلة C# كاملة.

### [دمج الصور](./image-merging/)
إتقان تقنيات دمج BMP و GIF و PNG و SVG و TIFF وغيرها من صيغ الصور. اكتشف كيفية دمج الصور في مستندات واحدة مع الحفاظ على الجودة والتنسيق.

### [دمج المستندات](./document-merging/)
دمج DOC و DOCX و PDF و RTF وغيرها من صيغ المستندات في ملفات موحدة. تغطي هذه الدروس سيناريوهات دمج المستندات مع خطوات تنفيذ مفصلة وأفضل الممارسات.

### [دمج جداول البيانات](./spreadsheet-merging/)
دمج ملفات Excel (XLAM، XLS، XLSX، XLSM، XLTX) وغيرها من صيغ جداول البيانات مع الحفاظ على سلامة البيانات، الصيغ، والتنسيق من خلال هذه الأدلة خطوة بخطوة.

### [دمج Visio](./visio-merging/)
دمج مخططات ورسومات Visio (VDX، VSDM، VSDX، VSSM، VSSX) بكفاءة عبر دروسنا المتخصصة لإدارة مستندات المخططات في تطبيقات .NET.

### [دمج العروض التقديمية](./presentation-merging/)
تعلم دمج PowerPoint وغيرها من صيغ العروض التقديمية (PPS، PPSX، PPT، OTP) مع الحفاظ على الشرائح، الرسوم المتحركة، والتنسيق مع أمثلة شيفرة كاملة.

### [تحميل المستندات](./document-loading/)
اكتشف أساليب مختلفة لتحميل المستندات من الملفات، التدفقات، وعناوين URL مع تكوين مناسب لمختلف الصيغ. إتقان الخطوة الأساسية الأولى في معالجة المستندات.

### [معلومات المستند](./document-information/)
استخراج بيانات التعريف القيمة من المستندات بما في ذلك تفاصيل الصيغة، عدد الصفحات، والخصائص. تعلم تحليل المستندات برمجيًا قبل معالجتها.

### [ضم المستندات](./document-joining/)
دمج ملفات متعددة بسلاسة باستخدام تقنيات الضم المتقدمة. تُظهر لك دروسنا كيفية دمج المستندات مع تحكم دقيق في المحتوى والبنية.

### [دمج مخصص حسب الصيغة](./format-specific-merging/)
استكشف عمليات دمج مُحسّنة مخصصة لصيغ الملفات المحددة. تعلم تقنيات متخصصة لأنواع المستندات المختلفة لتحقيق أفضل النتائج.

### [خيارات الضم المتقدمة](./advanced-joining-options/)
ارتق بدمج المستندات إلى المستوى التالي عبر هذه الدروس المتقدمة التي تغطي اختيار الصفحات المعقد، الدمج عبر الصيغ، واستراتيجيات الحفاظ على المحتوى.

### [أمان المستند](./document-security/)
تنفيذ حماية قوية لمستنداتك. تعلم إضافة، إزالة، وتحديث كلمات المرور، إدارة الصلاحيات، وضمان سرية المستند في تطبيقاتك.

### [عمليات الصفحات](./page-operations/)
إتقان التحكم الدقيق في صفحات المستند عبر دروس حول إعادة ترتيب، تدوير، حذف، وتعديل الصفحات الفردية لإدارة مستندات مخصصة.

### [استخراج المستند](./document-extraction/)
استخراج محتوى محدد من المستندات عبر هذه الأدلة التفصيلية. تعلم اختيار وحفظ صفحات أو أقسام معينة كملفات منفصلة بأقل قدر من الشيفرة.

### [استيراد المستند](./document-import/)
تعزيز المستندات بمحتوى خارجي بما في ذلك كائنات OLE والملفات المدمجة. تعلم استيراد المحتوى من مصادر مختلفة لإثراء مستنداتك.

### [عمليات الصور](./image-operations/)
معالجة ملفات الصور بفعالية عبر دروسنا الشاملة التي تغطي دمج الصور، التحويل، وتقنيات التلاعب في تطبيقات .NET الخاصة بك.

### [تقسيم المستند](./document-splitting/)
تقسيم المستندات بذكاء إلى مكونات أصغر عبر هذه الدروس حول تقسيم المستندات حسب أرقام الصفحات، النطاقات، والمعايير المخصصة.

### [عمليات النص](./text-operations/)
التعامل مع المستندات النصية بفعالية باستخدام أدلتنا حول معالجة TXT، CSV، وغيرها من صيغ النص، بما في ذلك تقنيات التقسيم والدمج على أساس السطر.

### [التراخيص](./licensing/)
تهيئة GroupDocs.Merger بشكل صحيح في مشاريعك عبر دروس الترخيص التفصيلية التي تغطي جميع سيناريوهات النشر والبيئات.

## صيغ الملفات المدعومة

GroupDocs.Merger for .NET يدعم **أكثر من 55** صيغة مستند شائعة، بما في ذلك:

- **صيغ المستندات**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **جداول البيانات**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **العروض التقديمية**: PPT, PPTX, PPS, PPSX, ODP
- **الصور**: BMP, GIF, JPG, PNG, SVG, TIFF
- **المخططات**: VDX, VSDX, VSX, VTX, VSTX, VSSX
- **الأرشيفات**: ZIP, TAR, 7Z
- **والمزيد!**

## الأسئلة المتكررة

**س: هل يمكنني تقسيم PDF محمي بكلمة مرور؟**  
ج: نعم. حمّل المستند مع معامل كلمة المرور، ثم استخدم `Split` أو `Extract` كما تفعل مع ملف غير محمي.

**س: كم عدد الصفحات التي يمكنني تقسيمها في مرة واحدة؟**  
ج: لا يوجد حد ثابت؛ المكتبة تبث الصفحات، لذا يمكنك تقسيم ملفات PDF التي تحتوي على آلاف الصفحات طالما لديك مساحة قرص كافية للملفات الناتجة.

**س: هل يدعم GroupDocs.Merger دمج ملفات PowerPoint مع ملفات PDF؟**  
ج: يدعم الدمج عبر الصيغ، مما يتيح لك دمج شرائح PPTX مع صفحات PDF في ملف PDF واحد.

**س: ما هي الطريقة الموصى بها للتعامل مع ملفات PDF الكبيرة جدًا؟**  
ج: فعّل وضع البث (`PdfLoadOptions.Stream = true`) للحفاظ على استهلاك الذاكرة منخفضًا أثناء تقسيم أو استخراج الصفحات.

**س: هل هناك طريقة لأتمتة تقسيم كل فصل في PDF؟**  
ج: نعم. استخدم مجموعة `Bookmarks` لتحديد صفحات بدء الفصول واستدعِ برمجيًا `Split` لكل نطاق.

---

**آخر تحديث:** 2026-08-10  
**تم الاختبار مع:** GroupDocs.Merger 23.9 for .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية دمج ملفات PDF بفعالية باستخدام GroupDocs.Merger لـ .NET](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [كيفية دمج صفحات PDF محددة باستخدام GroupDocs.Merger لـ .NET: دليل شامل](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [كيفية دمج ملفات PDF مع العلامات المرجعية باستخدام GroupDocs.Merger لـ .NET](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)