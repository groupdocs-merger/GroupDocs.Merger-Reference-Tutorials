---
date: '2026-03-17'
description: تعلم كيفية تضمين ملف PDF في Excel واستيراد المستند إلى Excel باستخدام
  GroupDocs.Merger للغة Java. اتبع هذا الدليل التفصيلي مع أمثلة على الشيفرة ونصائح
  استكشاف الأخطاء وإصلاحها.
keywords:
- import OLE object into Excel
- embed PDF in Excel with Java
- use GroupDocs.Merger for document integration
title: كيفية تضمين ملف PDF في Excel باستخدام GroupDocs.Merger للغة Java - استيراد
  كائن OLE – دليل خطوة بخطوة
type: docs
url: /ar/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# كيفية تضمين PDF في Excel باستخدام GroupDocs.Merger للـ Java: دليل خطوة بخطوة

يمكن أن يحول تضمين PDF في Excel جدول بيانات ثابت إلى تقرير غني وتفاعلي يحتوي على المستند الأصلي بالكامل حيثما تحتاجه. في هذا البرنامج التعليمي ستتعلم **كيفية تضمين PDF في Excel** عن طريق استيراد ملف PDF ككائن OLE (Object Linking and Embedding) باستخدام GroupDocs.Merger للـ Java. سنستعرض جميع المتطلبات المسبقة، ونظهر لك الشيفرة الدقيقة، ونقدم لك نصائح عملية حتى تتمكن من بدء استخدام هذه التقنية في مشاريعك اليوم.

## إجابات سريعة
- **ماذا يعني “تضمين PDF في Excel”؟** يعني إدراج ملف PDF ككائن OLE بحيث يمكن فتح الـ PDF مباشرةً من داخل جدول البيانات.  
- **أي مكتبة تتولى عملية الاستيراد؟** توفر GroupDocs.Merger للـ Java طريقة `importDocument` لهذا الغرض.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ يتطلب الاستخدام الإنتاجي ترخيصًا تجاريًا.  
- **هل يمكنني تضمين أنواع ملفات أخرى؟** نعم – يمكن استيراد مستندات Word، الصور، وغيرها من الصيغ المدعومة ككائنات OLE.  
- **هل هذا النهج متوافق مع Java 8+؟** بالتأكيد – المكتبة تدعم Java 8 والإصدارات الأحدث.

## ما هو تضمين PDF في Excel؟
تضمين PDF في Excel يعني تخزين ملف PDF داخل المصنف ككائن OLE. يمكن للمستخدمين النقر المزدوج على الكائن لفتح الـ PDF الأصلي دون مغادرة جدول البيانات، وهو ما يُعد مثالياً لسجلات التدقيق، التقارير التفصيلية، أو المستندات المرجعية.

## لماذا نستخدم GroupDocs.Merger لتضمين PDF في Excel؟
- **تكامل سلس:** لا حاجة للنسخ واللصق اليدوي؛ الـ API يتولى تحديد الموقع والحجم.  
- **جاهز للأتمتة:** مثالي لمعالجة دفعات من التقارير الشهرية أو إنشاء لوحات معلومات برمجياً.  
- **دعم صيغ متعددة:** يعمل مع PDFs، مستندات Word، الصور، وأكثر، كل ذلك عبر مكتبة واحدة.  
- **تركيز على الأداء:** صُممت لتعمل بكفاءة مع مصنفات كبيرة وعدة كائنات OLE.

## كيفية تضمين PDF في Excel – المتطلبات المسبقة
- **Java Development Kit (JDK) 8 أو أعلى** – مثبت ومُعد في بيئة التطوير المتكاملة (IDE) الخاصة بك.  
- **GroupDocs.Merger للـ Java** – أضفه إلى مشروعك عبر Maven أو Gradle (انظر أدناه).  
- **بيئة تطوير متكاملة** مثل IntelliJ IDEA أو Eclipse لتحرير وتشغيل الشيفرة.  
- **معرفة أساسية بمعالجة الملفات في Java** – ستتعامل مع مسارات الملفات وتدفقات البيانات.

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
ضمّن المكتبة في ملف `build.gradle` الخاص بك:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

يمكنك أيضًا تنزيل أحدث إصدار مباشرةً من [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### خطوات الحصول على الترخيص
1. **نسخة تجريبية مجانية:** ابدأ بنسخة تجريبية لاستكشاف جميع الميزات.  
2. **ترخيص مؤقت:** اطلب ترخيصًا مؤقتًا للاختبار الموسع.  
3. **شراء:** احصل على ترخيص كامل للنشر التجاري.

## تنفيذ خطوة بخطوة

### الخطوة 1: تعريف مسارات الملفات وتهيئة الكائنات
أولاً، اضبط مسارات ملف Excel، ملف PDF الذي تريد تضمينه، وملف الإخراج. ثم أنشئ كائن `OleSpreadsheetOptions` الذي يحدد موقع ظهور كائن OLE.

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

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**لماذا نستخدم `importDocument`؟** تُخبر هذه الطريقة GroupDocs.Merger بمعاملة PDF ككائن OLE، مع الحفاظ على محتواه الأصلي وجعله قابلًا للوصول من داخل Excel.

### الخطوة 3: حفظ المصنف
احفظ التغييرات في ملف جديد حتى يبقى المصنف الأصلي دون تعديل.

```java
merger.save(filePathOut);
```

**خيارات التكوين الرئيسية:** يمكنك تعديل `OleSpreadsheetOptions` أكثر—مثل ضبط حجم الكائن، رؤيته، أو ما إذا كان يجب ربطه بدلاً من تضمينه.

## المشكلات الشائعة ونصائح استكشاف الأخطاء
- **FileNotFoundException:** تأكد من أن المسارات التي أدخلتها تشير إلى ملفات موجودة.  
- **عدم توافق الإصدارات:** تحقق من أن نسخة GroupDocs.Merger التي تستخدمها تتطابق مع نسخة JDK لديك.  
- **PDF تالف:** تأكد من أن ملف PDF يفتح بشكل مستقل قبل تضمينه.  
- **ضغط الذاكرة:** عند معالجة عدد كبير من المصنفات، أغلق كل مثيل `Merger` فور الانتهاء أو استخدم `try‑with‑resources` لتحرير الموارد.

## تطبيقات عملية
تُعدّ إضافة كائنات OLE إلى Excel مفيدة في العديد من السيناريوهات:
1. **دمج البيانات:** دمج ملفات PDF ربع السنوية في مصنف لوحة تحكم واحد.  
2. **عروض تقديمية تفاعلية:** توفير أوراق مواصفات تفصيلية تُفتح عند الطلب أثناء الاجتماع.  
3. **تقارير آلية:** إنشاء بيانات مالية شهرية تتضمن تلقائيًا الوثائق الداعمة.

## اعتبارات الأداء
- **إدارة الذاكرة:** أغلق أي مثيلات `Merger` لم تعد بحاجة إليها لتحرير الموارد.  
- **معالجة دفعات:** عند التعامل مع عشرات جداول البيانات، عالجها على دفعات صغيرة لتجنب ارتفاع استهلاك الذاكرة.  
- **أفضل ممارسات Java:** استخدم `try‑with‑resources` للتيارات وتعامل مع الاستثناءات بشكل مرن.

## الخلاصة
أصبح لديك الآن حل كامل وجاهز للإنتاج **لتضمين PDF في Excel** و**استيراد المستند إلى Excel** باستخدام GroupDocs.Merger للـ Java. جرّب صيغ ملفات مختلفة، اضبط خيارات الموضع، ودمج هذا التدفق في خطوط تقاريرك الآلية.

### الخطوات التالية
- جرّب تضمين مستند Word أو صورة لترى كيف يتعامل الـ API مع صيغ أخرى.  
- استكشف قدرات إضافية في GroupDocs.Merger مثل التقسيم، الدمج، أو تحويل المستندات.

## قسم الأسئلة المتكررة

**س1: هل يمكنني تضمين عدة كائنات OLE في ملف Excel واحد؟**  
ج1: نعم، يمكنك تضمين عدة كائنات OLE بتكرار عملية الاستيراد لكل كائن.

**س2: ما هي صيغ الملفات المدعومة ككائنات OLE؟**  
ج2: يدعم GroupDocs.Merger ملفات PDF، مستندات Word، ملفات Excel، الصور، والعديد من الصيغ الشائعة الأخرى.

**س3: كيف يمكنني التعامل مع الملفات الكبيرة بكفاءة باستخدام GroupDocs.Merger؟**  
ج3: حسّن استخدام الذاكرة بمعالجة الملفات على دفعات أصغر وتخلص من مثيلات `Merger` فور الانتهاء.

**س4: ماذا لو كان الملف المضمّن غير قابل للوصول أو تالف؟**  
ج4: تحقق من مسار الملف الأصلي وسلامته قبل محاولة تضمينه. سيؤدي الملف التالف إلى استثناء أثناء الاستيراد.

**س5: هل يمكنني تخصيص مظهر كائنات OLE في Excel؟**  
ج5: نعم، تسمح لك `OleSpreadsheetOptions` بتحديد مؤشرات الصف/العمود، الحجم، والرؤية لتخصيص مظهر الكائن في الورقة.

## موارد

- **التوثيق:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)
- **دليل API:** [API Reference Guide](https://reference.groupdocs.com/merger/java/)
- **التنزيل:** [Latest Releases](https://releases.groupdocs.com/merger/java/)
- **الشراء:** [Buy GroupDocs.Merger for Java](https://purchase.groupdocs.com/buy)
- **نسخة تجريبية مجانية:** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)
- **ترخيص مؤقت:** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **الدعم:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/) 

---

**آخر تحديث:** 2026-03-17  
**تم الاختبار مع:** أحدث نسخة من GroupDocs.Merger للـ Java  
**المؤلف:** GroupDocs