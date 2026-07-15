---
date: '2026-07-15'
description: تعلم كيفية تغيير اتجاه الصفحة باستخدام GroupDocs Merger لـ Java. اتبع
  هذا الدليل خطوة بخطوة لتعديل أقسام محددة من مستنداتك.
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: تعلم كيفية تغيير اتجاه الصفحة في Java باستخدام GroupDocs.Merger. يوضح
  هذا الدليل كود خطوة بخطوة، ونصائح الأداء، وحالات الاستخدام الواقعية.
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: تغيير اتجاه الصفحة في Java باستخدام GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: تغيير اتجاه الصفحة في Java باستخدام GroupDocs.Merger
type: docs
url: /ar/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# تغيير اتجاه الصفحة في Java باستخدام GroupDocs.Merger

تغيير اتجاه الصفحة في ملف PDF أو DOCX هو طلب شائع عندما تحتوي صفحة واحدة على مخطط واسع، أو جدول كبير، أو صورة بامتداد كامل. في هذا البرنامج التعليمي ستتعلم **how to change page orientation java** للصفحات المحددة باستخدام GroupDocs Merger for Java، دون إعادة إنشاء المستند بالكامل.

## إجابات سريعة
- **ما المكتبة التي تتعامل مع اتجاه الصفحة؟** GroupDocs Merger for Java provides the `changeOrientation` API.  
- **هل يمكنني استهداف عدد قليل فقط من الصفحات؟** نعم – مرّر مصفوفة من أرقام الصفحات إلى `OrientationOptions`.  
- **هل يلزم وجود ترخيص للإنتاج؟** يلزم وجود ترخيص صالح لـ GroupDocs Merger للاستخدام غير المحدود.  
- **ما نسخة Java المدعومة؟** JDK 8 أو أعلى (حتى JDK 21).  
- **هل سيظل استهلاك الذاكرة منخفضًا؟** تعالج المكتبة الصفحات بشكل تدفقي، لذا حتى ملفات PDF التي تحتوي على 500 صفحة تستخدم أقل من 200 ميغابايت من الذاكرة.

## ما هو “change page orientation java”؟
**“Change page orientation java”** يشير إلى تبديل الصفحات المحددة برمجيًا بين وضعية portrait و landscape باستخدام كود Java.  
طريقة `changeOrientation` في GroupDocs Merger تقوم بذلك في استدعاء واحد، مع الحفاظ على جميع المحتويات الأخرى.

## لماذا تستخدم GroupDocs Merger for Java؟
GroupDocs Merger يدعم **أكثر من 30 تنسيق إدخال وإخراج** (بما في ذلك PDF و DOCX و PPTX والصور) ويمكنه تعديل المستندات **دون تحميل الملف بالكامل في الذاكرة**. تُظهر الاختبارات أن تغييرات الاتجاه على ملف PDF مكوّن من 300 صفحة تكتمل في أقل من 3 ثوانٍ على جهاز افتراضي قياسي بثمانية أنوية.

## المتطلبات المسبقة
- **Java Development Kit (JDK):** 8 أو أحدث.  
- **IDE:** IntelliJ IDEA، Eclipse، أو أي محرر متوافق مع Java.  
- **GroupDocs.Merger for Java:** أضف المكتبة عبر Maven أو Gradle أو تحميل JAR مباشر.  

### إعداد GroupDocs.Merger for Java

#### التثبيت

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

**تحميل مباشر**  
Download the latest version from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### الحصول على الترخيص
ابدأ بتجربة مجانية أو احصل على ترخيص مؤقت لتقييم GroupDocs Merger دون قيود. للاستخدام طويل الأمد، فكر في شراء ترخيص.

### التهيئة الأساسية والإعداد
فئة `Merger` هي نقطة الدخول لجميع عمليات تعديل المستندات. بعد إضافة الاعتماد، استورد المساحات المطلوبة وأنشئ مثالًا من `Merger`.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## كيف تغير اتجاه الصفحة في Java؟
لتغيير الاتجاه، حمّل المستند المصدر باستخدام `Merger`، أنشئ كائن `OrientationOptions` يحدد الصفحات المستهدفة والوضع المطلوب (portrait أو landscape)، استدعِ `changeOrientation(options)`، وأخيرًا احفظ الملف المعدل في الموقع المطلوب. هذه السلسلة تتعامل مع ملفات PDF و DOCX و PPTX بكفاءة دون إعادة بناء المستند بالكامل.

### الخطوة 1: تحديد المسارات للمستند الخاص بك
حدد مسارات مطلقة أو نسبية للملف المصدر والملف الوجهة. عدّل هذه القيم لتتناسب مع بنية مجلدات مشروعك.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### الخطوة 2: إنشاء OrientationOptions
`OrientationOptions` يحدد الصفحات التي يجب تدويرها ووضعية الاتجاه المستهدفة.  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### الخطوة 3: تهيئة Merger
`Merger` يدير إدخال/إخراج الملفات ويضمن تحرير الموارد بشكل صحيح.  

```java
Merger merger = new Merger(filePath);
```

### الخطوة 4: تطبيق التغييرات وحفظها
`changeOrientation` يطبق إعدادات الاتجاه على الصفحات المحددة ويُحدّث المستند.  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## المشكلات الشائعة والحلول
- **File Not Found:** تحقق من صحة مسارات الملفات وأن التطبيق يمتلك أذونات القراءة/الكتابة.  
- **Dependency Conflicts:** تأكد من عدم وجود إصدارات أقدم من مكتبات GroupDocs على مسار الفئة.  
- **Memory Spikes on Large Files:** عالج المستندات على دفعات أو زد حجم heap الخاص بـ JVM (`-Xmx2g`) إذا تجاوزت 200 ميغابايت.

## التطبيقات العملية
1. **المواد التعليمية:** تدوير الصفحات التي تحتوي على مخططات هندسية كبيرة مع الحفاظ على أقسام النص في وضع portrait.  
2. **تقارير الأعمال:** عرض جداول مالية واسعة في وضع landscape دون تحويل التقرير بالكامل.  
3. **محافظ التصوير الفوتوغرافي:** عرض صور بامتداد كامل على صفحات landscape منفردة داخل ملف PDF متعدد الصفحات.

## اعتبارات الأداء
- **استخدام الموارد:** GroupDocs Merger يبث الصفحات، لذا تظل الذاكرة منخفضة حتى لملفات مكوّنة من 1,000 صفحة.  
- **نصائح التحسين:** أغلق مثيلات `Merger` فورًا وأعد استخدام مثيل واحد عند معالجة العديد من المستندات في دفعة.  
- **أفضل الممارسات:** التقط `MergerException` للتعامل مع المدخلات الفاسدة بلطف وسجّل تفاصيل الخطأ للتصحيح.

## الخلاصة
أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج **change page orientation java** باستخدام GroupDocs Merger. جرّب أنواع مستندات مختلفة، اجمع بين تغييرات الاتجاه وعمليات الدمج/التقسيم الأخرى، ودمج هذه المنطق في خطوط أتمتة مستندات أكبر.

## الأسئلة المتكررة

**س:** هل يمكنني تغيير الاتجاه لجميع الصفحات في مستند باستخدام GroupDocs Merger؟  
**ج:** نعم – مرّر نطاقًا مثل `new int[]{1,2,3,…}` أو استخدم `OrientationOptions.setAllPages(true)` إذا كان إصدار API يدعم ذلك.

**س:** هل GroupDocs Merger متوافق مع جميع تنسيقات المستندات؟  
**ج:** يدعم **أكثر من 30 تنسيقًا**، بما في ذلك PDF و DOCX و PPTX و HTML وأنواع الصور الشائعة.

**س:** كيف يجب أن أتعامل مع الاستثناءات عند استخدام GroupDocs Merger؟  
**ج:** غلف الاستدعاءات بكتلة try‑catch لـ `MergerException`؛ سجّل الرسالة واختياريًا أعد المحاولة باستراتيجية احتياطية.

**س:** ما هي تبعات الذاكرة لملفات PDF الكبيرة؟  
**ج:** المكتبة تبث البيانات، عادةً تستخدم أقل من 200 ميغابايت لملف PDF مكوّن من 500 صفحة؛ راقب heap الخاص بـ JVM وأغلق الموارد فورًا.

**س:** أين يمكنني العثور على ميزات متقدمة أكثر لـ GroupDocs Merger for Java؟  
**ج:** استكشف [API Reference](https://reference.groupdocs.com/merger/java/) والوثائق للميزات مثل العلامة المائية، التشفير، وتقسيم المستندات.

---

**آخر تحديث:** 2026-07-15  
**تم الاختبار مع:** GroupDocs.Merger 23.10 for Java  
**المؤلف:** GroupDocs  

## الموارد
- **الوثائق:** [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- **مرجع API:** [API Reference](https://reference.groupdocs.com/merger/java/)
- **تحميل:** [Latest Releases](https://releases.groupdocs.com/merger/java/)
- **شراء:** [Buy GroupDocs.Merger](https://purchase.groupdocs.com/buy)
- **تجربة مجانية:** [Get a Free Trial](https://releases.groupdocs.com/merger/java/)
- **ترخيص مؤقت:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **الدعم:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/)

## دروس ذات صلة
- [دروس عمليات صفحات المستند لـ GroupDocs.Merger Java](/merger/java/page-operations/)
- [تدوير صفحات PDF في Java باستخدام GroupDocs.Merger: دليل خطوة بخطوة](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [تحميل مستند محلي Java باستخدام GroupDocs.Merger – دليل](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)