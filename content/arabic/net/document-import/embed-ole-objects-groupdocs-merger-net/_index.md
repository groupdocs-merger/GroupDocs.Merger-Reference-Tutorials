---
date: '2026-09-21'
description: تعلم كيفية تضمين PDF في جداول Excel باستخدام GroupDocs.Merger for .NET،
  مما يعزز عرض البيانات والوظائف.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: تعلم كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for .NET.
  اتبع التعليمات خطوة بخطوة، واحصل على إجابات سريعة، وتجنب الأخطاء الشائعة.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for .NET
type: docs
url: /ar/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger لـ .NET

## المقدمة

يتيح لك تضمين PDF في Excel الاحتفاظ بالمستندات الداعمة — مثل العقود، التقارير، أو المواصفات — في نفس المكان الذي توجد فيه البيانات. باستخدام **GroupDocs.Merger for .NET**، يمكنك إضافة كائنات OLE إلى الخلايا ببضع أسطر من الشيفرة فقط، مما يحول جدول البيانات العادي إلى دفتر عمل تفاعلي ومتكامل. يشرح هذا الدليل كل ما تحتاج إلى معرفته، من التثبيت إلى استكشاف الأخطاء وإصلاحها.

**ما ستتعلمه**

- كيفية إعداد GroupDocs.Merger لـ .NET في مشروع C#  
- الخطوات الدقيقة لتضمين PDF (أو أي ملف متوافق مع OLE) في خلية Excel  
- خيارات التكوين، نصائح الأداء، والمشكلات الشائعة  

دعنا نتأكد من أن كل شيء جاهز قبل أن نبدأ.

## إجابات سريعة
- **هل يمكنني تضمين أي نوع ملف؟** نعم — أي تنسيق مدعوم ككائن OLE (PDF، Word، صورة، إلخ).  
- **هل أحتاج إلى ترخيص للتطوير؟** نسخة تجريبية مجانية تكفي للاختبار؛ الترخيص الدائم مطلوب للإنتاج.  
- **ما إصدارات .NET المدعومة؟** .NET Framework 4.5+، .NET Core 3.1+، .NET 5/6/7+.  
- **هل سيزيد حجم ملف Excel بشكل كبير؟** فقط بمقدار حجم المستند المضمّن؛ حافظ على الملفات تحت بضعة ميغابايت لأفضل أداء.  
- **هل هناك حد لعدد كائنات OLE؟** عمليًا لا يوجد حد، لكن دفاتر العمل الكبيرة جدًا قد تؤثر على وقت التحميل.

## ما هو تضمين PDF في Excel؟

يُدرج تضمين PDF في Excel ملف PDF بالكامل ككائن OLE يمكن فتحه مباشرة من جدول البيانات. ينقر المستخدمون على الأيقونة ويعرضون المستند الأصلي دون مغادرة Excel. يحافظ هذا النهج على التخطيط الأصلي، ويسهل الإشارة السريعة، ويقضي على الحاجة لإدارة ملفات منفصلة. يتصرف PDF المضمّن كأي كائن OLE آخر، مما يسمح للمستخدمين بالنقر المزدوج على الأيقونة لتشغيل عارض PDF مع البقاء داخل بيئة Excel.

## لماذا يتم تضمين كائنات OLE في Excel؟

يدعم GroupDocs.Merger **120+** تنسيق إدخال وإخراج ويمكنه تضمين الكائنات دون تحميل الملف بالكامل في الذاكرة، مما يتيح معالجة سريعة لملفات PDF التي تتجاوز مئات الصفحات. يقلل هذا من الحاجة إلى مستودعات ملفات منفصلة ويحافظ على البيانات المرتبطة معًا. كما يبسط التحكم في الإصدارات ويضمن أن جميع الوثائق ذات الصلة تنتقل مع دفتر العمل، مما يحسن التعاون بين الفرق.

## المتطلبات المسبقة

- **GroupDocs.Merger for .NET** (أحدث حزمة NuGet)  
- **.NET Framework** 4.5+ **أو** **.NET Core/5+/6+**  
- Visual Studio 2022 أو أحدث  
- معرفة أساسية بـ C# وإلمام بعمليات I/O للملفات  

## إعداد GroupDocs.Merger لـ .NET

### التثبيت

أضف الحزمة باستخدام إحدى الطرق التالية:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
ابحث عن “GroupDocs.Merger” وقم بتثبيت أحدث نسخة.

### الحصول على الترخيص

1. **نسخة تجريبية مجانية** – اختبر المكتبة دون تكلفة.  
2. **ترخيص مؤقت** – اطلب ترخيصًا مؤقتًا من صفحة [temporary‑license page](https://purchase.groupdocs.com/temporary-license/).  
3. **شراء** – فكر في شراء ترخيص من صفحة [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

### التهيئة الأساسية

`Merger` هو نقطة الدخول لجميع العمليات.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## كيفية تضمين كائنات OLE في Excel؟

يقوم هذا القسم بتحميل دفتر العمل المصدر، تكوين خيارات OLE، والسماح لـ `Merger` بإدراج الكائن. الأقسام التالية تقدم لك سير عمل مختصر وجاهز للتنفيذ.

### نظرة عامة على الميزة
يتيح لك تضمين كائنات OLE تخزين PDF كامل داخل خلية، مع الحفاظ على التخطيط الأصلي وتمكين الوصول بنقرة واحدة من Excel.

### تنفيذ خطوة بخطوة

#### 1. تعيين المسارات ورقم الصفحة
حدد جدول البيانات، الملف المراد تضمينه، وعنوان الخلية الهدف.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. تكوين OleSpreadsheetOptions
`OleSpreadsheetOptions` يحدد مكان وضع كائن OLE في ورقة العمل وكيفية ظهور أيقونته.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. تهيئة Merger وتنفيذ التضمين
تتعامل فئة `Merger` مع عملية الإدراج الفعلية. بعد الاستدعاء، يحتوي دفتر العمل على أيقونة OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### نصائح شائعة لاستكشاف الأخطاء وإصلاحها
- تحقق من أن جميع مسارات الملفات مطلقة أو تم حلها بشكل صحيح بالنسبة للملف التنفيذي.  
- تأكد من أن رقم الصفحة الذي تحدده موجود في PDF المصدر؛ وإلا سيتم رمي استثناء.  
- إذا لم يظهر الكائن المضمّن، تأكد من أن نسخة Excel المستهدفة تدعم OLE (معظم الإصدارات الحديثة تدعم ذلك).

## تطبيقات عملية

يكون تضمين PDF في Excel مفيدًا لـ:

1. **التقارير المالية** – إرفاق القوائم المدققة مباشرة بجوار جداول الملخص.  
2. **توثيق المشاريع** – حفظ مواصفات التصميم، تحليلات المخاطر، أو العقود داخل متعقب رئيسي.  
3. **لوحات التدريب** – تضمين أدلة المستخدم أو سياسات PDF للرجوع السريع من قبل الموظفين.

## اعتبارات الأداء

- **حجم الملف** – حافظ على PDFs المضمنة تحت 5 MB لتجنب تضخم دفتر العمل.  
- **استخدام الذاكرة** – `GroupDocs.Merger` يبث البيانات، لذا يبقى استهلاك الذاكرة منخفضًا حتى مع ملفات مصدر كبيرة.  
- **إتلاف الكائنات** – استدعِ دائمًا `Dispose()` على مثيلات `Merger` لتحرير مقابض الملفات بسرعة.

## الأسئلة المتكررة

**س: ما هو كائن OLE؟**  
ج: كائن OLE (Object Linking and Embedding) يخزن ملفًا آخر (PDF، Word، صورة، إلخ) داخل مستند مضيف، مما يسمح بالتحرير داخل المكان أو الفتح.

**س: هل يمكنني تضمين كائنات OLE في صيغ Office أخرى؟**  
ج: نعم — يدعم GroupDocs.Merger أيضًا ملفات Word وPowerPoint وVisio.

**س: كيف أتعامل مع ملفات PDF محمية بكلمة مرور؟**  
ج: قدم كلمة المرور عند إنشاء مثيل `OleSpreadsheetOptions`؛ ستقوم المكتبة بفك تشفير الملف تلقائيًا.

**س: هل هناك حد لحجم PDFs المضمنة؟**  
ج: تقنيًا لا يوجد حد ثابت، لكن الملفات التي تتجاوز 10 MB قد تزيد بشكل ملحوظ من وقت تحميل دفتر العمل.

**س: أين يمكنني العثور على المزيد من الأمثلة؟**  
ج: زر الوثائق الرسمية لـ [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) للحصول على عينات شيفرة إضافية ومراجع API.

## موارد إضافية
- **الوثائق**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **مرجع API**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **التنزيلات**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **شراء الترخيص**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **نسخة تجريبية مجانية**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **ترخيص مؤقت**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **منتدى الدعم**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**آخر تحديث:** 2026-09-21  
**تم الاختبار مع:** GroupDocs.Merger 23.12 for .NET  
**المؤلف:** GroupDocs

## الدروس ذات الصلة

- [Embed PDF as OLE in PowerPoint using GroupDocs.Merger for .NET&#58; A Step-by-Step Guide](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)  
- [Embed PDF in Word Using GroupDocs.Merger for .NET&#58; A Step-by-Step Guide](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)  
- [Loading PDF from URL in .NET Using GroupDocs.Merger&#58; A Comprehensive Guide](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}