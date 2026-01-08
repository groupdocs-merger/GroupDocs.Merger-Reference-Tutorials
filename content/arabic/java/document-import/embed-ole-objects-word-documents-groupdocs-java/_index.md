---
date: '2025-12-19'
description: تعلم كيفية تضمين ملفات PDF في مستندات Word وإضافة PDF إلى ملفات Word
  باستخدام GroupDocs.Merger للغة Java. دليل خطوة بخطوة لتضمين OLE بسلاسة.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: كيفية دمج ملف PDF في Word باستخدام GroupDocs.Merger للغة Java – دليل شامل
type: docs
url: /ar/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# كيفية تضمين PDF في Word باستخدام GroupDocs.Merger للـ Java

إنشاء كائن PDF داخل مستند Word مباشرةً يمكن أن يحسن التعاون بشكل كبير، لأن القراء لم يعودوا بحاجة للتنقل بين الملفات. في هذا الدليل ستكتشف **كيفية تضمين PDF في Word** باستخدام GroupDocs.Merger للـ Java، وسترى نصائح عملية حول **إضافة PDF إلى Word**. سنستعرض كل شيء من إعداد المكتبة إلى تخصيص حجم وموقع كائن OLE.

## إجابات سريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Merger for Java (latest version)  
- **هل يمكنني تضمين أي نوع ملف؟** نعم – PDFs, images, spreadsheets, إلخ، ككائنات OLE  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تعمل للتطوير؛ الترخيص التجاري مطلوب للإنتاج  
- **أي بيئة تطوير Java IDE هي الأفضل؟** IntelliJ IDEA, Eclipse, أو أي IDE يدعم Maven/Gradle  
- **كم من الوقت تستغرق عملية التنفيذ؟** تقريبًا 10‑15 دقيقة لتضمين أساسي  

## ما هو تضمين PDF في Word؟
إنشاء كائن OLE (Object Linking and Embedding) داخل ملف Word عند تضمين PDF. يظل PDF فعالًا بالكامل — يمكن للمستخدمين النقر المزدوج على الأيقونة لفتحها في عارض PDF، بينما يبقى مستند Word مستقلًا.

## لماذا إضافة PDF إلى Word باستخدام GroupDocs.Merger؟
- **توثيق مصدر واحد:** احتفظ بالعقود، الأدلة، أو التقارير معًا دون روابط خارجية.  
- **تحسين إمكانية الوصول:** يمكن للقراء عرض PDF دون مغادرة بيئة Word.  
- **ملائم للأتمتة:** مثالي لإنشاء تقارير دفعة أو حزم قانونية برمجيًا.  

## المتطلبات المسبقة
- **المكتبات والاعتمادات:** تضمين مكتبة GroupDocs.Merger عبر Maven أو Gradle.  
- **بيئة التطوير:** IntelliJ IDEA, Eclipse، أو أي IDE جافا.  
- **المعرفة الأساسية:** الإلمام بجافا ومفاهيم معالجة المستندات.  

## إعداد GroupDocs.Merger للـ Java
لتضمين كائنات OLE، أضف المكتبة أولاً إلى مشروعك.

### Maven
أضف هذا الاعتماد إلى ملف `pom.xml` الخاص بك:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
قم بتضمينه في ملف `build.gradle` الخاص بك:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct Download
بدلاً من ذلك، قم بتنزيل أحدث نسخة من [صفحة إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/).

**الحصول على الترخيص:** يمكنك البدء بنسخة تجريبية مجانية أو الحصول على ترخيص مؤقت لتقييم الميزات قبل الشراء. زر [Purchase GroupDocs](https://purchase.groupdocs.com/buy) لمزيد من التفاصيل.

## التهيئة الأساسية
استورد الفئات المطلوبة لتتمكن من العمل مع كائنات OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## دليل خطوة بخطوة لتضمين PDF في Word

### الخطوة 1: تحديد مسارات الملفات والصفحة المستهدفة
حدد مستند Word المصدر، PDF الذي تريد تضمينه، والمكان الذي يجب أن يظهر فيه كائن OLE.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – مسار ملف Word الموجود.  
- **`embeddedFilePath`** – PDF الذي تريد **إضافة PDF إلى Word**.  
- **`outputFilePath`** – المكان الذي سيُحفظ فيه المستند الجديد.  
- **`pageNumber`** – الصفحة التي ستستضيف كائن OLE.  

### الخطوة 2: تكوين OleWordProcessingOptions
خصص مظهر PDF المضمن عن طريق ضبط أبعاده.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – التحكم في حجم أيقونة PDF داخل مستند Word.  

### الخطوة 3: تهيئة Merger واستيراد كائن OLE
أنشئ نسخة `Merger` للمستند المصدر، استورد كائن OLE، واحفظ النتيجة.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – يأخذ `OleWordProcessingOptions` ويُدرج PDF ككائن OLE.  
- **`save()`** – يكتب المستند المعدل إلى `outputFilePath`.  

### الخطوة 4: (اختياري) إعادة تطبيق الإعدادات لكائنات إضافية
إذا كنت بحاجة إلى تضمين المزيد من ملفات PDF، كرر **الخطوة 1‑3** مع مسارات ملفات وأرقام صفحات جديدة. تسمح لك فئة `OleWordProcessingOptions` نفسها بالتحكم في كل كائن على حدة.

## تكوين OleWordProcessingOptions (متقدم)
يمكنك تعديل الموضع أكثر، مثل محاذاة الكائن أو إضافة تسمية توضيحية. يكرر مقتطف الشيفرة أدناه التكوين الأساسي للتوضيح:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## تطبيقات عملية
تضمين ملفات PDF مفيد في العديد من السيناريوهات الواقعية:

1. **الأدلة التقنية** – إدراج مخططات مفصلة أو ملفات PDF مرجعية مباشرةً في الدليل.  
2. **التقارير المالية** – إضافة ملفات PDF تدقيق إضافية دون كسر تدفق التقرير الرئيسي.  
3. **العقود القانونية** – إرفاق ملاحق أو مرفقات ككائنات OLE للوصول السهل أثناء المراجعة.  

## اعتبارات الأداء
عند التعامل مع مستندات كبيرة أو عدة كائنات OLE، ضع هذه النصائح في الاعتبار:

- **قصر المحتوى غير الضروري** – قم بتضمين الصفحات التي تحتاجها فعلاً فقط.  
- **إدارة الذاكرة** – استخدم علم Java `-Xmx` لتخصيص مساحة كومة كافية للملفات الكبيرة.  
- **ابقَ محدثًا** – إصدارات GroupDocs.Merger الأحدث غالبًا ما تتضمن تحسينات في الأداء.  

## الأسئلة المتكررة

**س: ما هو تضمين OLE؟**  
ج: يسمح التضمين بإدراج كائنات مثل PDFs في مستندات Word كروابط تحافظ على وظيفتها الأصلية.

**س: هل يمكنني تضمين عدة كائنات OLE في مستند واحد؟**  
ج: نعم، يمكن تكوين كل منها لصفحات وأحجام مختلفة باستخدام `OleWordProcessingOptions` منفصلة.

**س: هل هناك حد لحجم الملفات المضمنة؟**  
ج: الحد عادةً ما يحدده قيود Word نفسها، لكن GroupDocs.Merger يتعامل مع الملفات الكبيرة بفعالية.

**س: كيف أحل أخطاء التضمين؟**  
ج: تأكد من صحة مسارات الملفات وأن JVM لديها ذاكرة كافية. تحقق من أن PDF المصدر غير تالف.

**س: هل يمكنني تعديل الكائنات المضمنة بعد الإدراج؟**  
ج: يمكنك إعادة فتح ملف Word في Microsoft Word وتعديل كائن OLE، أو إعادة تشغيل كود Merger مع خيارات محدثة.

## موارد إضافية
- [توثيق GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [مرجع API](https://reference.groupdocs.com/merger/java/)
- [تنزيل أحدث نسخة](https://releases.groupdocs.com/merger/java/)
- [شراء GroupDocs](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية مجانية](https://releases.groupdocs.com/merger/java/)
- [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [منتدى الدعم](https://forum.groupdocs.com/c/merger/)

---

**آخر تحديث:** 2025-12-19  
**تم الاختبار مع:** GroupDocs.Merger for Java أحدث نسخة  
**المؤلف:** GroupDocs