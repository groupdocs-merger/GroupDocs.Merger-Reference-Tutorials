---
date: '2026-09-21'
description: تعلم كيفية تضمين pdf في powerpoint ككائن OLE باستخدام GroupDocs.Merger
  for .NET. يوضح هذا الدليل خطوة بخطوة استدعاءات API الدقيقة وأفضل الممارسات.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: تضمين pdf في powerpoint باستخدام GroupDocs.Merger for .NET. اتبع هذا
  البرنامج التعليمي المختصر لإضافة كائنات OLE، وتكوين الخيارات، وتجنب الأخطاء الشائعة.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: تضمين pdf في powerpoint – تضمين PDF كـ OLE مع GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: كيفية تضمين pdf في powerpoint ككائن OLE باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# إدراج ملف PDF في PowerPoint كـ OLE باستخدام GroupDocs.Merger لـ .NET

Embedding a PDF directly into a PowerPoint slide lets you keep the original document intact while giving your audience instant access. In this tutorial you’ll learn **how to embed pdf in powerpoint** as an OLE object with GroupDocs.Merger for .NET, see the required API options, and discover tips for reliable performance.

## إجابات سريعة
- **أي مكتبة تتعامل مع تضمين OLE؟** GroupDocs.Merger for .NET provides the `OlePresentationOptions` class for this purpose.  
- **هل أحتاج إلى ترخيص؟** A trial license works for development; a full license is required for production use.  
- **هل يمكنني تضمين أكثر من PDF واحد؟** Yes – repeat the import step for each slide you target.  
- **ما إصدارات .NET المدعومة؟** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **هل العملية فعّالة في استهلاك الذاكرة؟** The API streams files, so even multi‑hundred‑page PDFs can be embedded without loading the whole file into memory.

## ما هو embed pdf in powerpoint؟
**embed pdf in powerpoint** يعني إدراج ملف PDF ككائن OLE (Object Linking and Embedding) بحيث تُظهر الشريحة أيقونة أو معاينة، وعند النقر المزدوج تُفتح نسخة PDF الأصلية في العارض الافتراضي. هذه الطريقة تحافظ على التنسيق والروابط التشعبية وإعدادات الأمان في المستند الأصلي.

## لماذا نستخدم تضمين OLE بدلاً من تحويل PDF؟
يُحافظ التضمين على حجم الملف الأصلي وتنسيقه كما هو، ويقضي على أخطاء التحويل، ويسمح لك بتحديث ملف PDF المصدر دون الحاجة إلى إعادة تصدير العرض التقديمي. يدعم GroupDocs.Merger **50+ تنسيقات إدخال وإخراج** ويمكنه تضمين ملفات PDF تصل إلى عدة مئات من الميجابايت مع تدفق البيانات للحفاظ على استهلاك الذاكرة أقل من 100 ميغابايت.

## المتطلبات المسبقة
- Visual Studio 2022 (أو أي بيئة تطوير متوافقة مع .NET)  
- .NET Framework 4.5+ أو .NET Core 3.1+ runtime  
- ترخيص صالح لـ GroupDocs.Merger for .NET (تجريبي أو تجاري)  
- ملف PowerPoint (.pptx) وملف PDF الذي تريد تضمينه  

## إعداد GroupDocs.Merger لـ .NET

### كيف أقوم بتثبيت المكتبة؟
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – ابحث عن “GroupDocs.Merger” وانقر **Install** للحصول على أحدث نسخة.

### كيف أحصل على ترخيص؟
- **Free trial** – سجّل على موقع GroupDocs للحصول على مفتاح ترخيص مؤقت.  
- **Temporary license** – اطلب تجربة موسعة إذا كنت تحتاج أكثر من 30 يوم.  
- **Full purchase** – اشترِ ترخيصًا تجاريًا لاستخدام غير محدود في الإنتاج.

### كيف أقوم بتهيئة الـ API؟
`Merger` هي الفئة الأساسية التي توفر عمليات معالجة المستندات مثل الاستيراد والدمج والتحويل.  
أضف توجيهات `using` المطلوبة في أعلى ملف C# الخاص بك وأنشئ مثيلًا من `Merger` مع مسار ملف الترخيص:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## دليل التنفيذ

### كيف أدمج pdf في powerpoint كـ OLE؟
حمّل العرض التقديمي الخاص بك، واضبط خيارات OLE، واستدعِ طريقة الاستيراد – تُنجز العملية بالكامل في ثلاث خطوات منطقية.

**Step 1 – define file locations**  
حدد المسارات المطلقة أو النسبية لملف PDF المصدر، وملف PowerPoint الهدف، والمجلد الذي سيُحفظ فيه العرض التقديمي المعدل.

**Step 2 – configure the OLE options**  
`OlePresentationOptions` هي الفئة التي تخبر GroupDocs.Merger أي ملف سيتم تضمينه، وعلى أي شريحة، وفي أي إحداثيات. كما تسمح لك بتحديد العرض والارتفاع ووضع العرض للكائن المدمج.

**Step 3 – import the PDF**  
`ImportDocument` هي استدعاء API في Merger الذي يدرج كائن OLE في ملف PowerPoint باستخدام الخيارات المقدمة. تقوم الطريقة بتدفق PDF إلى الشريحة دون تحميل المستند بالكامل في الذاكرة.

#### تعريف الروابط
- `OlePresentationOptions` هو حاوية الخيارات التي تحدد الملف المدمج، موقعه (X/Y)، حجمه، ورقم الشريحة المستهدفة.  
- `ImportDocument` هو استدعاء API في Merger الذي يدرج كائن OLE في ملف PowerPoint باستخدام الخيارات المقدمة.

## معلمات التكوين الشائعة
- **SlideNumber** – الفهرس القائم على 1 للشريحة التي ستستضيف كائن OLE.  
- **XCoordinate / YCoordinate** – الموقع مقاسًا بالنقاط من الزاوية العلوية اليسرى للشريحة.  
- **Width / Height** – أبعاد العنصر النائب OLE؛ اضبطها على 0 لاستخدام الحجم الافتراضي.  
- **ObjectName** – اسم صديق اختياري يُظهر عند تحديد الكائن في PowerPoint.

## التطبيقات العملية
يبرز تضمين PDF ككائن OLE في العديد من السيناريوهات الواقعية:
1. **Corporate briefings** – أرفق أحدث التقرير المالي دون زيادة حجم العرض.  
2. **Academic lectures** – قدّم أوراق بحثية كاملة النص إلى جانب ملخصات الشرائح.  
3. **Project status updates** – دمج خطة مشروع حية يمكن لأصحاب المصلحة فتحها للحصول على التفاصيل.  
4. **Sales decks** – تضمين أوراق مواصفات المنتج التي يمكن لمندوبي المبيعات فتحها عند الطلب.  
5. **Technical workshops** – عرض المخططات أو أوراق البيانات التي يمكن للمهندسين فحصها فورًا.

## اعتبارات الأداء
للحفاظ على سرعة عملية التضمين وصداقة الذاكرة:
- **Stream files** – يقرأ ويكتب GroupDocs.Merger البيانات على شكل تدفقات، لذا حتى ملف PDF من 200 صفحة يستخدم أقل من 100 ميغابايت من الذاكرة.  
- **Batch process** – عند تحديث العديد من العروض، أعد استخدام مثيل واحد من `Merger` وأغلق التدفقات فورًا.  
- **Resize large PDFs** – ضغط أو تقليل عينات الصور في ملف PDF المصدر إذا لاحظت بطء في أوقات التحميل.

## الأسئلة المتكررة
**Q: هل يمكنني تضمين عدة ملفات PDF في عرض تقديمي واحد؟**  
A: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber` or position on the same slide.

**Q: ما هو الحد الأقصى لحجم PDF الذي يمكنني تضمينه؟**  
A: The practical limit is dictated by your server’s memory; embeddings of up to 500 MB have been tested without issues when streaming.

**Q: هل يحتفظ كائن OLE بالعناصر التفاعلية مثل الروابط التشعبية؟**  
A: Absolutely. The embedded PDF opens in the default viewer, preserving all internal links and bookmarks.

**Q: ماذا لو كان PDF محميًا بكلمة مرور؟**  
A: Provide the password via the `Password` property of `OlePresentationOptions` before calling `ImportDocument`.

**Q: هل سيعمل الكائن المدمج على جميع إصدارات PowerPoint؟**  
A: The OLE format is supported by PowerPoint 2007 and later, including Office 365.

## الخلاصة
أنت الآن تمتلك سير عمل كامل وجاهز للإنتاج لـ **embed pdf in powerpoint** ككائن OLE باستخدام GroupDocs.Merger لـ .NET. من خلال تدفق الملفات، وضبط `OlePresentationOptions`، واستدعاء `ImportDocument`، يمكنك إثراء العروض التقديمية بملفات PDF الأصلية مع الحفاظ على استهلاك منخفض للذاكرة وحفظ جميع الميزات التفاعلية. استكشف قدرات Merger الإضافية مثل دمج الشرائح، تحويل الصيغ، وإضافة العلامات المائية لمزيد من أتمتة خطوط أنابيب المستندات.

---

**آخر تحديث:** 2026-09-21  
**تم الاختبار مع:** GroupDocs.Merger 23.12 for .NET  
**المؤلف:** GroupDocs  

## الموارد
- **التوثيق:** [GroupDocs.Merger for .NET Documentation](https://docs.groupdocs.com/merger/net/)  
- **مرجع API:** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **تحميل:** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **شراء:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **تجربة مجانية:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **ترخيص مؤقت:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## دروس ذات صلة
- [إدراج PDF في Word باستخدام GroupDocs.Merger لـ .NET: دليل خطوة بخطوة](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [تحميل PDF من URL في .NET باستخدام GroupDocs.Merger: دليل شامل](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [كيفية استرجاع معلومات المستند باستخدام GroupDocs.Merger لـ .NET: دليل شامل](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)