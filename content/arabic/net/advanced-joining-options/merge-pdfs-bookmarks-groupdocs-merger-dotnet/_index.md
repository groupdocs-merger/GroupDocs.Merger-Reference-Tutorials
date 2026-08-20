---
date: '2026-08-20'
description: تعرف على كيفية دمج ملفات pdf مع العلامات المرجعية باستخدام GroupDocs.Merger
  for .NET، بما في ذلك الإعداد، أمثلة الشيفرة، وأفضل الممارسات لدمج مستندات PDF.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: تعرف على كيفية دمج ملفات pdf مع العلامات المرجعية باستخدام GroupDocs.Merger
  for .NET. اتبع شيفرة خطوة بخطوة لدمج مستندات PDF مع الحفاظ على التنقل.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: كيفية دمج ملفات pdf مع العلامات المرجعية باستخدام GroupDocs.Merger for .NET
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
title: كيفية دمج ملفات pdf مع العلامات المرجعية باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# كيفية دمج ملفات PDF مع الإشارات المرجعية باستخدام GroupDocs.Merger لـ .NET

دمج عدة ملفات PDF مع الحفاظ على الإشارات المرجعية الأصلية يمكن أن يوفر لك ساعات من إعادة التنظيم اليدوي. في هذا البرنامج التعليمي ستتعلم كيفية **دمج ملفات PDF مع الإشارات المرجعية** باستخدام GroupDocs.Merger لـ .NET، من إعداد المشروع إلى عينة شفرة جاهزة للإنتاج.

## إجابات سريعة
- **أي مكتبة تدعم الدمج مع الحفاظ على الإشارات المرجعية؟** GroupDocs.Merger لـ .NET.  
- **هل يمكن دمج أكثر من ملفين PDF في آن واحد؟** نعم – أضف عدد الملفات المصدر التي تحتاجها.  
- **هل أحتاج إلى ترخيص للتطوير؟** نسخة تجريبية مجانية تكفي للاختبار؛ الترخيص الدائم مطلوب للإنتاج.  
- **هل .NET Core مدعوم؟** بالتأكيد – المكتبة تعمل مع .NET Core، .NET 5/6 والإطار الكامل .NET Framework.  
- **ما هو أكبر حجم ملف يمكنه التعامل معه؟** حتى 2 GB لكل مستند، يتم معالجتها دون تحميل الملف بالكامل إلى الذاكرة.

## ما هو دمج ملفات PDF مع الإشارات المرجعية؟
**دمج ملفات PDF مع الإشارات المرجعية** يعني أخذ عدة مستندات PDF ودمجها في ملف واحد مع الحفاظ على هيكلية الإشارات المرجعية لكل مستند مصدر. يحتفظ ملف PDF الناتج ببنية التنقل الأصلية، مما يسمح للقراء بالانتقال مباشرة إلى الأقسام التي نشأت من كل ملف فردي، وهو أمر أساسي للتقارير الكبيرة أو الأدلة المجمعة.

## لماذا ندمج ملفات PDF مع الإشارات المرجعية؟
الحفاظ على الإشارات المرجعية عند دمج ملفات PDF يحسن من التنقل في المستندات المجمعة، مما يتيح للمستخدمين تحديد الفصول أو الأقسام بسرعة دون الحاجة للتمرير عبر الملف بالكامل. يحافظ GroupDocs.Merger على هيكل المخطط الأصلي، يقلل من جهد إعادة التنظيم اليدوي، ويدعم الملفات الكبيرة حتى 2 GB مع استهلاك ذاكرة منخفض، مما يجعله مثالياً لتدفقات العمل على مستوى المؤسسات.

## المتطلبات المسبقة
- **.NET Core SDK** (3.1 أو أحدث) أو **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** أو أي بيئة تطوير تدعم .NET.  
- معرفة أساسية بـ C# وإلمام بعمليات إدخال/إخراج الملفات.  

## إعداد GroupDocs.Merger لـ .NET

### التثبيت
أضف المكتبة إلى مشروعك باستخدام أحد الأوامر التالية:

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

**NuGet Package Manager UI:**  
- ابحث عن “GroupDocs.Merger” وقم بتثبيت أحدث نسخة.

### الحصول على الترخيص
- **نسخة تجريبية مجانية:** حمّلها من صفحة [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **ترخيص مؤقت:** احصل عليه عبر صفحة [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **ترخيص كامل:** اشترِه من [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### التهيئة الأساسية
فئة `Merger` هي نقطة الدخول لجميع عمليات الدمج.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
هذا النطاق يمنحك الوصول إلى مجموعة كاملة من ميزات معالجة PDF.

## كيفية دمج ملفات PDF مع الإشارات المرجعية في .NET

حمّل ملف PDF الأساسي، اضبط معالجة الإشارات المرجعية، أضف ملفات إضافية، واحفظ النتيجة – كل ذلك في بضع أسطر مختصرة من الشفرة.

**إجابة مباشرة (40‑70 كلمة):**  
أنشئ كائن `Merger` مع أول ملف PDF، فعّل `PdfJoinOptions.UseBookmarks`، أضف كل ملف PDF لاحق عبر `Join`، ثم استدعِ `Save` لكتابة الملف المدمج. يحافظ هذا النهج على كل هيكلية إشارات مرجعية أصلية ويعمل في تمريرة واحدة، مما يقلل استهلاك الذاكرة.

### الخطوة 1: تعريف مسارات الأدلة
قم بإعداد مجلدات المصدر والإخراج حتى يتمكن الكود من العثور على ملفات PDF التي تريد دمجها.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### الخطوة 2: تحميل ملف PDF الأساسي
`Merger` يمثل المستند الرئيسي الذي ستضيف إليه الآخرين.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### الخطوة 3: ضبط خيارات الحفاظ على الإشارات المرجعية
`PdfJoinOptions` يتحكم في سلوك الدمج؛ علم `UseBookmarks` يوجه المحرك للحفاظ على الإشارات المرجعية الموجودة.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### الخطوة 4: إضافة ملفات PDF إضافية
استدعِ `Join` لكل ملف إضافي. تقوم المكتبة تلقائياً بدمج أشجار الإشارات المرجعية تحت مخطط المستند الرئيسي.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### الخطوة 5: حفظ ملف PDF المدمج
حدد مسار الإخراج والصيغة؛ تقوم المكتبة بكتابة ملف PDF واحد يحتفظ بجميع إدخالات الإشارات المرجعية.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## المشكلات الشائعة والحلول
- **فقدان الإشارات المرجعية:** تأكد من ضبط `UseBookmarks = true` في `PdfJoinOptions`.  
- **أخطاء المسار:** استخدم `Path.Combine` وتحقق من وجود الملفات قبل الدمج.  
- **الملفات الكبيرة تسبب ارتفاع الذاكرة:** عالج ملفات PDF بشكل متسلسل وتخلص من كائن `Merger` بعد كل عملية حفظ.

## تطبيقات عملية
1. **تجميع التقارير المالية** – حافظ على أقسام الربع السنوي قابلة للوصول فوراً عبر الإشارات المرجعية.  
2. **حزم مواد الدورات التعليمية** – دمج محاضرات PDF مع الحفاظ على تنقل الفصول للطلاب.  
3. **حزم وثائق المشاريع** – دمج مواصفات التصميم، خطط الاختبار، وملاحظات الإصدار في ملف واحد قابل للبحث.

## اعتبارات الأداء
- عالج ملفاً واحداً في كل مرة عند دمج أكثر من 20 ملف PDF لتقليل استهلاك الذاكرة.  
- استخدم أحدث نسخة من .NET runtime (مثل .NET 6) للحصول على تحسينات في تجميع JIT وكفاءة جمع القمامة.  
- للملفات التي تتجاوز 500 MB، فعّل وضع البث عبر `MergerSettings` لتجنب تحميل المستند بالكامل في الذاكرة.

## الأسئلة المتكررة

**س: ما هو GroupDocs.Merger؟**  
ج: GroupDocs.Merger هي مكتبة .NET تتيح لك دمج، تقسيم، تدوير، وتعديل ملفات PDF وغيرها من صيغ المستندات برمجياً.

**س: هل يمكن دمج أكثر من ملفين PDF في آن واحد؟**  
ج: نعم – استدعِ `Join` بشكل متكرر أو مرّر مجموعة من مسارات الملفات لدمج أي عدد من ملفات PDF في عملية واحدة.

**س: كيف أتعامل مع الترخيص للاستخدام الإنتاجي؟**  
ج: احصل على ترخيص دائم من صفحة شراء GroupDocs؛ الترخيص التجريبي يعمل فقط للتقييم وينتهي صلاحيته بعد 30 يوماً.

**س: ملف PDF المدمج لا يظهر أي إشارات مرجعية—ما الخطأ؟**  
ج: تأكد من ضبط `PdfJoinOptions.UseBookmarks` إلى `true` وأن كل ملف PDF مصدر يحتوي فعلاً على إشارات مرجعية قبل الدمج.

**س: هل المكتبة متوافقة مع .NET Core و .NET Framework؟**  
ج: بالتأكيد – تدعم .NET Core 3.1+، .NET 5/6، والإطار الكامل .NET Framework 4.6.1+.

## موارد
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**آخر تحديث:** 2026-08-20  
**تم الاختبار مع:** GroupDocs.Merger 23.11 لـ .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)