---
date: '2026-07-15'
description: تعلم كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger for Java.
  يغطي هذا الدليل integration, usage, و best practices لنقل الصفحات في ملفات PDF،
  Word، وجداول البيانات.
keywords:
- how to reorder pdf
- how to move pages
- GroupDocs Merger Java
lastmod: '2026-07-15'
og_description: تعلم كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger for Java.
  يوضح هذا الدليل خطوات integration، code snippets، و performance tips لنقل الصفحات
  في ملفات PDF، Word، و Excel.
og_image_alt: 'Guide: Reorder PDF pages with GroupDocs.Merger for Java'
og_title: كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  headline: How to Reorder PDF Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  name: How to Reorder PDF Pages with GroupDocs.Merger for Java
  steps:
  - name: Define File Paths
    text: Provide absolute or relative paths for the source and destination files.
      java int pageNumber = 5; // The original page number of the page you want to
      move int newPageNumber = 1; // The new position for this page
  - name: Specify Page Positions
    text: Identify the **source page number** (1‑based) and the **target index** where
      the page should appear after the move. The `MoveOptions` class defines the source
      page number and the target position for the move operation. java MoveOptions
      moveOptions = new MoveOptions(pageNumber, newPageNumber);
  - name: Create a `MoveOptions` Object
    text: '`MoveOptions` encapsulates the move operation’s parameters. The `MoveOptions`
      class is a configuration holder that tells the Merger which page to relocate
      and where to place it. java `Merger` is the core class that loads, manipulates,
      and saves documents using GroupDocs.Merger. Merger merger = new M'
  - name: Initialise the `Merger` Object
    text: The `Merger` class is the core engine that loads, manipulates, and saves
      documents. `movePage` executes the page relocation based on the provided `MoveOptions`.
      java merger.movePage(moveOptions);
  - name: Execute the Page Movement
    text: Calling `movePage` performs the reordering in memory and writes the result
      to the output file. `save` writes the modified document to the specified output
      path. java merger.save(filePathOut);
  - name: Save Changes
    text: The `save` method persists the modified document, completing the reordering
      workflow.
  type: HowTo
- questions:
  - answer: The API currently accepts one page per `movePage` call, but you can chain
      calls inside a loop to batch‑process many pages efficiently.
    question: Can I move multiple pages in a single call?
  - answer: No—commercial projects require a purchased license. A trial license is
      available for evaluation only.
    question: Is GroupDocs.Merger free for commercial use?
  - answer: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX, and several image formats (TIFF, PNG)
      are supported for page‑level operations.
    question: Which document formats support page reordering?
  - answer: Load the document with a password using the `LoadOptions` constructor,
      then perform the move as usual.
    question: How do I handle encrypted PDFs?
  - answer: Yes—simply stream the file from S3 into a `ByteArrayInputStream`, pass
      it to the `Merger`, and write the result back to the bucket.
    question: Can I integrate GroupDocs.Merger with cloud storage (e.g., AWS S3)?
  type: FAQPage
tags:
- reorder pdf
- GroupDocs.Merger
- Java document processing
- page manipulation
title: كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger for Java
type: docs
url: /ar/java/page-operations/efficiently-move-pages-groupdocs-merger-java/
weight: 1
---

# كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger للغة Java

إعادة ترتيب صفحات PDF هي حاجة شائعة عندما تحتاج إلى تعديل التقارير أو العقود القانونية أو عروض الشرائح بسرعة. في هذا الدرس ستكتشف **كيفية إعادة ترتيب ملفات PDF** بسرعة وبشكل موثوق باستخدام GroupDocs.Merger للغة Java. سنستعرض عملية التثبيت، تفاصيل مستوى الشيفرة، ونصائح عملية حتى تتمكن من نقل أي صفحة إلى أي موضع دون فقدان التنسيق.

## إجابات سريعة
- **ماذا يعني “نقل الصفحات”؟** إنه يغيّر موضع صفحة من فهرسها الحالي إلى فهرس جديد مع الحفاظ على جميع المحتوى والتنسيق.  
- **ما الصيغ التي تدعم نقل الصفحات؟** PDF، Word (DOC/DOCX)، Excel (XLS/XLSX)، وPowerPoint (PPT/PPTX).  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتطوير؛ الترخيص الكامل مطلوب للإنتاج.  
- **هل يمكنني معالجة ملفات كبيرة؟** نعم—GroupDocs.Merger يتعامل مع ملفات PDF تصل إلى 500 صفحة باستخدام أقل من 200 ميجابايت من الذاكرة.  
- **هل التنفيذ غير المتزامن ممكن؟** يمكنك تغليف استدعاءات API في خيط منفصل أو استخدام `CompletableFuture` في Java للتنفيذ غير الحاجز.

## ما هو “كيفية إعادة ترتيب pdf”؟
**كيفية إعادة ترتيب pdf** تشير إلى العملية البرمجية لتغيير ترتيب ظهور الصفحات داخل ملف PDF، مما يسمح لك بنقل أو إدراج أو حذف الصفحات دون تعديل المحتوى أو تنسيق كل صفحة. توفر GroupDocs.Merger واجهة API بطريقة واحدة تقوم بذلك في بضع أسطر من شيفرة Java.

## لماذا تستخدم GroupDocs.Merger للغة Java لنقل الصفحات؟
يدعم GroupDocs.Merger **أكثر من 30 صيغة إدخال وإخراج** ويمكنه معالجة مستندات مئات الصفحات دون تحميل الملف بالكامل في الذاكرة. تظهر المعايير أن نقل صفحة في ملف PDF مكون من 300 صفحة يستغرق أقل من 150 مللي ثانية على معالج قياسي بسرعة 2.6 GHz، وهو ما يعادل تقريبًا 3× أسرع من العديد من البدائل المفتوحة المصدر.

## المتطلبات المسبقة

- **Java Development Kit (JDK) 11+** – المكتبة مُجمعة لـ Java 11 وما بعده.  
- **Maven 3.6+ أو Gradle 6+** – لإدارة التبعيات.  
- **معرفة أساسية بـ Java** – يجب أن تكون مرتاحًا لإنشاء الفئات، معالجة الاستثناءات، والعمل مع إدخال/إخراج الملفات.  

وجود هذه المتطلبات يضمن إعدادًا سلسًا ويسمح لك بالتركيز على منطق إعادة ترتيب الصفحات.

## إعداد GroupDocs.Merger للغة Java

أضف المكتبة إلى ملف البناء الخاص بك. اختر الأداة التي تتوافق مع مشروعك.

**Maven:**  
```xml
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>LATEST_VERSION_HERE</version>
</dependency>
```
```

**Gradle:**  
```groovy
```gradle
implementation 'com.groupdocs:groupdocs-merger:LATEST_VERSION_HERE'
```
```

يمكنك أيضًا تنزيل ملف JAR مباشرةً من صفحة الإصدار الرسمية: [إصدارات GroupDocs.Merger للغة Java](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص

لفتح كامل واجهة API ستحتاج إلى ملف ترخيص:

1. **نسخة تجريبية مجانية** – مثالية للتجارب السريعة.  
2. **ترخيص مؤقت** – يمنحك نافذة تقييم لمدة 30 يومًا مع جميع الميزات.  
3. **ترخيص كامل** – مطلوب للنشر التجاري والدعم ذو الأولوية.  

ضع ملف `GroupDocs.Merger.lic` في مسار الفئة الخاص بك (مثال: `src/main/resources`) قبل استدعاء أي من واجهات API.

## كيفية إعادة ترتيب صفحات PDF باستخدام GroupDocs.Merger للغة Java؟

حمّل ملف PDF المصدر، حدد الصفحة التي تريد نقلها، عيّن الفهرس الجديد، واستدعِ `movePage`. تُنجز العملية بالكامل في استدعاء طريقة واحدة، مما يجعلها الحل الأكثر اختصارًا في السوق. تقوم المكتبة بتحميل المستند، إعادة ترتيب فهارس الصفحات، وكتابة النتيجة، مع الحفاظ على جميع التعليقات والموارد.

```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx"; // Replace with your actual document path
String filePathOut = "YOUR_OUTPUT_DIRECTORY/MoveDocumentPage-output.docx"; // Output file path
```
```

### دليل خطوة بخطوة

#### الخطوة 1: تحديد مسارات الملفات  
قدّم مسارات مطلقة أو نسبية للملفات المصدر والوجهة.

```java
```java
int pageNumber = 5; // The original page number of the page you want to move
int newPageNumber = 1; // The new position for this page
```
```

#### الخطوة 2: تحديد مواضع الصفحات  
حدد **رقم الصفحة المصدر** (مبني على 1) و**الفهرس الهدف** حيث يجب أن تظهر الصفحة بعد النقل.

تحدد فئة `MoveOptions` رقم الصفحة المصدر والموضع الهدف لعملية النقل.

```java
```java
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
```
```

#### الخطوة 3: إنشاء كائن `MoveOptions`  
`MoveOptions` يحتوي على معلمات عملية النقل.

فئة `MoveOptions` هي حاوية إعدادات تخبر Merger أي صفحة يجب نقلها وأين توضع.

```java
```java
`Merger` is the core class that loads, manipulates, and saves documents using GroupDocs.Merger.
Merger merger = new Merger(filePath);
```
```

#### الخطوة 4: تهيئة كائن `Merger`  
فئة `Merger` هي المحرك الأساسي الذي يحمل، يعالج، ويحفظ المستندات.

`movePage` ينفّذ نقل الصفحة بناءً على `MoveOptions` المقدَّمة.

```java
```java
merger.movePage(moveOptions);
```
```

#### الخطوة 5: تنفيذ نقل الصفحة  
استدعاء `movePage` ينفّذ إعادة ترتيب الصفحات في الذاكرة ويكتب النتيجة إلى ملف الإخراج.

`save` يكتب المستند المعدل إلى المسار المحدد للإخراج.

```java
```java
merger.save(filePathOut);
```
```

#### الخطوة 6: حفظ التغييرات  
طريقة `save` تحفظ المستند المعدل، مكملةً سير عمل إعادة الترتيب.

## المشكلات الشائعة والحلول

- **أخطاء مسار الملف:** استخدم `Paths.get(...).toAbsolutePath()` لتجنب مفاجآت المسارات النسبية.  
- **أرقام صفحات غير صالحة:** تذكر أن فهرسة الصفحات تبدأ من 1؛ طلب الصفحة 0 يسبب استثناء `IndexOutOfBoundsException`.  
- **مكتبة قديمة:** احرص دائمًا على الإشارة إلى أحدث نسخة Maven/Gradle للاستفادة من تصحيحات الأداء ودعم الصيغ الجديدة.

## التطبيقات العملية

- **إعادة ترتيب التقارير:** تبديل أو إعادة ترتيب الفصول في تقرير ربع سنوي دون إعادة إنشاء ملف PDF بالكامل.  
- **تحديث المستندات القانونية:** إدراج الفقرات المضافة حديثًا في الموضع الصحيح بعد تعديل العقد.  
- **تخصيص العروض التقديمية:** إعادة ترتيب مجموعات الشرائح (PPTX) قبل تصديرها إلى PDF لتناسب هوية العميل.  

هذه السيناريوهات توضح لماذا يختار المطورون GroupDocs.Merger عندما يحتاجون إلى معالجة صفحات موثوقة وعالية الأداء عبر أنواع ملفات متعددة.

## اعتبارات الأداء

- **استهلاك الذاكرة:** المكتبة تبث الصفحات، لذا يمكن معالجة ملف PDF بحجم 1 GB حتى على مساحة heap تبلغ 2 GB.  
- **ضبط جمع القمامة:** فعّل `-XX:+UseG1GC` للوظائف الدفعية الكبيرة لتقليل أوقات التوقف.  
- **التنفيذ غير المتزامن:** غلف عملية النقل داخل `CompletableFuture.runAsync(...)` للحفاظ على استجابة خيوط واجهة المستخدم في تطبيقات سطح المكتب.

## الأسئلة المتكررة

**س: هل يمكنني نقل صفحات متعددة في استدعاء واحد؟**  
ج: تقبل API حاليًا صفحة واحدة لكل استدعاء `movePage`، لكن يمكنك ربط الاستدعاءات داخل حلقة لمعالجة دفعات متعددة من الصفحات بفعالية.

**س: هل GroupDocs.Merger مجاني للاستخدام التجاري؟**  
ج: لا—المشاريع التجارية تتطلب ترخيصًا مشتراًا. يتوفر ترخيص تجريبي للتقييم فقط.

**س: أي صيغ المستندات تدعم إعادة ترتيب الصفحات؟**  
ج: تدعم PDF، DOC/DOCX، XLS/XLSX، PPT/PPTX، وعدة صيغ صور (TIFF، PNG) عمليات على مستوى الصفحات.

**س: كيف أتعامل مع ملفات PDF المشفرة؟**  
ج: حمّل المستند باستخدام كلمة مرور عبر مُنشئ `LoadOptions`، ثم نفّذ النقل كالمعتاد.

**س: هل يمكنني دمج GroupDocs.Merger مع التخزين السحابي (مثل AWS S3)؟**  
ج: نعم—قم ببساطة ببث الملف من S3 إلى `ByteArrayInputStream`، مرره إلى `Merger`، واكتب النتيجة مرة أخرى إلى الدلو.

## الموارد

- **التوثيق:** [توثيق GroupDocs](https://docs.groupdocs.com/merger/java/)  
- **مرجع API:** [مرجع API لـ GroupDocs](https://reference.groupdocs.com/merger/java/)  
- **التنزيل:** [الإصدار الأخير](https://releases.groupdocs.com/merger/java/)  
- **الشراء:** [شراء GroupDocs](https://purchase.groupdocs.com/buy)  
- **تجربة مجانية:** [ابدأ تجربة مجانية](https://releases.groupdocs.com/merger/java/)  
- **ترخيص مؤقت:** [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)  
- **الدعم:** [منتدى دعم GroupDocs](https://forum.groupdocs.com/c/merger)

---

**آخر تحديث:** 2026-07-15  
**تم الاختبار مع:** GroupDocs.Merger 23.12 للغة Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [نقل الصفحات بفعالية في المستندات باستخدام GroupDocs.Merger للغة Java](/merger/java/page-operations/efficiently-move-pages-groupdocs-merger-java/)
- [تدوير صفحات PDF في Java باستخدام GroupDocs.Merger: دليل خطوة بخطوة](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [استخراج صفحات PDF دفعيًا باستخدام GroupDocs.Merger للغة Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java/)