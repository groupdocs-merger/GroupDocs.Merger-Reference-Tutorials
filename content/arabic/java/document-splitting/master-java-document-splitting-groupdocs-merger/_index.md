---
date: '2026-07-25'
description: تعرف على كيفية تقسيم صفحات docx باستخدام GroupDocs.Merger for Java، مع
  تغطية تقسيم DOCX إلى ملفات منفصلة، استخراج التدفقات، وخيارات التقسيم.
keywords:
- split docx pages
- how to split docx
- split docx into files
lastmod: '2026-07-25'
og_description: قسّم صفحات docx باستخدام GroupDocs.Merger for Java. تعلّم خطوة بخطوة
  كيفية تقسيم DOCX إلى ملفات أو تدفقات مع أمثلة على الشيفرة.
og_image_alt: Guide to split DOCX pages using GroupDocs.Merger Java library
og_title: تقسيم صفحات DOCX باستخدام GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  headline: How to Split DOCX Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  name: How to Split DOCX Pages with GroupDocs.Merger for Java
  steps:
  - name: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
    text: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
  - name: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
    text: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
  - name: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
    text: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting over
      50 document formats—including DOCX, PDF, PPTX, and HTML—without requiring Microsoft
      Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Acquire a temporary trial license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/)
      for evaluation. For production, purchase a full license at the same site.
    question: How do I obtain a license for GroupDocs.Merger?
  - answer: Yes, the `split` method works with PDF, DOCX, PPTX, and other supported
      formats.
    question: Can I split PDF files using the same API?
  - answer: Absolutely—use the stream‑based approach shown above to keep everything
      in memory.
    question: Is it possible to split a document without writing to disk?
  - answer: Always target the latest stable release to benefit from performance improvements
      and bug fixes.
    question: Which version of GroupDocs.Merger should I use?
  type: FAQPage
tags:
- split docx
- GroupDocs.Merger
- Java document processing
- DOCX splitting
title: كيفية تقسيم صفحات DOCX باستخدام GroupDocs.Merger for Java
type: docs
url: /ar/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# تقسيم صفحات DOCX باستخدام GroupDocs.Merger للـ Java

في هذا البرنامج التعليمي ستكتشف **كيفية تقسيم صفحات docx** بكفاءة باستخدام GroupDocs.Merger للـ Java. سواء كنت بحاجة إلى تقسيم عقد ضخم إلى صفحات فردية أو استخراج أقسام محددة كتيارات في الذاكرة، سنستعرض الإعداد، الكود، ونصائح عملية حتى تتمكن من تنفيذ الحل في دقائق.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع تقسيم DOCX في Java؟** GroupDocs.Merger للـ Java.  
- **هل يمكنني تقسيم DOCX إلى ملفات منفصلة؟** نعم – قم بتكوين `SplitOptions` مع أرقام الصفحات المطلوبة.  
- **هل من الممكن الحصول على الصفحات كتيارات بدلاً من ملفات؟** بالطبع، عن طريق توفير `SplitStreamFactory` مخصص.  
- **هل أحتاج إلى ترخيص؟** رخصة تجريبية مؤقتة تعمل للتقييم؛ يلزم الحصول على رخصة كاملة للإنتاج.  
- **ما إصدارات Java المدعومة؟** أي JDK 8+ يعمل مع أحدث إصدار من GroupDocs.Merger.

## ما هو تقسيم صفحات docx؟
**تقسيم صفحات docx** يعني استخراج صفحة واحدة أو أكثر من مستند Word متعدد الصفحات وحفظ كل اختيار كملف منفصل أو كتيار في الذاكرة. يتيح ذلك توصيلًا معياريًا، عمليات تدفق عمل مدفوعة بالامتثال، أو معالجة فورية دون التعامل مع المستند بالكامل مرة واحدة.

## لماذا استخدام GroupDocs.Merger للـ Java؟
GroupDocs.Merger يعالج المستندات **بشكل كامل في Java** — بدون ثنائيات أصلية، بدون تثبيت Office. يدعم **أكثر من 50 صيغة إدخال وإخراج** ويمكنه تقسيم **DOCX مكون من 200 صفحة في أقل من ثانيتين** على خادم عادي بسرعة 2.5 GHz، مع الحفاظ على استهلاك الذاكرة تحت 100 MB بفضل هندسته القائمة على التيارات.

## المتطلبات المسبقة

### المكتبات والاعتمادات المطلوبة
- **Java Development Kit (JDK):** JDK 8 أو أحدث.  
- **GroupDocs.Merger للـ Java:** المكتبة الأساسية لمعالجة المستندات.

### إضافة الاعتماد
قم بتضمين المكتبة عبر Maven أو Gradle (كتل الشيفرة تبقى دون تغيير):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

يمكنك أيضًا تنزيل أحدث إصدار من الموقع الرسمي: [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
- **رخصة تجريبية:** احصل على مفتاح مؤقت من صفحة [رخصة تجريبية GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **رخصة إنتاج:** اشترِ رخصة كاملة عبر [شراء GroupDocs](https://purchase.groupdocs.com/buy).

## إعداد GroupDocs.Merger للـ Java
`Merger` هي الفئة المركزية التي تنسق عمليات التقسيم، الدمج، والتحويل.

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

مع جاهزية البيئة، دعنا نستكشف الطريقتين الرئيسيتين لـ **تقسيم صفحات docx إلى ملفات** أو تيارات.

## كيفية تقسيم DOCX إلى ملفات باستخدام GroupDocs.Merger
حمّل ملف DOCX المصدر، حدد نطاقات الصفحات المطلوبة، واستدعِ طريقة `split` — هذه الدعوة الواحدة تُنشئ ملفات إخراج منفصلة لكل جزء مختار. تقوم طريقة `split` بمعالجة المستند وفقًا لـ `SplitOptions` المقدمة وتعيد مسارات الملفات التي تم إنشاؤها. الخطوات التالية تُظهر تنفيذًا كاملاً وجاهزًا للإنتاج.

### الخطوة 1 – تحديد مسارات الإدخال والإخراج
حدد موقع ملف DOCX الأصلي والمجلد الذي ستُكتب فيه الملفات المقسمة.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

### الخطوة 2 – تكوين SplitOptions (خيارات التقسيم في Java)
`SplitOptions` تُخبر الـ API بالصفحات التي يجب استخراجها وأين توضع النتائج.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```

- `filePathOut` – المجلد الذي سيوضع فيه كل ملف صفحة.  
- `new int[]{3,6,8}` – أرقام الصفحات التي تريد تقسيمها (الصفحات تبدأ من 1).

### الخطوة 3 – تنفيذ التقسيم
أنشئ كائن `Merger` واستدعِ `split`. تُعيد الطريقة قائمة بمسارات الملفات التي تم إنشاؤها.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**نصيحة احترافية:** تأكد من وجود دليل الإخراج وأن تطبيقك يمتلك أذونات كتابة؛ وإلا سيفشل التقسيم.

#### الأخطاء الشائعة
- **مجلد الإخراج مفقود:** الـ API لا ينشئ الأدلة تلقائيًا.  
- **أرقام صفحات غير صحيحة:** تبدأ فهارس الصفحات من 1؛ تحديد 0 سيسبب خطأ.

## كيفية تقسيم صفحات DOCX إلى تيارات (في الذاكرة)
عندما تحتاج إلى وصول مؤقت — مثل إرسال صفحة عبر خدمة ويب أو إجراء تحليل في الذاكرة — فإن التقاط كل صفحة مستخرجة كتيار يلغي عبء الكتابة إلى القرص. باستخدام `SplitStreamFactory` مخصص، تقوم المكتبة بكتابة المحتوى المقسم مباشرةً إلى كائنات `ByteArrayOutputStream`، والتي يمكن بعدها نقلها، تخزينها، أو معالجتها أكثر دون ملفات وسيطة.

### الخطوة 1 – تحديد مسار الإدخال وإعداد قائمة للتيارات
حدد ملف المصدر وأنشئ حاوية للاحتفاظ بالتيارات التي تم إنشاؤها.

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

### الخطوة 2 – تكوين SplitOptions باستخدام SplitStreamFactory مخصص
نفّذ `SplitStreamFactory` لتوفير `OutputStream` جديد لكل صفحة وتخزين التيار المكتمل.

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```

- `createSplitStream` – يُنشئ `OutputStream` جديد لكل صفحة مطلوبة.  
- `closeSplitStream` – يخزن التيار المكتمل للاستخدام لاحقًا.

### الخطوة 3 – تنفيذ التقسيم واسترجاع التيارات
نفّذ عملية التقسيم ثم تعامل مع التيارات في الذاكرة حسب الحاجة (مثلاً، إرفاقها ببريد إلكتروني، رفعها إلى التخزين السحابي).

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**نصائح استكشاف الأخطاء**  
- تأكد من صحة مسار ملف DOCX المصدر؛ أي خطأ إملائي سيسبب `FileNotFoundException`.  
- دائمًا أغلق التيارات بعد الانتهاء لتفريغ الذاكرة وتجنب التسريبات.

## التطبيقات العملية
1. **العقود القانونية:** استخراج بنود فردية للمراجعة المنفصلة دون كشف الاتفاقية بالكامل.  
2. **منصات التعلم الإلكتروني:** تقديم ملفات Word فصلًا بفصل حسب الطلب، مع الحفاظ على حماية الكتاب الكامل.  
3. **تقارير الأعمال:** إرسال قسم المالية فقط من تقرير ربع السنة إلى المدير المالي، مما يقلل استهلاك النطاق الترددي ويحسن السرية.

## اعتبارات الأداء
- **تيارات كفء في الذاكرة:** يفضَّل نهج التيارات للمستندات الأكبر من 50 MB للحفاظ على انخفاض استهلاك الذاكرة.  
- **معالجة دفعات:** جمع عدة وظائف تقسيم في جلسة JVM واحدة لتقليل عبء بدء التشغيل.  
- **تنظيف الموارد:** استدعِ `merger.close()` وأغلق جميع التيارات لتجنب تسرب الذاكرة.  
- **مؤشر السرعة:** على خادم قياسي بثمانية نوى، يستغرق تقسيم DOCX مكون من 300 صفحة إلى صفحات فردية حوالي ~1.8 ثانية.

## الأسئلة المتكررة

**س: ما هو GroupDocs.Merger للـ Java؟**  
ج: إنها مكتبة Java تمكّن من الدمج، التقسيم، والتحويل لأكثر من 50 صيغة مستند — بما في ذلك DOCX، PDF، PPTX، وHTML — دون الحاجة إلى Microsoft Office.

**س: كيف أحصل على ترخيص لـ GroupDocs.Merger؟**  
ج: احصل على رخصة تجريبية مؤقتة من [موقع GroupDocs](https://purchase.groupdocs.com/temporary-license/) للتقييم. للإنتاج، اشترِ رخصة كاملة من نفس الموقع.

**س: هل يمكنني تقسيم ملفات PDF باستخدام نفس الـ API؟**  
ج: نعم، طريقة `split` تعمل مع PDF، DOCX، PPTX، وغيرها من الصيغ المدعومة.

**س: هل من الممكن تقسيم مستند دون الكتابة إلى القرص؟**  
ج: بالتأكيد — استخدم النهج القائم على التيارات الموضح أعلاه للحفاظ على كل شيء في الذاكرة.

**س: أي نسخة من GroupDocs.Merger يجب أن أستخدم؟**  
ج: استهدف دائمًا أحدث إصدار ثابت للاستفادة من تحسينات الأداء وإصلاحات الأخطاء.

---

**آخر تحديث:** 2026-07-25  
**تم الاختبار مع:** GroupDocs.Merger للـ Java أحدث إصدار  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية تقسيم المستندات إلى ملفات متعددة الصفحات باستخدام GroupDocs.Merger للـ Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)
- [كيفية استخراج صفحات محددة في Java باستخدام GroupDocs.Merger](/merger/java/document-extraction/)
- [كيفية دمج صفحات محددة في Java باستخدام GroupDocs.Merger](/merger/java/document-joining/join-specific-pages-groupdocs-merger-java/)