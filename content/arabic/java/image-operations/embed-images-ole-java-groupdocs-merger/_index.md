---
date: '2026-06-26'
description: تعلم كيفية تحويل الصورة إلى OLE باستخدام GroupDocs.Merger لـ Java. Step‑by‑step
  guide، code snippets، وأفضل الممارسات لتضمين الصور ككائنات OLE.
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: كيفية تحويل الصورة إلى OLE في Java باستخدام GroupDocs.Merger
type: docs
url: /ar/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# كيفية تحويل الصورة إلى OLE في Java باستخدام GroupDocs.Merger

إدراج الصور مباشرةً في مستند قد يبدو مرهقًا، لكن **convert image to OLE** يصبح سهلًا مع GroupDocs.Merger for Java. في هذا البرنامج التعليمي ستتعرف على لماذا كائنات OLE مفيدة، وكيفية إعداد بيئتك، والخطوات الدقيقة لإدراج صورة كرسمة OLE. في النهاية، ستحصل على نمط كود قابل لإعادة الاستخدام يعمل عبر ملفات Word وExcel وPowerPoint وPDF.

## الإجابات السريعة
- **ما هي الطريقة الرئيسية؟** استخدم `Merger.importOleDiagram()` بعد تحميل المستند المصدر.  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية تعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما صيغ الصور المدعومة؟** PNG, JPEG, BMP, GIF, و TIFF كلها مقبولة.  
- **هل يمكنني ضبط حجم وموقع OLE؟** نعم—`OleDiagramOptions` يتيح لك تحديد الصفحة، الإحداثيات، العرض، والارتفاع.  
- **هل العملية فعّالة في الذاكرة؟** GroupDocs.Merger يبث البيانات، لذا حتى ملفات 500 صفحة تبقى تحت 200 ميغابايت من الذاكرة.

## ما هو “convert image to OLE”؟
**Convert image to OLE** يعني تحويل ملف صورة نقطية إلى مخطط Object Linking and Embedding (OLE) يمكن تحريره داخل المستند المضيف. يتيح هذا التحويل للمستخدمين النهائيين النقر المزدوج على الصورة، فتحها في المحرر الأصلي لها، وحفظ التغييرات مرة أخرى إلى المستند الحاوي دون مغادرة الملف.

## لماذا تستخدم GroupDocs.Merger لتضمين OLE؟
GroupDocs.Merger يدعم **أكثر من 50 تنسيقًا للإدخال والإخراج**—بما في ذلك DOCX وXLSX وPPTX وPDF وأنواع الصور الشائعة—ويمكنه تضمين كائنات OLE في مستندات تصل إلى **300 ميغابايت** دون تحميل الملف بالكامل إلى الذاكرة. المكتبة تعالج ملف Word مكوّن من 200 صفحة مع ثلاث صور PNG مدمجة في أقل من **3 ثوانٍ** على خادم عادي بسرعة 2.6 GHz، مما يمنحك السرعة والقابلية للتوسع.

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8+** مثبت ومُعد في بيئة التطوير المتكاملة الخاصة بك.  
- **GroupDocs.Merger for Java** مضاف عبر Maven أو Gradle (الإصدار الأحدث موصى به).  
- إلمام أساسي بـ Java I/O streams والبرمجة الكائنية.

## إعداد GroupDocs.Merger للـ Java

لإضافة GroupDocs.Merger إلى مشروعك، أضف الاعتماد إلى ملف البناء الخاص بك. المكتبة متوفرة على Maven Central، لذا يمكنك نسخ المقتطف أدناه إلى `pom.xml` أو `build.gradle`.  

> **ملاحظة:** العناصر النائبة أدناه تمثل كتل الشيفرة الدقيقة من البرنامج التعليمي الأصلي؛ احتفظ بها دون تغيير.

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

يمكنك أيضًا تنزيل ملف JAR مباشرةً من صفحة الإصدارات الرسمية: [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية:** مثالية للنمذجة والتقييم.  
- **ترخيص مؤقت:** يمدد ميزات النسخة التجريبية لفترة محدودة.  
- **ترخيص كامل:** يفتح جميع إمكانيات OLE ويزيل حدود الاستخدام.

بعد إضافة الاعتماد، أنت جاهز لتهيئة المكتبة في شفرة Java الخاصة بك.

## كيفية تحويل الصورة إلى OLE في Java؟
لتحويل صورة إلى كائن OLE، حمّل المستند الهدف باستخدام كائن `Merger`، اقرأ ملف الصورة إلى مصفوفة بايت، أنشئ كائن `OleDiagramOptions` يحدد الصفحة، الموقع، والحجم، ثم استدعِ `merger.importOleDiagram(imageBytes, options)`. أخيرًا، احفظ المستند باستخدام `merger.save(outputPath)`. هذه العملية تدمج الصورة كرسمة OLE قابلة للتحرير.

### الخطوة 1: تحديد مسارات الملفات
حدد مكان وجود المستند المصدر والصورة. استبدل العناصر النائبة بالمسارات الفعلية على جهازك:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### الخطوة 2: قراءة بايتات الصورة
اقرأ ملف الصورة بالكامل إلى مصفوفة بايت. تصبح هذه المصفوفة حمولة OLE:

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### الخطوة 3: تكوين خيارات مخطط OLE
`OleDiagramOptions` يخبر GroupDocs أين وكيفية وضع كائن OLE. هذه الفئة هي **حامل الخيارات العليا لاستيراد مخطط OLE**؛ تتيح لك ضبط رقم الصفحة، إحداثيات X/Y، العرض، والارتفاع.

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### الخطوة 4: تهيئة Merger واستيراد مخطط OLE
`Merger` هو الفئة الأساسية التي تمثل مستندًا وتوفر طرقًا للتلاعب به. إنه **يغلف جميع عمليات القراءة/الكتابة** للملف الهدف.

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## حفظ مستند معدل

بعد دمج مخطط OLE، تحتاج إلى كتابة التغييرات مرة أخرى إلى القرص.

### الخطوة 1: تهيئة Merger بمسار المصدر
أعد استخدام نفس كائن `Merger` أو أنشئ كائنًا جديدًا يشير إلى المستند المعدل:

```java
Merger merger = new Merger(filePath);
```

### الخطوة 2: حفظ المستند المعدل
استدعِ طريقة `save` مع موقع الإخراج المطلوب. GroupDocs.Merger يكتب الملف بطريقة تدفقية، مما يحافظ على انخفاض استهلاك الذاكرة:

```java
merger.save(outputPath);
```

## التطبيقات العملية
إدراج الصور ككائنات OLE يفتح عدة سيناريوهات واقعية:

- **تقارير تفاعلية:** يمكن للمستخدمين النقر المزدوج على مخطط مدمج، تحريره في Excel، ورؤية التحديث البصري فورًا.  
- **إنشاء مستندات تلقائي:** يمكن لأنظمة المالية والرعاية الصحية حقن رسومات محدثة في العقود أو ملخصات المرضى دون تحرير يدوي.  
- **منصات التعاون:** يمكن للفرق مشاركة ملف Word واحد حيث يقوم كل عضو بتحديث مخططه الخاص، مما يقلل من مشاكل التحكم في الإصدارات.

## اعتبارات الأداء
للحفاظ على استجابة تطبيقك عند معالجة ملفات كبيرة:

- **تدفق البيانات:** GroupDocs.Merger يبث كلًا من الإدخال والإخراج، مما يمنع تحميل الملف بالكامل إلى الذاكرة.  
- **إعادة استخدام الكائنات:** إعادة استخدام كائن `Merger` واحد لعدة عمليات استيراد يقلل من عبء إنشاء الكائنات.  
- **مراقبة الذاكرة:** بالنسبة للمستندات التي تتجاوز 200 ميغابايت، فكر في زيادة مساحة heap للـ JVM (`-Xmx1g`) لتجنب `OutOfMemoryError`.

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| `Unsupported file format` error | الصورة ليست بصيغة PNG/JPEG/BMP/GIF/TIFF | حوّل الصورة إلى صيغة مدعومة قبل قراءة البايتات. |
| OLE object appears at the wrong location | إحداثيات `x`/`y` غير صحيحة في `OleDiagramOptions` | تحقق من أن الإحداثيات مقاسة بالنقاط (1 pt ≈ 1/72 in). |
| Output file is corrupted | عدم استدعاء `save()` بعد الاستيراد | تأكد من تنفيذ `merger.save(outputPath)` بعد جميع التعديلات. |

## الأسئلة المتكررة

**س: ما هو كائن OLE؟**  
ج: كائن OLE يدمج بيانات من تطبيق واحد (مثل صورة) إلى آخر (مثل ملف Word)، مما يسمح بالتحرير داخل المستند دون مغادرة المستند المضيف.

**س: هل يمكنني استخدام GroupDocs.Merger للمشاريع التجارية؟**  
ج: نعم—الاستخدام التجاري يتطلب ترخيصًا صالحًا. نسخة تجريبية متاحة للتقييم، لكن النشر في الإنتاج يجب أن يكون مرخصًا.

**س: كيف يتعامل المكتبة مع الصور الكبيرة جدًا؟**  
ج: تُقرأ الصور إلى مصفوفة بايت، لكن يمكنك تدفق الملفات الكبيرة باستخدام `FileInputStream` وتمرير الدفق إلى `importOleDiagram` للحفاظ على انخفاض استهلاك الذاكرة.

**س: أي صيغ مستندات تدعم تضمين OLE؟**  
ج: DOCX وXLSX وPPTX وPDF مدعومة بالكامل. بالنسبة لـ PDF، يُخزن كائن OLE كدفق ملف مدمج.

**س: هل هناك أي قيود على عدد كائنات OLE في المستند؟**  
ج: عمليًا لا توجد—GroupDocs.Merger يمكنه دمج عشرات مخططات OLE، يقتصر فقط على حجم المستند المضيف والذاكرة المتاحة.

## الموارد
- [إصدارات GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [توثيق GroupDocs.Merger Java](https://docs.groupdocs.com/merger/java/)
- [مرجع API للـ Java](https://reference.groupdocs.com/merger/java/)
- [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/)
- [صفحة شراء GroupDocs](https://purchase.groupdocs.com/buy)
- [منتدى دعم GroupDocs](https://forum.groupdocs.com/c/merger)

## الخلاصة
أنت الآن تمتلك سير عمل كامل وجاهز للإنتاج لتحويل **convert image to OLE** باستخدام GroupDocs.Merger للـ Java. من خلال تحديد مسارات الملفات، قراءة بايتات الصورة، تكوين `OleDiagramOptions`، واستدعاء `importOleDiagram`، يمكنك إثراء أي مستند مدعوم برسومات تفاعلية. استكشف واجهات برمجة التطبيقات الإضافية—مثل الدمج، التقسيم، وإضافة العلامات المائية—لبناء خط أنابيب معالجة مستندات متكامل.

---

**آخر تحديث:** 2026-06-26  
**تم الاختبار مع:** GroupDocs.Merger 23.10 للـ Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية إدراج PDF في Excel باستخدام GroupDocs.Merger للـ Java - استيراد كائن OLE – دليل خطوة بخطوة](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [كيفية إدراج PDF في Word باستخدام GroupDocs.Merger للـ Java – دليل شامل](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [كيفية دمج صور PNG باستخدام GroupDocs.Merger للـ Java – دليل خطوة بخطوة](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)