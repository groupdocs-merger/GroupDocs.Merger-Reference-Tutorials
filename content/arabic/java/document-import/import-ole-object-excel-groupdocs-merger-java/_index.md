---
date: '2026-10-06'
description: تعرف على كيفية تضمين PDF في Excel واستيراد مستند إلى Excel باستخدام GroupDocs.Merger
  for Java. اتبع هذا الدليل التفصيلي مع أمثلة code ونصائح troubleshooting.
keywords:
- how to embed pdf excel
- GroupDocs Merger Java OLE
- embed PDF in Excel Java
lastmod: '2026-10-06'
og_description: تعرف على كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for Java.
  يوضح هذا الدليل code خطوة بخطوة، المتطلبات المسبقة، ونصائح لاستيراد كائن OLE بنجاح.
og_image_alt: Illustration of embedding a PDF as an OLE object in an Excel worksheet
  using Java
og_title: كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-06'
  description: Learn how to embed PDF in Excel and import a document into Excel with
    GroupDocs.Merger for Java. Follow this detailed guide with code examples and troubleshooting
    tips.
  headline: How to embed PDF in Excel using GroupDocs.Merger for Java – a step‑by‑step
    guide
  type: TechArticle
- description: Learn how to embed PDF in Excel and import a document into Excel with
    GroupDocs.Merger for Java. Follow this detailed guide with code examples and troubleshooting
    tips.
  name: How to embed PDF in Excel using GroupDocs.Merger for Java – a step‑by‑step
    guide
  steps:
  - name: define file paths and initialize objects
    text: First, set up the paths for your Excel workbook, the PDF you want to embed,
      and the output file. Then create the `OleSpreadsheetOptions` that describe where
      the OLE object will appear. **Definition anchor:** `OleSpreadsheetOptions` configures
      the target cell, size, and display properties of an OLE o
  - name: import the OLE document
    text: Use the `importDocument` method to embed the PDF as an OLE object at the
      location you defined. **Definition anchor:** `importDocument` tells GroupDocs.Merger
      to treat the supplied file as an OLE object, preserving its original binary
      content while linking it to the worksheet. **Why we use `importDoc
  - name: save the spreadsheet
    text: Persist the changes to a new file so you keep the original workbook untouched.
      **Key configuration options:** You can further tweak `OleSpreadsheetOptions`—for
      example, adjusting the object's size, visibility, or whether it should be linked
      rather than embedded.
  type: HowTo
- questions:
  - answer: Yes, repeat the `importDocument` call for each object, adjusting the `OleSpreadsheetOptions`
      to target different cells.
    question: Can I embed multiple OLE objects in a single Excel file?
  - answer: GroupDocs.Merger supports PDFs, Word documents, Excel files, images, and
      several other common formats—over **30+** types in total.
    question: What file formats are supported as OLE objects?
  - answer: Process files in smaller batches, use streaming APIs, and dispose of `Merger`
      instances promptly to keep memory usage low.
    question: How do I handle large files efficiently with GroupDocs.Merger?
  - answer: Verify the source file’s path and integrity before attempting to embed
      it. A corrupted file will raise an exception during import.
    question: What if the embedded file is not accessible or is corrupted?
  - answer: Yes, `OleSpreadsheetOptions` lets you set row/column indices, size, and
      visibility to tailor how the object looks in the worksheet.
    question: Can I customize the appearance of OLE objects in Excel?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- Java OLE object
- Excel integration
title: كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger for Java – دليل خطوة بخطوة
type: docs
url: /ar/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger للـ Java

يمكن أن يتحول تضمين ملف PDF في Excel إلى تحويل جدول بيانات ثابت إلى تقرير غني وتفاعلي يحتوي على المستند الأصلي بالكامل حيث تحتاجه. في هذا البرنامج التعليمي ستتعلم **كيفية تضمين PDF في Excel** عن طريق استيراد ملف PDF ككائن OLE (ربط وتضمين الكائنات) باستخدام GroupDocs.Merger للـ Java. سنستعرض جميع المتطلبات المسبقة، نعرض لك الشيفرة الدقيقة، ونقدم لك نصائح عملية حتى تتمكن من بدء استخدام هذه التقنية في مشاريعك اليوم.

## إجابات سريعة
- **ماذا يعني “embed PDF in Excel”؟** يعني إدراج ملف PDF ككائن OLE بحيث يمكن فتح PDF مباشرة من جدول البيانات.  
- **أي مكتبة تتعامل مع الاستيراد؟** توفر GroupDocs.Merger للـ Java طريقة `importDocument` لهذا الغرض.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ يلزم ترخيص تجاري للاستخدام في الإنتاج.  
- **هل يمكنني تضمين أنواع ملفات أخرى؟** نعم – يمكن استيراد ملفات Word، الصور، وغيرها من الصيغ المدعومة ككائنات OLE.  
- **هل هذا النهج متوافق مع Java 8+؟** بالتأكيد – المكتبة تدعم Java 8 والإصدارات الأحدث.

## ما هو تضمين PDF في Excel؟
يخزن تضمين PDF في Excel ملف PDF داخل المصنف ككائن OLE، مما يسمح للمستخدمين بالنقر المزدوج على الأيقونة وفتح PDF الأصلي دون مغادرة جدول البيانات. هذه التقنية مثالية لسجلات التدقيق، التقارير المفصلة، أو أي سيناريو تحتاج فيه إلى ربط المستند الأصلي ارتباطًا وثيقًا ببيانات الملخص.

## لماذا نضمّن PDF في Excel باستخدام GroupDocs.Merger؟
يُزيل تضمين ملفات PDF باستخدام GroupDocs.Merger الحاجة إلى النسخ واللصق اليدوي ويضمن وضعًا ثابتًا عبر آلاف المصنفات. تدعم المكتبة **أكثر من 30 صيغة إدخال وإخراج** ويمكنها معالجة مصنفات يصل حجمها إلى **500 ميغابايت** دون تحميل الملف بالكامل في الذاكرة، مما يوفر أتمتة سريعة وفعّالة في استهلاك الذاكرة لخطوط أنابيب التقارير على نطاق واسع.

## كيفية تضمين PDF في Excel – المتطلبات المسبقة
قبل أن تبدأ بالبرمجة، تأكد من أن بيئة التطوير الخاصة بك تلبي الشروط التالية. يجب أن يكون لديك JDK متوافق مثبتًا، ومكتبة GroupDocs.Merger مضافة إلى مشروعك، وبيئة تطوير متكاملة (IDE) جاهزة للتحرير والتنفيذ. سيساعدك الإلمام بمعالجة ملفات Java على متابعة الأمثلة بسلاسة.

- Java Development Kit (JDK) 8 أو أعلى، مثبت ومضاف إلى `PATH` الخاص بك.
- GroupDocs.Merger للـ Java – أضفه إلى مشروعك عبر Maven أو Gradle (انظر الأقسام أدناه).
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse لتحرير وتشغيل الشيفرة.
- إلمام أساسي بمعالجة ملفات Java وتدفقات البيانات.

## إعداد GroupDocs.Merger للـ Java

### Maven
أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
قم بإدراج المكتبة في ملف `build.gradle` الخاص بك:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

يمكنك أيضًا تنزيل أحدث نسخة مباشرة من [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/).

#### خطوات الحصول على الترخيص
1. **نسخة تجريبية مجانية:** ابدأ بنسخة تجريبية مجانية لاستكشاف جميع الميزات.  
2. **ترخيص مؤقت:** اطلب ترخيصًا مؤقتًا للاختبار الموسع.  
3. **شراء:** احصل على ترخيص كامل للنشر التجاري.

## تنفيذ خطوة بخطوة

### الخطوة 1: تعريف مسارات الملفات وتهيئة الكائنات
أولاً، قم بإعداد المسارات لملف Excel الخاص بك، وملف PDF الذي تريد تضمينه، وملف الإخراج. ثم أنشئ `OleSpreadsheetOptions` التي تحدد موقع ظهور كائن OLE.

**مرساة التعريف:** `OleSpreadsheetOptions` تُكوّن الخلية المستهدفة، الحجم، وخصائص العرض لكائن OLE داخل ورقة Excel.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleSpreadsheetOptions;

public class ImportOLEToSpreadsheet {
    public static void main(String[] args) throws Exception {
        // Define the paths for input and output files.
        String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";  // Excel file path
        String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf";  // PDF file to embed

        // Specify the output file path.
        String filePathOut = "YOUR_OUTPUT_DIRECTORY/ImportDocumentToSpreadsheet-output.xlsx";

        // Specify the page number of the OLE object and its position in the spreadsheet.
        int pageNumber = 2;  
        OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber);
        
        // Set the desired row and column indices for the OLE object placement.
        oleCellsOptions.setRowIndex(2); 
        oleCellsOptions.setColumnIndex(2);

        // Create a Merger instance for the target Excel file.
        Merger merger = new Merger(filePath);
    }
}
```

### الخطوة 2: استيراد مستند OLE
استخدم طريقة `importDocument` لتضمين PDF ككائن OLE في الموقع الذي حددته.

**مرساة التعريف:** `importDocument` تُخبر GroupDocs.Merger بمعاملة الملف المقدم ككائن OLE، مع الحفاظ على محتواه الثنائي الأصلي وربطه بورقة العمل.

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**لماذا نستخدم `importDocument`:** تضمن هذه الطريقة أن يظل PDF عمليًا بالكامل عند فتحه من Excel، حيث تتعامل تلقائيًا مع حزم البيانات الثنائية والبيانات الوصفية للعلاقات اللازمة.

### الخطوة 3: حفظ جدول البيانات
احفظ التغييرات في ملف جديد لتبقى المصنف الأصلي دون تعديل.

```java
merger.save(filePathOut);
```

**خيارات التكوين الرئيسية:** يمكنك تعديل `OleSpreadsheetOptions` أكثر—مثل ضبط حجم الكائن، رؤيته، أو ما إذا كان يجب ربطه بدلاً من تضمينه.

## المشكلات الشائعة ونصائح استكشاف الأخطاء
- **FileNotFoundException:** تحقق مرة أخرى من أن المسارات التي قدمتها تشير إلى ملفات موجودة.  
- **عدم توافق الإصدارات:** تأكد من أن إصدار GroupDocs.Merger الذي تستخدمه يتطابق مع إصدار JDK الخاص بك.  
- **PDF معطوب:** تحقق من أن PDF يفتح بشكل مستقل قبل تضمينه.  
- **ضغط الذاكرة:** عند معالجة العديد من المصنفات، أغلق كل نسخة من `Merger` فورًا أو استخدم try‑with‑resources لتحرير الموارد.

## تطبيقات عملية
تضمين كائنات OLE في Excel مفيد في العديد من السيناريوهات:
1. **دمج البيانات:** دمج ملفات PDF ربع السنوية في مصنف لوحة تحكم واحد.  
2. **عروض تقديمية تفاعلية:** توفير أوراق مواصفات مفصلة تُفتح عند الطلب خلال الاجتماع.  
3. **تقارير آلية:** إنشاء بيانات مالية شهرية تتضمن تلقائيًا الوثائق الداعمة.

## اعتبارات الأداء
- **إدارة الذاكرة:** أغلق أي نسخة من `Merger` لم تعد بحاجة إليها لتحرير الموارد.  
- **المعالجة الدفعية:** عند التعامل مع العشرات من جداول البيانات، عالجها على دفعات صغيرة لتجنب ارتفاع استهلاك الذاكرة.  
- **أفضل ممارسات Java:** استخدم try‑with‑resources للتدفقات وتعامل مع الاستثناءات برشاقة.

## الخلاصة
أصبح لديك الآن حل كامل وجاهز للإنتاج **لتضمين PDF في Excel** و**استيراد مستند إلى Excel** باستخدام GroupDocs.Merger للـ Java. جرب أنواع ملفات مختلفة، عدّل خيارات الموضع، ودمج هذا سير العمل في خطوط أنابيب التقارير الآلية الخاصة بك.

### الخطوات التالية
- جرّب تضمين مستند Word أو صورة لترى كيف يتعامل API مع الصيغ الأخرى.  
- استكشف قدرات إضافية في GroupDocs.Merger مثل التقسيم، الدمج، أو تحويل المستندات.

## الأسئلة المتكررة

**س: هل يمكنني تضمين عدة كائنات OLE في ملف Excel واحد؟**  
ج: نعم، كرّر استدعاء `importDocument` لكل كائن، مع تعديل `OleSpreadsheetOptions` لاستهداف خلايا مختلفة.

**س: ما هي صيغ الملفات المدعومة ككائنات OLE؟**  
ج: تدعم GroupDocs.Merger ملفات PDF، مستندات Word، ملفات Excel، الصور، والعديد من الصيغ الشائعة الأخرى—أكثر من **30+** نوعًا إجمالًا.

**س: كيف يمكنني معالجة الملفات الكبيرة بكفاءة باستخدام GroupDocs.Merger؟**  
ج: عالج الملفات على دفعات أصغر، استخدم واجهات برمجة التطبيقات المتدفقة (streaming APIs)، وتخلص من نسخ `Merger` فورًا للحفاظ على انخفاض استهلاك الذاكرة.

**س: ماذا لو كان الملف المضمّن غير قابل للوصول أو معطوب؟**  
ج: تحقق من مسار الملف المصدر وسلامته قبل محاولة تضمينه. سيؤدي ملف معطوب إلى رفع استثناء أثناء الاستيراد.

**س: هل يمكنني تخصيص مظهر كائنات OLE في Excel؟**  
ج: نعم، تسمح لك `OleSpreadsheetOptions` بتحديد مؤشرات الصف/العمود، الحجم، والرؤية لتخصيص مظهر الكائن في ورقة العمل.

## الموارد

- **التوثيق:** [توثيق GroupDocs.Merger للـ Java](https://docs.groupdocs.com/merger/java/)
- **مرجع API:** [دليل مرجع API](https://reference.groupdocs.com/merger/java/)
- **التنزيل:** [الإصدارات الأخيرة](https://releases.groupdocs.com/merger/java/)
- **الشراء:** [شراء GroupDocs.Merger للـ Java](https://purchase.groupdocs.com/buy)
- **تجربة مجانية:** [ابدأ تجربة مجانية](https://releases.groupdocs.com/merger/java/)
- **ترخيص مؤقت:** [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- **الدعم:** [منتدى GroupDocs](https://forum.groupdocs.com/c/merger/) 

---

**آخر تحديث:** 2026-10-06  
**تم الاختبار مع:** أحدث نسخة من GroupDocs.Merger للـ Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [تضمين كائن Ole في PowerPoint باستخدام Java GroupDocs Merger](/merger/java/document-import/embed-ole-object-ppt-java-groupdocs-merger/)
- [كيفية تضمين PDF في Word باستخدام GroupDocs.Merger للـ Java – دليل شامل](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [دمج PDF في Java: تحميل مستند محلي باستخدام GroupDocs.Merger – دليل](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)