---
date: '2026-02-19'
description: تعلم كيفية تضمين ملفات PDF في مستندات Word وإضافة PDF إلى ملفات Word
  باستخدام GroupDocs.Merger للغة Java. دليل خطوة بخطوة لتضمين OLE بسلاسة.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: كيفية تضمين ملف PDF في Word باستخدام GroupDocs.Merger للغة Java – دليل شامل
type: docs
url: /ar/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

Let's craft final answer.# كيفية تضمين pdf في word باستخدام GroupDocs.Merger للـ Java

تضمين ملف PDF مباشرة داخل مستند Word يمكن أن يحسن التعاون بشكل كبير، لأن القراء لم يعودوا بحاجة للتنقل بين الملفات. في هذا الدليل ستكتشف **كيفية تضمين pdf في word** باستخدام GroupDocs.Merger للـ Java، وستطلع على نصائح عملية حول **إضافة pdf إلى word** في سير العمل. سنستعرض كل شيء بدءًا من إعداد المكتبة وحتى تخصيص حجم وموقع كائن OLE، لتتمكن من أتمتة إنشاء المستندات بثقة.

## إجابات سريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Merger للـ Java (أحدث إصدار)  
- **هل يمكنني تضمين أي نوع ملف؟** نعم – PDF، صور، جداول بيانات، إلخ، ككائنات OLE  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تكفي للتطوير؛ الترخيص التجاري مطلوب للإنتاج  
- **أي بيئة تطوير Java هي الأنسب؟** IntelliJ IDEA، Eclipse، أو أي IDE يدعم Maven/Gradle  
- **كم يستغرق التنفيذ؟** تقريبًا 10‑15 دقيقة لتضمين أساسي  

## ما هو تضمين pdf في word؟
تضمين PDF يُنشئ كائن OLE (Object Linking and Embedding) داخل ملف Word. يبقى ملف PDF وظيفيًا بالكامل—يمكن للمستخدمين النقر المزدوج على الأيقونة لفتحها في عارض PDF، بينما يظل مستند Word مكتملًا ذاتيًا.

## لماذا إضافة pdf إلى word باستخدام GroupDocs.Merger؟
- **توثيق مصدر واحد:** احفظ العقود، الأدلة، أو التقارير معًا دون روابط خارجية.  
- **تحسين إمكانية الوصول:** يمكن للقراء عرض PDF دون مغادرة بيئة Word.  
- **ملائم للأتمتة:** مثالي لإنشاء تقارير دفعة أو حزم قانونية برمجيًا.  
- **قابل للتوسع:** يمكنك **تضمين عدة pdfs في مستندات word** بإعادة استخدام نفس سير العمل لكل ملف.

## المتطلبات المسبقة
- **المكتبات والاعتمادات:** أضف مكتبة GroupDocs.Merger عبر Maven أو Gradle.  
- **بيئة التطوير:** IntelliJ IDEA، Eclipse، أو أي IDE للـ Java.  
- **معرفة أساسية:** إلمام بـ Java ومفاهيم معالجة المستندات.

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
ضمن هذا في ملف `build.gradle` الخاص بك:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### تحميل مباشر
بدلاً من ذلك، حمّل أحدث إصدار من صفحة [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/).

**الحصول على الترخيص:** يمكنك البدء بنسخة تجريبية مجانية أو الحصول على ترخيص مؤقت لتقييم الميزات قبل الشراء. زر [Purchase GroupDocs](https://purchase.groupdocs.com/buy) للمزيد من التفاصيل.

## التهيئة الأساسية
استورد الفئات المطلوبة لتتمكن من العمل مع كائنات OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## دليل خطوة بخطوة لتضمين pdf في word

### الخطوة 1: تعريف مسارات الملفات والصفحة المستهدفة
حدد مستند Word المصدر، ملف PDF الذي تريد تضمينه، ومكان ظهور كائن OLE.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – المسار إلى ملف Word الموجود.  
- **`embeddedFilePath`** – ملف PDF الذي تريد **إضافة pdf إلى word**.  
- **`outputFilePath`** – المكان الذي سيُحفظ فيه المستند الجديد.  
- **`pageNumber`** – الصفحة التي ستستضيف كائن OLE.

### الخطوة 2: تكوين OleWordProcessingOptions
خصص مظهر PDF المضمّن عن طريق ضبط أبعاده.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – تتحكم في حجم أيقونة PDF داخل مستند Word.

### الخطوة 3: إنشاء Merger واستيراد كائن OLE
أنشئ كائن `Merger` للمستند المصدر، استورد كائن OLE، واحفظ النتيجة.
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
إذا احتجت لتضمين المزيد من ملفات PDF، كرّر **الخطوة 1‑3** مع مسارات صفحات جديدة. تسمح لك فئة `OleWordProcessingOptions` نفسها بالتحكم في كل كائن على حدة.

## تكوين OleWordProcessingOptions (متقدم)
يمكنك تعديل الموضع أكثر، مثل محاذاة الكائن أو إضافة تسمية توضيحية. يكرر المقتطف البرمجي أدناه التكوين الأساسي لتوضيح الفكرة:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## تطبيقات عملية
تضمين ملفات PDF مفيد في العديد من السيناريوهات الواقعية:

1. **الأدلة التقنية** – إدراج مخططات تفصيلية أو ملفات PDF مرجعية مباشرة داخل الدليل.  
2. **التقارير المالية** – إضافة ملفات PDF تدقيق مكملة دون كسر تدفق التقرير الرئيسي.  
3. **العقود القانونية** – إرفاق ملاحق أو مرفقات ككائنات OLE للوصول السريع أثناء المراجعة.  
4. **حزم التسويق** – **إدراج pdf في word** الكتيبات للحفاظ على مواصفات المنتج في متناول اليد.

## اعتبارات الأداء
عند التعامل مع مستندات كبيرة أو عدة كائنات OLE، ضع في اعتبارك النصائح التالية:

- **قصر المحتوى غير الضروري** – قم بتضمين الصفحات التي تحتاجها فقط.  
- **إدارة الذاكرة** – استخدم علم Java `-Xmx` لتخصيص مساحة كافية للـ heap للملفات الكبيرة.  
- **البقاء محدثًا** – إصدارات GroupDocs.Merger الأحدث غالبًا ما تتضمن تحسينات أداء.

## المشكلات الشائعة والحلول
- **مسار ملف غير صحيح:** تأكد من أن مسارات Word وPDF إما مطلقة أو نسبية بشكل صحيح بالنسبة لجذر المشروع.  
- **أخطاء نفاد الذاكرة:** زد حجم heap للـ JVM أو عالج المستندات على دفعات أصغر.  
- **PDF تالف:** تأكد من أن ملف PDF المصدر يفتح بشكل طبيعي في عارض قبل التضمين.  
- **فقدان أيقونة OLE:** تحقق من أن قالب Word غير محمي ضد إدراج OLE.

## الأسئلة المتكررة

**س: ما هو OLE embedding؟**  
ج: يتيح التضمين إدراج كائنات مثل PDF داخل مستندات Word كروابط تحافظ على وظائفها الأصلية.

**س: هل يمكنني تضمين عدة كائنات OLE في مستند واحد؟**  
ج: نعم، يمكن تكوين كل منها لصفحات وأحجام مختلفة باستخدام `OleWordProcessingOptions` منفصلة.

**س: هل هناك حد لحجم الملفات المضمنة؟**  
ج: الحد يُحدده عادةً قيود Word نفسها، لكن GroupDocs.Merger يتعامل مع الملفات الكبيرة بكفاءة.

**س: كيف أحل أخطاء التضمين؟**  
ج: تحقق من صحة مسارات الملفات وتأكد من أن JVM لديها ذاكرة كافية. تأكد من أن PDF المصدر غير تالف.

**س: هل يمكن تعديل الكائنات المضمنة بعد الإدراج؟**  
ج: يمكنك فتح ملف Word في Microsoft Word وتحرير كائن OLE، أو إعادة تشغيل كود Merger مع خيارات محدثة.

## موارد إضافية
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**آخر تحديث:** 2026-02-19  
**تم الاختبار مع:** GroupDocs.Merger للـ Java أحدث إصدار  
**المؤلف:** GroupDocs  

---