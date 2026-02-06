---
date: '2026-02-06'
description: تعرّف على كيفية تقسيم ملفات DOCX باستخدام GroupDocs.Merger للـ Java،
  بما يشمل تقسيم docx إلى ملفات، خيارات التقسيم في Java، واستخراج البث.
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: كيفية تقسيم DOCX باستخدام GroupDocs.Merger للـ Java
type: docs
url: /ar/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# إتقان تقسيم مستندات Java باستخدام GroupDocs.Merger: تقسيم صفحات DOCX إلى ملفات وتدفقات

في هذا الدرس ستكتشف **كيفية تقسيم ملفات docx** بفعالية باستخدام GroupDocs.Merger للـ Java. سواء كنت بحاجة إلى تقسيم عقد كبير إلى صفحات منفصلة أو استخراج أقسام محددة كـ streams، سنرشدك خلال كل خطوة، من الإعداد إلى الاستخدام العملي.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع تقسيم DOCX في Java؟** GroupDocs.Merger for Java.  
- **هل يمكنني تقسيم DOCX إلى ملفات منفصلة؟** نعم – استخدم `SplitOptions` مع أرقام الصفحات.  
- **هل من الممكن الحصول على الصفحات كـ streams بدلاً من ملفات؟** بالتأكيد، عن طريق توفير `SplitStreamFactory` مخصص.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي مؤقت يكفي للتقييم؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما إصدارات Java المدعومة؟** أي JDK 8+ يعمل مع أحدث إصدار من GroupDocs.Merger.

## ما هو “كيفية تقسيم docx”؟
تقسيم DOCX يعني أخذ مستند Word متعدد الصفحات وإنشاء ملفات فردية (أو streams) تحتوي على صفحة أو أكثر مختارة. هذا مفيد لتسليم المستندات بشكل معياري، أو سير عمل الامتثال، أو المعالجة الفورية حيث لا ترغب في تخزين ملفات مؤقتة.

## لماذا تستخدم GroupDocs.Merger للـ Java؟
- **معالجة بدون تبعيات:** تعمل باستخدام Java النقي، دون أي ملفات ثنائية أصلية.  
- **تحكم دقيق:** اختر الصفحات المحددة، صيغ الإخراج، وحتى الـ streams في الذاكرة.  
- **أداء قابل للتوسع:** التقسيم القائم على الـ streams يقلل من ضغط الذاكرة للملفات الكبيرة.  

## المتطلبات المسبقة

### المكتبات والتبعيات المطلوبة
- **Java Development Kit (JDK):** JDK 8 أو أحدث.  
- **GroupDocs.Merger للـ Java:** المكتبة الأساسية لمعالجة المستندات.

### إضافة التبعيات
أدرج المكتبة عبر Maven أو Gradle (كتل الشيفرة تبقى دون تغيير):

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

يمكنك أيضًا تنزيل أحدث إصدار من الموقع الرسمي: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
- **ترخيص تجريبي:** احصل على مفتاح مؤقت من صفحة [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/).  
- **ترخيص إنتاج:** اشترِ ترخيصًا كاملاً عبر [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## إعداد GroupDocs.Merger للـ Java
ابدأ تهيئة المكتبة في مشروع Java الخاص بك:

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

مع جاهزية البيئة، دعنا نستكشف الطريقتين الرئيسيتين لـ **تقسيم docx إلى ملفات** أو streams.

## كيفية تقسيم DOCX إلى ملفات باستخدام GroupDocs.Merger

### تقسيم المستند إلى صفحات منفردة
#### نظرة عامة
هذه الطريقة تنشئ ملفًا منفصلًا لكل صفحة مختارة، وهو مثالي لتوزيع الأقسام الفردية.

#### تنفيذ خطوة بخطوة

**الخطوة 1 – تحديد مسارات الإدخال والإخراج**  
حدد موقع ملف DOCX الأصلي ومكان حفظ الملفات المقسمة.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**الخطوة 2 – تكوين SplitOptions (split options java)**  
أخبر المكتبة بالصفحات التي تريد استخراجها.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – المجلد الذي سيتم وضع كل ملف صفحة فيه.  
- `new int[]{3,6,8}` – أرقام الصفحات التي تريد تقسيمها.

**الخطوة 3 – تنفيذ التقسيم**  
نفّذ العملية باستخدام كائن `Merger`.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**نصيحة احترافية:** تأكد من وجود دليل الإخراج وأن تطبيقك يمتلك صلاحيات الكتابة؛ وإلا سيفشل التقسيم.

### الأخطاء الشائعة
- **مجلد الإخراج مفقود:** الـ API لن ينشئ الأدلة تلقائيًا.  
- **أرقام صفحات غير صحيحة:** تبدأ فهارس الصفحات من 1؛ تحديد 0 سيسبب حدوث خطأ.

## كيفية تقسيم صفحات DOCX إلى Streams (في الذاكرة)

### نظرة عامة
عندما تحتاج إلى وصول مؤقت—مثل إرسال صفحة عبر خدمة ويب—التقاط الصفحات كـ streams يتجنب عمليات إدخال/إخراج القرص.

#### تنفيذ خطوة بخطوة

**الخطوة 1 – تحديد مسار الإدخال وتحضير قائمة للـ Streams**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**الخطوة 2 – تكوين SplitOptions مع SplitStreamFactory مخصص**  

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
- `createSplitStream` – يولد `OutputStream` جديد لكل صفحة مطلوبة.  
- `closeSplitStream` – يخزن الـ stream المكتمل للاستخدام لاحقًا.

**الخطوة 3 – تنفيذ التقسيم واسترجاع الـ Streams**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

### نصائح استكشاف الأخطاء وإصلاحها
- تأكد من صحة مسار ملف DOCX المصدر؛ أي خطأ إملائي سيسبب `FileNotFoundException`.  
- دائمًا أغلق الـ streams بعد الانتهاء لتفريغ الذاكرة.

## تطبيقات عملية
1. **العقود القانونية:** استخراج بنود منفردة للمراجعة بشكل مستقل.  
2. **منصات التعلم الإلكتروني:** تقديم ملفات Word فصلًا بفصل دون كشف الكتاب الكامل.  
3. **تقارير الأعمال:** إرسال قسم المالية فقط من تقرير ربع السنة إلى المدير المالي.

## اعتبارات الأداء
- **Streams فعّالة في الذاكرة:** يفضَّل استخدام نهج الـ stream للوثائق الكبيرة (>50 MB).  
- **معالجة دفعات:** اجمع عدة عمليات تقسيم في جلسة JVM واحدة لتقليل عبء بدء التشغيل.  
- **تنظيف الموارد:** استدعِ `merger.close()` وأغلق جميع الـ streams لتجنب التسريبات.

## الخلاصة
أنت الآن تعرف **كيفية تقسيم ملفات docx** إلى ملفات منفصلة أو إلى streams في الذاكرة باستخدام GroupDocs.Merger للـ Java. تمنحك هذه التقنيات مرونة لتخصيص تسليم المستندات وفقًا لأي احتياج تجاري.

**الخطوات التالية**
- جرّب نطاقات صفحات مختلفة وصيغ إخراج مختلفة (PDF، HTML، إلخ).  
- دمج التقسيم مع الدمج لإعادة تجميع حزم مخصصة بشكل فوري.  

## الأسئلة المتكررة

**س: ما هو GroupDocs.Merger للـ Java؟**  
ج: إنها مكتبة Java تمكّن من دمج، تقسيم، وتحويل مجموعة واسعة من صيغ المستندات، بما في ذلك DOCX، PDF، PPTX، وغيرها.

**س: كيف أحصل على ترخيص لـ GroupDocs.Merger؟**  
ج: يمكنك الحصول على ترخيص تجريبي مؤقت من [موقع GroupDocs](https://purchase.groupdocs.com/temporary-license/) للتقييم. للاستخدام الإنتاجي، اشترِ ترخيصًا كاملاً من نفس الموقع.

**س: هل يمكنني تقسيم ملفات PDF باستخدام نفس الـ API؟**  
ج: نعم، طريقة `split` تعمل مع PDF، DOCX، PPTX، وغيرها من الصيغ المدعومة.

**س: هل يمكن تقسيم مستند دون الكتابة إلى القرص؟**  
ج: بالتأكيد—استخدم النهج القائم على الـ stream الموضح أعلاه للاحتفاظ بكل شيء في الذاكرة.

**س: أي نسخة من GroupDocs.Merger يجب أن أستخدمها؟**  
ج: استهدف دائمًا أحدث إصدار ثابت للاستفادة من تحسينات الأداء وإصلاحات الأخطاء.

---

**آخر تحديث:** 2026-02-06  
**تم الاختبار مع:** GroupDocs.Merger للـ Java أحدث إصدار  
**المؤلف:** GroupDocs