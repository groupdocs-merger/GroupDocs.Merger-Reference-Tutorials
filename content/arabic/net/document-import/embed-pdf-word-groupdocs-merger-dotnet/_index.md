---
date: '2026-10-01'
description: تعلم كيفية إدراج PDF في Word باستخدام GroupDocs.Merger for .NET. اتبع
  هذا الدليل لإضافة ملفات PDF ككائنات OLE، وتعزيز تفاعل المستند، والحفاظ على تنسيقات
  الصفحات.
keywords:
- embed pdf in word
- add pdf to word
- ole object embedding
- insert ole object word
lastmod: '2026-10-01'
og_description: إدراج PDF في Word باستخدام GroupDocs.Merger for .NET. يشرح هذا البرنامج
  التعليمي كيفية إضافة ملفات PDF ككائنات OLE، ويغطي الإعداد، والرمز، وأفضل الممارسات.
og_image_alt: Guide showing how to embed a PDF into a Word document using GroupDocs.Merger
  for .NET
og_title: إدراج PDF في Word مع GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to embed pdf in word with GroupDocs.Merger for .NET. Follow
    this guide to add PDF files as OLE objects, boost document interactivity, and
    keep layouts intact.
  headline: 'Embed PDF in Word Using GroupDocs.Merger for .NET: A Step-by-Step Guide'
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Merger supports various file types. Check [documentation](https://docs.groupdocs.com/merger/net/)
      for the full list.
    question: Can I embed other file formats besides PDF?
  - answer: Use memory‑efficient practices such as processing in chunks and handling
      exceptions effectively.
    question: How do I handle large documents efficiently with GroupDocs.Merger?
  - answer: Absolutely, you can obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
    question: Is there a way to trial this library before purchasing?
  - answer: Ensure compatibility with .NET Core 3.1 or higher.
    question: What are the system requirements for using GroupDocs.Merger on .NET
      Core?
  - answer: Visit [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)
      for assistance.
    question: Where can I find support if I encounter issues?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET document processing
- OLE embedding
- PDF to Word
title: 'إدراج PDF في Word باستخدام GroupDocs.Merger for .NET: دليل خطوة بخطوة'
type: docs
url: /ar/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/
weight: 1
---

# إدراج PDF في Word باستخدام GroupDocs.Merger لـ .NET: دليل خطوة بخطوة

إدراج PDF داخل ملف Word يتيح لك الحفاظ على التنسيق الأصلي مع إعطاء القراء وصولًا فوريًا إلى المستند الأصلي. في هذا الدرس ستتعلم كيفية **إدراج PDF في Word** عن طريق إدراج كائن OLE (Object Linking and Embedding) باستخدام GroupDocs.Merger لـ .NET. سنغطي كل شيء من تثبيت المكتبة إلى الكود الدقيق الذي تحتاجه، بالإضافة إلى نصائح استكشاف الأخطاء وحالات الاستخدام الواقعية.

## إجابات سريعة
- **ما هي أبسط طريقة لإدراج PDF؟** Use `Merger.ImportDocument` with `OleWordProcessingOptions`.
- **أي مكتبة تدعم ذلك؟** GroupDocs.Merger for .NET.
- **هل أحتاج إلى ترخيص؟** ترخيص مؤقت يعمل للتقييم؛ الترخيص الكامل مطلوب للإنتاج.
- **هل يمكنني إضافة أنواع ملفات أخرى؟** نعم – الطريقة نفسها تعمل مع DOCX و XLSX و PPTX والمزيد.
- **هل هو متوافق مع .NET Core؟** مدعوم بالكامل على .NET Core 3.1+ و .NET 5/6/7.

## ما هو إدراج PDF في Word؟
إدراج PDF في Word يعني إدراج ملف PDF ككائن OLE بحيث يظهر الملف كأيقونة أو معاينة داخل المستند بينما يبقى ملف PDF الأصلي دون تغيير. هذه الطريقة تحافظ على التخطيط الدقيق والخطوط والرسومات للمصدر PDF، مما يسمح للقراء بفتح الملف المضمن مباشرةً من مستند Word للرجوع إليه أو تحريره لاحقًا.

## لماذا نستخدم إدراج كائن OLE مع GroupDocs.Merger؟
GroupDocs.Merger يدعم **أكثر من 70 تنسيقًا للإدخال والإخراج** ويمكنه معالجة ملفات تصل إلى **500 ميغابايت** دون تحميل المستند بالكامل في الذاكرة، مما يمنحك عمليات سريعة وفعّالة في استهلاك الذاكرة لأعباء العمل الكبيرة في المؤسسات. استخدام إدراج OLE يتيح لك الحفاظ على PDF الأصلي دون تعديل، ويوفر أيقونة قابلة للنقر للوصول السريع، ويضمن أن المحتوى المضمن قابل للنقل عبر مختلف الأجهزة والمنصات.

## المقدمة
هل تواجه صعوبة في تحسين مستندات Word الخاصة بك عن طريق إدراج محتوى غني مثل ملفات PDF؟ يوجهك هذا الدرس عبر عملية إدراج كائن OLE (Object Linking and Embedding)، مثل PDF، في صفحة محددة من مستند Microsoft Word باستخدام GroupDocs.Merger لـ .NET. يمكن أن يثري إدراج الكائنات مستنداتك بمحتوى ديناميكي أو خارجي يحافظ على التفاعلية. سواءً كنت تُعد تقارير تتطلب مجموعات بيانات مدمجة أو عروضًا تقديمية تحتاج إلى ملفات إضافية، فإن هذه الميزة تُبسّط العملية.

### ما ستتعلمه
- كيفية إعداد واستخدام GroupDocs.Merger لـ .NET
- دليل خطوة بخطوة حول إدراج كائنات OLE في مستندات Word
- خيارات التكوين الرئيسية ونصائح استكشاف الأخطاء

## المتطلبات المسبقة
قبل تنفيذ هذه الميزة، تأكد من أن بيئة التطوير جاهزة مع المكتبات والإعدادات اللازمة:

### المكتبات المطلوبة
- **GroupDocs.Merger for .NET** – مكتبة قوية لمعالجة صيغ المستندات.  
- **.NET Framework** أو **.NET Core/5+** – أي نسخة حديثة مدعومة.

### إعداد البيئة
- Visual Studio (2017 أو أحدث) مع دعم C#  
- فهم أساسي للتعامل مع الملفات وت Manipulation الكائنات في .NET  

### المتطلبات المعرفية
- الإلمام بلغة البرمجة C#  
- فهم كيفية العمل مع المكتبات الخارجية في .NET  

## إعداد GroupDocs.Merger لـ .NET
للبدء، تحتاج إلى تثبيت GroupDocs.Merger. إليك الخطوات:

### التثبيت

**Using .NET CLI:**  
```bash
dotnet add package GroupDocs.Merger
```  

**Using Package Manager Console:**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI:**  
ابحث عن "GroupDocs.Merger" وقم بتثبيت أحدث نسخة.

### الحصول على الترخيص
To use GroupDocs.Merger, you can acquire a license through:
- **Free trial** – ابدأ بترخيص مؤقت لتقييم الميزات.  
- **Temporary license** – احصل عليه من [هنا](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase** – اشترِ ترخيصًا كاملًا للاستخدام الإنتاجي عبر [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

### التهيئة الأساسية
After installation, import the library in your C# project:  
```csharp
using GroupDocs.Merger;
```  

## دليل التنفيذ
الآن بعد أن تم إعداد كل شيء، دعنا ننفذ الميزة لإدراج كائن OLE.

### كيفية إدراج PDF في Word باستخدام GroupDocs.Merger لـ .NET؟
حمّل ملف Word المصدر باستخدام `new Merger("source.docx")`، وقم بتكوين `OleWordProcessingOptions` لتحديد مسار PDF، الأبعاد، وموقع الصفحة، ثم استدعِ `ImportDocument` و `Save`. هذه العملية المكوّنة من ثلاث خطوات تُدرج PDF ككائن OLE في سطر واحد من الكود وتكتب النتيجة إلى مسار الإخراج.

#### استيراد كائن OLE إلى مستند Word
فئة `Merger` هي المحرك الأساسي لـ GroupDocs.Merger لمعالجة المستندات. توفر طرقًا للدمج، والتقسيم، واستيراد الملفات الخارجية ككائنات OLE.

##### الخطوة 1: إعداد مسارات الملفات وتهيئة الخيارات
OleWordProcessingOptions يحدد إعدادات كائن OLE مثل مسار الملف، حجم الأيقونة، وموقع الإدراج. عرّف مسارات مستند Word المصدر، وPDF الذي تريد إدراجه، وملف الإخراج. ثم أنشئ مثيلًا من `OleWordProcessingOptions` لتعيين حجم الأيقونة ورقم الصفحة.

```csharp
string sourceFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.docx");
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "embedded.pdf");
string outputFilePath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "output_sample.docx");

int pageNumberToEmbed = 2; // Page number for the OLE object
OleWordProcessingOptions oleOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumberToEmbed)
{
    Width = 300, // Set width in points
    Height = 300 // Set height in points
};
```  

##### الخطوة 2: دمج وحفظ المستند
أنشئ مثيلًا من فئة `Merger` باستخدام ملف المصدر الخاص بك. استخدم طريقة `ImportDocument` لإضافة كائن OLE وحفظ المستند.

```csharp
using (Merger merger = new Merger(sourceFilePath))
{
    merger.ImportDocument(oleOptions);
    merger.Save(outputFilePath); // Save the output document with embedded content
}
```  

### المعلمات والطرق
- **ImportDocument** – يضيف ملفًا خارجيًا ككائن OLE.  
- **Save** – يكتب التغييرات إلى مسار محدد.  

## التطبيقات العملية
Embedding OLE objects can be incredibly useful in various scenarios:
1. **تقارير الأعمال** – إدراج مجموعات البيانات المالية للرجوع السريع.  
2. **الوثائق التقنية** – تضمين مخططات أو رسومات تفصيلية مباشرةً في المستند.  
3. **المواد التعليمية** – إدراج قراءات إضافية، اختبارات، أو تعليمات مختبرية دون مغادرة المستند الرئيسي.

## اعتبارات الأداء
To keep your application responsive when using GroupDocs.Merger:
- قلل حجم الملفات عن طريق إدراج الكائنات الضرورية فقط.  
- تعامل مع الاستثناءات برشاقة لتجنب الأعطال أثناء معالجة المستند.  
- إدارة الذاكرة والموارد بفعالية، خاصةً في التطبيقات ذات النطاق الواسع.  

## الخلاصة
لقد تعلمت كيفية إدراج كائنات OLE بسلاسة في مستندات Word باستخدام GroupDocs.Merger لـ .NET. هذه القدرة يمكن أن تعزز مستنداتك بشكل كبير من خلال دمج أنواع مختلفة من المحتوى مباشرةً داخلها.

### الخطوات التالية
استكشف الميزات الإضافية التي يقدمها GroupDocs.Merger مثل تقسيم المستندات، الدمج، أو تدوير الصفحات للاستفادة الكاملة من هذه المكتبة القوية في مشاريعك.

## الأسئلة المتكررة
**س: هل يمكنني إدراج صيغ ملفات أخرى غير PDF؟**  
ج: نعم، يدعم GroupDocs.Merger صيغ ملفات متعددة. راجع [documentation](https://docs.groupdocs.com/merger/net/) للقائمة الكاملة.

**س: كيف يمكنني التعامل مع المستندات الكبيرة بكفاءة باستخدام GroupDocs.Merger؟**  
ج: استخدم ممارسات فعّالة في استهلاك الذاكرة مثل المعالجة على أجزاء ومعالجة الاستثناءات بفعالية.

**س: هل هناك طريقة لتجربة هذه المكتبة قبل الشراء؟**  
ج: بالتأكيد، يمكنك الحصول على ترخيص مؤقت [هنا](https://purchase.groupdocs.com/temporary-license/).

**س: ما هي متطلبات النظام لاستخدام GroupDocs.Merger على .NET Core؟**  
ج: تأكد من التوافق مع .NET Core 3.1 أو أعلى.

**س: أين يمكنني العثور على الدعم إذا واجهت مشكلات؟**  
ج: زر [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger) للحصول على المساعدة.

## الموارد
- **الوثائق**: [GroupDocs.Merger Docs](https://docs.groupdocs.com/merger/net/)  
- **مرجع API**: [GroupDocs API Ref](https://reference.groupdocs.com/merger/net/)  
- **تحميل GroupDocs.Merger**: [Latest Release](https://releases.groupdocs.com/merger/net/)  
- **شراء الترخيص**: [Buy Now](https://purchase.groupdocs.com/buy)  
- **تجربة مجانية**: [Try It](https://releases.groupdocs.com/merger/net/)  
- **ترخيص مؤقت**: [Acquire Temporary Access](https://purchase.groupdocs.com/temporary-license/)  
- **رابط ترخيص مؤقت إضافي**: [هنا](https://purchase.groupdocs.com/temporary-license/)  
- **دعم ومنتدى المجتمع**: [GroupDocs Forum](https://forum.groupdocs.com/c/merger)

---

**آخر تحديث:** 2026-10-01  
**تم الاختبار مع:** GroupDocs.Merger 24.2 for .NET  
**المؤلف:** GroupDocs

## دروس ذات صلة
- [إدراج كائنات Ole Groupdocs Merger Net](/merger/net/document-import/embed-ole-objects-groupdocs-merger-net/)
- [إدراج PDF OLE Powerpoint Groupdocs Merger Net](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [إضافة مرفقات PDF Groupdocs Merger Dotnet Tutorial](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)