---
date: '2026-02-13'
description: تعلم كيفية إضافة مرفق PDF وتضمين ملفات PPTX باستخدام GroupDocs.Merger
  للغة Java. يغطي هذا الدليل الإعداد، تحويل مرفق PPTX إلى PDF، وأفضل الممارسات.
keywords:
- embed documents in PDF with Java
- GroupDocs.Merger for Java setup
- embedding PPTX into PDF
title: إضافة مرفق PDF باستخدام GroupDocs.Merger للغة Java – دليل كامل
type: docs
url: /ar/java/format-specific-merging/embed-documents-pdf-groupdocs-merger-java/
weight: 1
---

# إضافة مرفق PDF باستخدام GroupDocs.Merger للغة Java

إدراج ملفات خارجية—مثل عرض PowerPoint—مباشرةً في ملف PDF هو طريقة قوية للحفاظ على المحتوى المرتبط معًا. في هذا البرنامج التعليمي ستقوم **بإضافة مرفق PDF** إلى ملف PDF موجود باستخدام GroupDocs.Merger للغة Java، وتتعلم كيفية **تحويل مرفق pptx إلى pdf**، وتكتشف أفضل الممارسات لحفظ وإدارة المستند الناتج.

## إجابات سريعة
- **ماذا يعني “add pdf attachment”؟** إنه يضم ملفًا آخر (مثل PPTX) داخل PDF كمرفق.
- **أي مكتبة تدعم ذلك؟** توفر GroupDocs.Merger للغة Java واجهة برمجة تطبيقات بسيطة لمرفقات PDF.
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للتقييم؛ يتطلب الترخيص الدائم للإنتاج.
- **هل يمكنني تضمين صيغ أخرى؟** نعم، معظم أنواع المستندات الشائعة مدعومة.
- **هل هو آمن للـ thread‑safe؟** العمليات آمنة عندما يستخدم كل خيط نسخة خاصة به من كائن `Merger`.

## ما هو “add pdf attachment”؟
إضافة مرفق PDF يعني إدراج ملف خارجي داخل حاوية PDF بحيث يمكن فتح الملف مباشرةً من لوحة المرفقات في عارض PDF. هذا يحافظ على جميع الأصول المرتبطة في ملف واحد قابل للنقل.

## لماذا تستخدم GroupDocs.Merger للغة Java؟
- **واجهة برمجة تطبيقات بسيطة** – استدعاءات سطر واحد لتضمين أو استخراج الملفات.  
- **متعددة المنصات** – تعمل على Windows وLinux وmacOS.  
- **مركزة على الأداء** – تتعامل مع الملفات الكبيرة بكفاءة.  
- **قابلة للتوسيع** – يمكن دمجها مع وحدات GroupDocs الأخرى لإنشاء سير عمل مستندات كامل.

## المتطلبات المسبقة
- Java 8 أو أحدث (IntelliJ IDEA، Eclipse، أو أي بيئة تطوير تفضلها).  
- Maven أو Gradle لإدارة التبعيات.  
- GroupDocs.Merger للغة Java 21.x أو أحدث.  

## إعداد GroupDocs.Merger للغة Java

### معلومات التثبيت
أضف تبعية GroupDocs.Merger إلى مشروعك.

**Maven:**
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>21.x.x</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.groupdocs:groupdocs-merger:21.x.x'
```

يمكنك تنزيل أحدث الملفات الثنائية من [إصدارات GroupDocs.Merger للغة Java](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – مجموعة كاملة من الميزات دون حدود زمنية.  
- **ترخيص مؤقت** – طلب مفتاح قصير الأجل للاختبار.  
- **شراء** – الحصول على ترخيص دائم عبر [شراء GroupDocs](https://purchase.groupdocs.com/buy).

### التهيئة الأساسية
أنشئ كائن `Merger` مع مسار ملف PDF المصدر. هذا يجهز المكتبة لعملية **add pdf attachment**.

## كيفية إضافة مرفق pdf إلى ملف PDF باستخدام GroupDocs.Merger
فيما يلي دليل خطوة بخطوة يغطي تعريف المسارات، تكوين الخيارات، تضمين المستند، وأخيرًا **save pdf embedded document**.

### الخطوة 1: تعريف مسارات الملفات والخيارات
استخدام واجهة `Paths` في Java يضمن معالجة مسارات مستقلة عن نظام التشغيل.  
```java
import java.nio.file.Paths;

String documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
String outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Construct full path for the source PDF file
String pdfFilePath = Paths.get(documentDirectory, "SAMPLE_PDF").toString();

// Construct full path for the embedded PPTX document
String embeddedDocumentPath = Paths.get(documentDirectory, "SAMPLE_PPTX").toString();
```

### الخطوة 2: تكوين خيارات التضمين
أنشئ كائن `PdfAttachmentOptions` الذي يحدد للـ merger أي ملف سيتم إرفاقه.  
```java
import com.groupdocs.merger.domain.options.PdfAttachmentOptions;

// Set up attachment options for the embedded document
PdfAttachmentOptions attachmentOptions = new PdfAttachmentOptions(embeddedDocumentPath);
```

### الخطوة 3: تهيئة Merger وتضمين المستند
أنشئ كائن `Merger` مع ملف PDF المصدر واستدعِ `importDocument` لتضمين ملف PPTX.  
```java
import com.groupdocs.merger.Merger;

// Create a Merger instance for the source PDF
Merger merger = new Merger(pdfFilePath);

// Import the embedded document into the PDF using specified options
merger.importDocument(attachmentOptions);
```

### الخطوة 4: حفظ النتيجة
أنشئ اسم ملف إخراج واضح و**save pdf embedded document** إلى المجلد المستهدف.  
```java
String pdfFileName = Paths.get(pdfFilePath).getFileName().toString();
String outputFilePath = Paths.get(outputDirectory, "ImportDocumentToPdf-" + pdfFileName.replaceFirst("\\.pdf", ".pdf-Embedded")).toString();

// Save the resultant PDF to the specified path
merger.save(outputFilePath);
```

**نصيحة احترافية:** تحقق من ظهور ملف الإخراج في لوحة مرفقات عارض PDF الخاص بك لتأكيد نجاح **add pdf attachment**.

## معالجة مسارات الملفات ودليل الإخراج
معالجة المسارات القوية تساعدك على **create pdf embedded files** في عمليات الدفعات:

1. **إنشاء مسار ديناميكي** – يعمل عبر Windows وmacOS وLinux.  
2. **تسمية تلقائية** – يحتفظ بأسماء الملفات الأصلية مع إلحاق “‑Embedded” لتسهيل التعرف.

## التطبيقات العملية
- **حزم الاجتماعات** – تضمين عروض الشرائح أو جداول البيانات أو العقود في ملف PDF واحد للتوزيع.  
- **التقارير التنظيمية** – دمج المستندات الداعمة مع التقرير الرئيسي لتلبية معايير الامتثال.  
- **التقارير الآلية** – إنشاء ملفات PDF تحمل ملفات البيانات الأصلية كمرفقات لتتبع التدقيق.

## اعتبارات الأداء
- حافظ على حجم الملفات المضمَّنة معقولًا لتجنب أوقات معالجة طويلة.  
- حرّر كائن `Merger` (`merger.close()`) بعد الحفظ لتحرير الذاكرة.  
- للعمليات الضخمة، شغّل كل مهمة تضمين في خيط منفصل للاستفادة من المعالجات متعددة النوى.

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|-------|-------|-----|
| **الملف غير موجود** | مسار غير صحيح أو أذونات ملف مفقودة | تحقق مرة أخرى من `documentDirectory` وتأكد من أن التطبيق لديه صلاحيات القراءة/الكتابة. |
| **OutOfMemoryError** | مرفقات كبيرة جدًا | زيادة حجم ذاكرة JVM (`-Xmx`) أو تضمين إصدارات أصغر من الملفات. |
| **المرفق غير مرئي** | عارض PDF يخزن نسخة قديمة في الذاكرة المؤقتة | افتح ملف PDF في نسخة جديدة من العارض أو امسح الذاكرة المؤقتة. |

## الأسئلة المتكررة

**س: هل يمكنني تضمين ملفات غير PPTX باستخدام GroupDocs.Merger؟**  
ج: نعم، تدعم الواجهة البرمجية العديد من الصيغ (DOCX، XLSX، صور، إلخ) لعمليات **add pdf attachment**.

**س: ما هو الحد الأقصى لحجم الملف المضمَّن؟**  
ج: يعتمد ذلك على ذاكرة الخادم وحجم كومة JVM؛ قد تتطلب الملفات الكبيرة تخصيص ذاكرة أعلى.

**س: كيف أتعامل مع الاستثناءات أثناء التضمين؟**  
ج: غلف الكود بكتلة `try‑catch` والتقط `IOException` أو `GroupDocsMergerException` لتسجيل الخطأ والتعافي بسلاسة.

**س: هل يمكن إزالة مرفق لاحقًا؟**  
ج: حاليًا يركز GroupDocs.Merger على إضافة المرفقات؛ الإزالة تتطلب عملية استخراج وإعادة إنشاء منفصلة.

**س: هل يمكنني استخدام هذا في تطبيق Java سحابي؟**  
ج: بالتأكيد—فقط أدرج تبعية Maven/Gradle وتأكد من أن وقت التشغيل لديه إمكانية الوصول إلى الملفات المطلوبة.

## الموارد
- **توثيق GroupDocs.Merger**: [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)  
- **مرجع API لـ GroupDocs.Merger**: [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/java/)  
- **تنزيلات GroupDocs.Merger**: [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/java/)  
- **صفحة شراء GroupDocs**: [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)  
- **نسخة تجريبية مجانية من GroupDocs**: [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **طلب ترخيص مؤقت**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **منتدى دعم GroupDocs**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**آخر تحديث:** 2026-02-13  
**تم الاختبار مع:** GroupDocs.Merger 21.x.x للغة Java  
**المؤلف:** GroupDocs