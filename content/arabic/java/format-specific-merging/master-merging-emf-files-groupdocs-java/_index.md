---
date: '2026-08-31'
description: تعلم كيفية دمج صور عمودية لملفات EMF باستخدام GroupDocs.Merger for Java،
  مع تعليمات خطوة بخطوة لتكديس الصور عموديًا.
keywords:
- vertical image merge
- stack images vertically
- groupdocs merge java
- java merge library
lastmod: '2026-08-31'
og_description: تعلم كيفية دمج صور عمودية لملفات EMF باستخدام GroupDocs.Merger for
  Java. اتبع تعليمات خطوة بخطوة لتكديس الصور عموديًا بأداء عالي.
og_image_alt: Guide showing vertical image merge of EMF files using GroupDocs.Merger
  for Java
og_title: دمج صور عمودية لملفات EMF باستخدام GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to perform a vertical image merge of EMF files using GroupDocs.Merger
    for Java, with step‑by‑step instructions to stack images vertically.
  headline: How to perform a vertical image merge of EMF files using GroupDocs.Merger
    for Java
  type: TechArticle
- description: Learn how to perform a vertical image merge of EMF files using GroupDocs.Merger
    for Java, with step‑by‑step instructions to stack images vertically.
  name: How to perform a vertical image merge of EMF files using GroupDocs.Merger
    for Java
  steps:
  - name: initialize the Merger object
    text: Create a `Merger` instance pointing to the first EMF file.
  - name: configure image join options for vertical stacking
    text: ImageJoinOptions is a configuration class that specifies how images are
      combined during a merge.
  - name: add additional EMF files
    text: '`join` is a method of Merger that appends another document to the current
      merge.'
  - name: save the merged result
    text: Specify the output path and write the merged EMF file.
  type: HowTo
- questions:
  - answer: Yes, simply call `merger.join()` for each additional file; the library
      will stack them vertically.
    question: Can I merge more than two EMF files?
  - answer: It supports PDFs, Word documents, PowerPoint, and image formats such as
      PNG, JPEG, BMP, plus over 50 additional types.
    question: What other formats can GroupDocs.Merger handle?
  - answer: There is no hard limit, but very large files increase memory consumption;
      monitor resources and consider batch processing for files exceeding 200 MB.
    question: Is there a file‑size limit for merging?
  - answer: Absolutely—provide the full path for each file when calling `join`.
    question: Can I merge files located in different directories?
  - answer: Wrap merge calls in try‑catch blocks and log `MergerException` details
      for troubleshooting.
    question: How should I handle errors during the merge?
  type: FAQPage
tags:
- vertical image merge
- groupdocs merger
- emf file processing
- java document merging
title: كيفية دمج صور عمودية لملفات EMF باستخدام GroupDocs.Merger for Java
type: docs
url: /ar/java/format-specific-merging/master-merging-emf-files-groupdocs-java/
weight: 1
---

# كيفية إجراء دمج عمودي للصور لملفات EMF باستخدام GroupDocs.Merger للـ Java

في هذا الدرس ستكتشف كيفية **دمج الصور عموديًا** لعدة ملفات Enhanced Metafile (EMF) في مستند واحد باستخدام GroupDocs.Merger للـ Java. سواءً كنت تبني تقارير، أو تجمع المخططات، أو تُعدّ موارد العروض التقديمية، فإن ترتيب الصور عموديًا يوفر الوقت ويقضي على الحاجة إلى دمج الرسومات يدويًا. سنستعرض عملية التثبيت، الترخيص، واستدعاءات API الدقيقة اللازمة لتحقيق دمج نظيف من الأعلى إلى الأسفل.

## إجابات سريعة
- **ما هو دمج الصور عموديًا؟** ترتيب عدة صور واحدة فوق الأخرى في ملف إخراج واحد.  
- **أي مكتبة تدعم ذلك لملفات EMF؟** GroupDocs.Merger للـ Java.  
- **هل أحتاج إلى ترخيص؟** يتوفر نسخة تجريبية مجانية أو ترخيص مؤقت؛ الترخيص الكامل مطلوب للإنتاج.  
- **هل يمكنني دمج أكثر من ملفي EMF؟** نعم – استدعِ طريقة `join` بشكل متكرر.  
- **هل يتم الدمج في الذاكرة أم على القرص؟** تقوم المكتبة ببث البيانات، مما يقلل من استهلاك الذاكرة للملفات الكبيرة.  
- **كم عدد الصيغ التي يدعمها GroupDocs.Merger؟** أكثر من 50 صيغة إدخال وإخراج، بما في ذلك PDF و DOCX و PNG و JPEG.  

## ما هو دمج الصور عموديًا؟
يُدمج دمج الصور عموديًا عدة ملفات صورة (في هذه الحالة EMF) في مستند واحد حيث تظهر كل صورة **أسفل** الصورة السابقة. هذا التخطيط مثالي للرسومات المتواصلة، والرسوم التوضيحية خطوة بخطوة، أو المخططات المدمجة. يُستخدم عادة لإنشاء رسم توضيحي مستمر واحد من صفحات مخطط منفصلة، مما يُسهل التنقل ويقلل من عبء إدارة الملفات. يحتفظ الملف الناتج بالدقة الأصلية لكل مكوّن EMF.

## لماذا نستخدم GroupDocs.Merger للـ Java؟
يوفر GroupDocs.Merger واجهة برمجة تطبيقات Java مخصصة تتعامل مع ملفات EMF بشكل أصلي، وتزيل الحاجة إلى كتابة كود رسومي منخفض المستوى، وتُجري عمليات الدمج بأقل من 10 مللي ثانية من الحمل الإضافي لكل صورة على عتاد الخادم المعتاد. كما يدعم **أكثر من 50** صيغة مستندات وصور، مما يتيح لك إعادة استخدام نفس الكود للـ PDFs و PNGs وغيرها دون الحاجة إلى مكتبات إضافية.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) مثبتة ومُكوَّنة.  
- أداة بناء Maven أو Gradle لإدارة التبعيات.  
- الوصول إلى ترخيص GroupDocs (نسخة تجريبية مجانية، ترخيص مؤقت، أو مُشتراة).  

### المكتبات والاعتمادات المطلوبة
أضف GroupDocs.Merger إلى مشروعك:

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

يمكنك أيضًا تنزيل أحدث إصدار مباشرةً من [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### خطوات الحصول على الترخيص
- **نسخة تجريبية مجانية** – قم بالتنزيل وابدأ التجربة فورًا.  
- **ترخيص مؤقت** – احصل على واحد من [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/).  
- **شراء** – للاستخدام التجاري الكامل، زر [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## إعداد GroupDocs.Merger للـ Java
أولاً، استورد الفئات اللازمة:

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.ImageJoinOptions;
import com.groupdocs.merger.domain.options.ImageJoinMode;
```

`Merger` هي الفئة الأساسية في GroupDocs.Merger التي تنسق عمليات دمج المستندات. بعد الاستيراد، يمكنك إنشاء مثيل يشير إلى ملف EMF الأساسي الخاص بك.

قم بتهيئة كائن `Merger` مع المسار إلى ملف EMF الأساسي الخاص بك. يصبح هذا الملف القاعدة التي ستُرصّ عليها الصور الأخرى.

```java
Merger merger = new Merger("YOUR_DOCUMENT_DIRECTORY/sample.emf");
```

## دليل التنفيذ

### دمج ملفات EMF متعددة (دمج صور عموديًا)

#### الخطوة 1: تهيئة كائن Merger
أنشئ مثيل `Merger` يشير إلى ملف EMF الأول.

```java
String sourceEmfFile = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
Merger merger = new Merger(sourceEmfFile);
```

#### الخطوة 2: تكوين خيارات دمج الصور للترصيف العمودي
ImageJoinOptions هي فئة تكوين تحدد كيفية دمج الصور أثناء الدمج.  

```java
ImageJoinOptions joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
```

#### الخطوة 3: إضافة ملفات EMF إضافية
`join` هي طريقة في Merger تُضيف مستندًا آخر إلى الدمج الحالي.  

```java
String anotherEmfFile = "YOUR_DOCUMENT_DIRECTORY/another_sample.emf";
merger.join(anotherEmfFile, joinOptions);
```

#### الخطوة 4: حفظ النتيجة المدمجة
حدد مسار الإخراج واكتب ملف EMF المدمج.

```java
String outputFile = "YOUR_OUTPUT_DIRECTORY/merged.emf";
merger.save(outputFile);
```

### تكوين خيارات دمج الصور (ضبط دقيق)

إذا كنت بحاجة إلى مزيد من التحكم في التخطيط، يمكنك تعديل إعدادات إضافية:

```java
ImageJoinOptions options = new ImageJoinOptions();
```

اختر وضع الدمج (العمودي هو الافتراضي في سيناريونا):

```java
options.setJoinMode(ImageJoinMode.Vertical); // For vertical merging
// Use ImageJoinMode.Horizontal for horizontal merging
```

اختياري: أضف فجوة بين الصور أو اضبط المحاذاة.

```java
// Example: Set a gap of 10 units between images
// options.setGap(10);
```

تتيح لك هذه الخيارات تخصيص سلوك **دمج الصور عموديًا** ليتناسب مع متطلبات تصميم المستند الخاص بك.

## التطبيقات العملية
يُعد دمج الصور عموديًا لملفات EMF مفيدًا في العديد من الحالات الواقعية:

- **الأرشفة** – دمج سلسلة من المخططات في ملف واحد لتسهيل الاسترجاع.  
- **تحضير العروض التقديمية** – دمج رسومات الشرائح في صورة واحدة لتبسيط مجموعة الشرائح.  
- **تجميع البيانات** – جمع المخططات ذات الصلة من مصادر مختلفة للحصول على عرض موحد.

## اعتبارات الأداء
- **إدارة الذاكرة** – يدير جامع القمامة في Java المخازن المؤقتة، لكن تجنّب تحميل ملفات EMF الكبيرة جدًا دفعة واحدة.  
- **مراقبة الموارد** – راقب وحدة المعالجة المركزية والذاكرة RAM، خاصةً عند دمج العشرات من الصور عالية الدقة.  
- **ابقَ محدثًا** – الترقية إلى أحدث إصدار من GroupDocs.Merger (يصدر كل ثلاثة أشهر) تحسن باستمرار معدل النقل بنسبة تصل إلى 20 % وتضيف دعم صيغ جديدة.

## المشكلات الشائعة والحلول
| المشكلة | الحل |
|-------|----------|
| **OutOfMemoryError** عند دمج العديد من ملفات EMF الكبيرة | قم بمعالجة الملفات على دفعات أصغر أو زد حجم الذاكرة المخصصة للـ JVM (`-Xmx`). |
| **Incorrect orientation** بعد الدمج | تحقق من أن كل ملف EMF مصدر يمتلك DPI والاتجاه الصحيح قبل الدمج. |
| **License not recognized** | تأكد من وضع ملف الترخيص في الدليل الجذر للتطبيق أو ضبط مسار الترخيص برمجيًا. |

## الأسئلة المتكررة

**س: هل يمكنني دمج أكثر من ملفي EMF؟**  
ج: نعم، ما عليك سوى استدعاء `merger.join()` لكل ملف إضافي؛ ستقوم المكتبة بترصيفها عموديًا.

**س: ما الصيغ الأخرى التي يمكن لـ GroupDocs.Merger التعامل معها؟**  
ج: يدعم PDFs، مستندات Word، PowerPoint، وصيغ الصور مثل PNG، JPEG، BMP، بالإضافة إلى أكثر من 50 نوعًا إضافيًا.

**س: هل هناك حد لحجم الملف عند الدمج؟**  
ج: لا يوجد حد ثابت، لكن الملفات الكبيرة جدًا تزيد من استهلاك الذاكرة؛ راقب الموارد وفكّر في المعالجة على دفعات للملفات التي تتجاوز 200 ميغابايت.

**س: هل يمكنني دمج ملفات موجودة في أدلة مختلفة؟**  
ج: بالتأكيد—قدّم المسار الكامل لكل ملف عند استدعاء `join`.

**س: كيف يجب أن أتعامل مع الأخطاء أثناء الدمج؟**  
ج: احطّ استدعاءات الدمج بكتل try‑catch وسجّل تفاصيل `MergerException` للتحقق من الأخطاء.

## الموارد
- [توثيق GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [مرجع API](https://reference.groupdocs.com/merger/java/)
- [تنزيل GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [خيارات الشراء](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية وترخيص مؤقت](https://releases.groupdocs.com/merger/java/)
- [منتدى الدعم](https://forum.groupdocs.com/c/merger/)

---

**آخر تحديث:** 2026-08-31  
**تم الاختبار مع:** أحدث إصدار من GroupDocs.Merger (حتى 2026)  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية دمج الصور عموديًا باستخدام GroupDocs.Merger Java](/merger/java/format-specific-merging/join-multiple-images-vertically-groupdocs-merger-java/)
- [كيفية دمج الصور في Java: إتقان دمج الصور باستخدام GroupDocs.Merger لملفات BMP](/merger/java/image-operations/mastering-image-merging-java-groupdocs-merger/)
- [دمج صور PNG في Java – مكتبة معالجة الصور في Java](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)