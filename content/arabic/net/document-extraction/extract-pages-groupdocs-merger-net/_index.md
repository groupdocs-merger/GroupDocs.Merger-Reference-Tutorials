---
date: '2026-09-26'
description: تعلم كيفية استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger for .NET،
  بما في ذلك استخراج الصفحات من Word ومعالجة المستندات الكبيرة بكفاءة.
keywords:
- extract specific pages pdf
- extract pages from word
- extract pages from large document
lastmod: '2026-09-26'
og_description: تعلم كيفية استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger for
  .NET. يوضح هذا الدليل إعدادًا خطوة بخطوة، وتكوينًا بدون كتابة كود، ونصائح الأداء
  لـ Word و PDF والمستندات الكبيرة.
og_image_alt: Guide showing how to extract specific pages pdf using GroupDocs.Merger
  for .NET
og_title: استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger for .NET
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
title: استخراج صفحات محددة من PDF باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/document-extraction/extract-pages-groupdocs-merger-net/
weight: 1
---

# استخراج صفحات PDF محددة باستخدام GroupDocs.Merger لـ .NET

استخراج صفحات PDF محددة من مستند متعدد الصفحات هو طلب شائع عندما تحتاج إلى مشاركة الأقسام ذات الصلة فقط، تقليل حجم الملف، أو أتمتة سير عمل المراجعة. في هذا الدرس ستكتشف كيف يتيح لك GroupDocs.Merger لـ .NET استخراج الصفحات الدقيقة — سواء كانت من PDF أو ملف Word أو أي من أكثر من 30 تنسيقًا مدعومًا — باستخدام نهج واضح برمجي.

## إجابات سريعة
- **هل يمكن لـ GroupDocs.Merger استخراج صفحات من مستندات Word؟** نعم، يعمل مع DOCX و DOC وغيرها من تنسيقات Office.  
- **هل هناك حد لحجم الملف؟** يمكن للمكتبة التعامل مع ملفات تصل إلى 2 GB دون تحميل المستند بالكامل في الذاكرة.  
- **هل أحتاج إلى ترخيص للتطوير؟** تتوفر نسخة تجريبية مجانية؛ الترخيص مطلوب للاستخدام في الإنتاج.  
- **هل سيعمل على .NET 6؟** بالتأكيد — يدعم GroupDocs.Merger .NET Framework 4.5+، .NET Core 3.1+، و .NET 5/6+.  
- **كم عدد الصفحات التي يمكنني استخراجها في مرة واحدة؟** يمكنك تحديد صفحات فردية، نطاقات، أو اختيارات أزواج/فردية في استدعاء واحد.

## ما هو GroupDocs.Merger لـ .NET؟
GroupDocs.Merger لـ .NET هو مكتبة تعمل على الخادم تمكّن من دمج، تقسيم، تدوير، واستخراج الصفحات من أكثر من 30 تنسيق مستند دون الحاجة إلى Microsoft Office أو Adobe Acrobat. تعالج الملفات بطريقة تدفقية، مما يحافظ على استهلاك الذاكرة منخفضًا حتى لملفات PDF التي تحتوي على مئات الصفحات.

## لماذا استخراج صفحات PDF محددة؟
استخراج صفحات PDF محددة يقلل من استهلاك النطاق الترددي، يسرّع التعاون، ويضمن بقاء الأقسام السرية مخفية. الفائدة المرقّمة: تقارير المؤسسات تشير إلى تحسين حتى 40 % في دورات مراجعة المستندات عندما يشاركون فقط الصفحات المطلوبة بدلاً من الملفات الكاملة. بالإضافة إلى ذلك، الملفات الأصغر تحسن أوقات التحميل لمشاهد الويب وتقلل تكاليف التخزين.

## المتطلبات المسبقة
- Visual Studio 2022 أو أي بيئة تطوير متوافقة مع .NET.  
- .NET 6 SDK (أو .NET Framework 4.7.2+).  
- الوصول إلى مصدر NuGet لتثبيت **GroupDocs.Merger**.  
- معرفة أساسية بـ C# وصلاحيات نظام الملفات.

## كيفية استخراج صفحات PDF محددة خطوة بخطوة

حمّل ملف المصدر، حدد الصفحات التي تحتاجها، واحفظ النتيجة — كل ذلك في بضع أسطر من الشيفرة.

### الإجابة المباشرة
`Merger` هو الفئة الأساسية التي تنسق عمليات معالجة المستندات. `ExtractOptions` يحدد الصفحات التي سيتم استخراجها وكيفية معالجتها. `Extract` ينفّذ عملية الاستخراج بناءً على الخيارات المقدمة ويكتب النتيجة إلى ملف جديد. لاستخراج صفحات PDF محددة، أنشئ كائن `Merger` مع ملف المصدر، اضبط كائن `ExtractOptions` الذي يحدد نطاق الصفحات والوضع (زوجي، فردي، أو مخصص)، ثم استدعِ `Extract` واحفظ ملف الإخراج. يعمل هذا التدفق بالكامل في أقل من ثانية لملفات PDF ذات 100 صفحة تقريبًا على خادم عادي.

### الخطوة 1: تثبيت حزمة NuGet
افتح طرفية في مجلد المشروع وشغّل أحد الأوامر التالية:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager Console**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – استخدم الواجهة للبحث عن “GroupDocs.Merger” وانقر **Install**.

### الخطوة 2: تعريف مسارات الملفات
حدد مسارات مطلقة أو نسبية للملف الإدخالي والملف الإخراجي الذي تريد إنشاؤه.

**Definition anchor**  
`ExtractOptions` هو كائن التكوين الذي يخبر المكتبة بالصفحات التي يجب استخراجها وكيفية التعامل معها.  
```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY\\Sample.docx"; // Input document path
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "ExtractedPages.docx"); // Output document path
```  

### الخطوة 3: ضبط خيارات الاستخراج
أنشئ مثيلًا من `ExtractOptions`، عيّن `StartPageNumber` و `EndPageNumber`، واختر `RangeMode` (مثال: `Even`). هذا يُخبر المحرك باختيار كل صفحة ثانية ضمن النطاق.

**Definition anchor**  
`Merger` هو الفئة الأساسية التي تنسق جميع عمليات معالجة المستندات، بما في ذلك الاستخراج، الدمج، وتدوير الصفحات.  
```csharp
ExtractOptions extractOptions = new ExtractOptions(1, 3, RangeMode.EvenPages);
```  

### الخطوة 4: استخراج وحفظ
استدعِ طريقة `Extract` على مثيل `Merger`، مع تمرير الخيارات ومسار الإخراج. تقوم المكتبة بكتابة الملف الجديد دون تحميل المصدر بالكامل في الذاكرة، وهو مثالي للمستندات الكبيرة.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ExtractPages(extractOptions);
    merger.Save(filePathOut); // Save the result to a specified path
}
```  

## المشكلات الشائعة والحلول
- **الصفحات غير مُستخرجة** – تحقق مرة أخرى من أن `StartPageNumber` و `EndPageNumber` يبدأان من 1 وأن ملف المصدر يحتوي فعليًا على النطاق المطلوب.  
- **أخطاء نفاد الذاكرة على ملفات ضخمة** – تأكد من أنك تستخدم واجهة برمجة التطبيقات المتدفقة (الافتراضية) وأن عمليتك تمتلك ذاكرة افتراضية كافية؛ فكر في زيادة إعداد `maxMemory` في تكوين المكتبة.  
- **ملفات محمية بكلمة مرور** – يتيح لك `LoadOptions` ضبط معلمات مثل كلمات المرور عند تحميل مستند محمي. قدّم كلمة المرور عبر `LoadOptions` قبل إنشاء مثيل `Merger`.

## التطبيقات العملية
1. **مراجعة المستندات** – استخراج فقط البنود التي يحتاجها المراجع، مع إبقاء البقية سرية.  
2. **التعليم** – إنشاء مواد توزيع مخصصة عن طريق استخراج شرائح المحاضرات أو فصول الكتب.  
3. **سير العمل القانوني** – عزل صفحات المرفقات لتقديمها للمحكمة دون كشف ملفات القضية بالكامل.

## اعتبارات الأداء
يعالج GroupDocs.Merger المستندات بطريقة تدفقية، مما يتيح له التعامل مع ملفات تصل إلى **2 GB** مع الحفاظ على الذاكرة القصوى أقل من **150 MB**. للحصول على أفضل النتائج، غلف كائن `Merger` داخل بيان `using` لضمان التخلص منه، وأعد استخدام نفس المثيل عند استخراج نطاقات متعددة من المصدر نفسه.

## الخلاصة
أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج لاستخراج صفحات PDF محددة باستخدام GroupDocs.Merger لـ .NET. من خلال ضبط `ExtractOptions` والاستفادة من محرك التدفق في المكتبة، يمكنك أتمتة تقطيع المستندات لأي تنسيق مدعوم، تحسين سرعة التعاون، والحفاظ على المعلومات الحساسة تحت السيطرة.

**الخطوات التالية** – استكشف القدرات الأخرى للمكتبة مثل دمج المستندات، تدوير الصفحات، وتطبيق العلامات المائية لإنشاء خطوط معالجة مستندات مؤتمتة بالكامل.

## الأسئلة المتكررة
**س: ما هي صيغ الملفات التي يمكنني استخراج الصفحات منها؟**  
ج: يدعم GroupDocs.Merger أكثر من 30 صيغة، بما في ذلك PDF و DOCX و XLSX و PPTX و HTML وأنواع الصور مثل PNG و JPEG.

**س: هل يمكنني استخراج صفحات غير متتالية (مثال: 1، 3، 5)؟**  
ج: نعم، يمكنك تمرير قائمة بأرقام الصفحات الفردية أو نطاقات متعددة إلى `ExtractOptions`.

**س: كيف أتعامل مع ملفات PDF محمية بكلمة مرور؟**  
ج: قدّم كلمة المرور عبر `LoadOptions` عند إنشاء مثيل `Merger`؛ سيستمر الاستخراج بشكل طبيعي بعد ذلك.

**س: هل هناك حد لعدد الصفحات التي يمكن استخراجها في استدعاء واحد؟**  
ج: لا يوجد حد صريح؛ القيد العملي الوحيد هو الذاكرة المتاحة، التي تظل منخفضة بفضل التدفق.

**س: هل تتطلب المكتبة تثبيت Microsoft Office أو Adobe Acrobat؟**  
ج: لا حاجة لتطبيقات خارجية؛ جميع المعالجة تتم داخل بيئة تشغيل .NET.

## الموارد
- [التوثيق](https://docs.groupdocs.com/merger/net/)
- [مرجع API](https://reference.groupdocs.com/merger/net/)
- [تحميل GroupDocs.Merger لـ .NET](https://releases.groupdocs.com/merger/net/)
- [شراء ترخيص](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية مجانية](https://releases.groupdocs.com/merger/net/)
- [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [منتدى الدعم](https://forum.groupdocs.com/c/merger/)

---

**آخر تحديث:** 2026-09-26  
**تم الاختبار مع:** GroupDocs.Merger 23.11 for .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة
- [كيفية دمج صفحات PDF محددة باستخدام GroupDocs.Merger لـ .NET: دليل شامل](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [كيفية إزالة صفحات من المستندات باستخدام GroupDocs.Merger لـ .NET: دليل خطوة بخطوة](/merger/net/page-operations/groupdocs-merger-remove-pages-net-tutorial/)
- [كيفية نقل الصفحات داخل مستند باستخدام GroupDocs.Merger لـ .NET: دليل شامل](/merger/net/page-operations/move-pages-groupdocs-merger-dotnet/)