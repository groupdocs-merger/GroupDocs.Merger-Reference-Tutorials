---
date: '2026-07-25'
description: تعرف على كيفية تقسيم الملف إلى أسطر باستخدام GroupDocs.Merger for Java
  – دليل خطوة بخطوة لتقسيم المستندات بكفاءة في مشاريع Java.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: تقسيم الملف إلى أسطر باستخدام GroupDocs.Merger for Java. يوضح هذا
  الدليل كيفية تقسيم ملفات النص الكبيرة إلى أجزاء بسرعة، مع أمثلة على الشيفرة ونصائح
  لأفضل الممارسات.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: تقسيم الملف إلى أسطر باستخدام GroupDocs.Merger for Java – سريع وسهل
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: كيفية تقسيم الملف إلى أسطر باستخدام GroupDocs.Merger for Java
type: docs
url: /ar/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# كيفية تقسيم الملف حسب الأسطر باستخدام GroupDocs.Merger للـ Java

إذا كنت بحاجة إلى **تقسيم الملف حسب الأسطر**—على سبيل المثال، لتقسيم ملف سجل ضخم إلى أجزاء صغيرة، أو إمداد دفعات من البيانات إلى خط أنابيب، أو تحويل تقرير طويل إلى ملفات فصول منفصلة—فهذا الدرس يوضح لك بالضبط كيفية القيام بذلك باستخدام GroupDocs.Merger للـ Java. ستتعرف على سبب توفير الوقت الذي توفره المكتبة، وستحصل على تنفيذ جاهز للتشغيل، وتتعلم نصائح عملية تحافظ على سرعة تطبيقك وموثوقيته.

## إجابات سريعة
- **ماذا يعني “تقسيم الملف حسب الأسطر”؟** ينشئ ملفات نصية منفصلة يحتوي كل منها على نطاق محدد من أرقام الأسطر من المستند الأصلي.  
- **أي مكتبة تتعامل مع عملية التقسيم؟** توفر GroupDocs.Merger للـ Java واجهة برمجة تطبيقات بسيطة لتقسيم حسب فواصل الأسطر.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للاختبار؛ يلزم ترخيص دائم للاستخدام في الإنتاج.  
- **هل يمكنني التقسيم حسب عدد الأحرف بدلاً من ذلك؟** ليس مباشرة—استخدم خطوة معالجة مسبقة لإعادة تشكيل الملف قبل التقسيم.  
- **ما نسخة Java المدعومة؟** أي بيئة تشغيل Java 8+ متوافقة.

## ما هو “تقسيم الملف حسب الأسطر”؟
**تقسيم الملف حسب الأسطر** يعني أخذ مستند نصي واحد وتقسيمه إلى ملفات متعددة، يحتوي كل منها على نطاق محدد من الأسطر المتتالية (على سبيل المثال، الأسطر 1‑3، 4‑6، إلخ). هذا النهج مثالي عندما تريد معالجة البيانات بشكل متوازي، أو تقليل الضغط على الذاكرة، أو ببساطة جعل الملفات الطويلة أسهل في التنقل.

## لماذا نستخدم GroupDocs.Merger للـ Java؟
يقوم GroupDocs.Merger بتجريد عمليات الإدخال/الإخراج منخفضة المستوى للملفات، مما يتيح لك التركيز على منطق الأعمال. يتعامل بكفاءة مع ملفات تصل إلى 2 غيغابايت دون تحميل المستند بالكامل في الذاكرة، يدعم **أكثر من 70** تنسيق إدخال وإخراج، ويوفر واجهة برمجة تطبيقات سلسة تتكامل بسهولة مع بناء Maven أو Gradle. استخدام هذه المكتبة يقلل من وقت التطوير بنسبة تصل إلى **80 %** مقارنةً بالحلول اليدوية للـ I/O.

## المتطلبات المسبقة
- **مجموعة تطوير Java (JDK) 8 أو أعلى** – تأكد من وجود `java` و `javac` في مسار النظام (PATH).  
- **GroupDocs.Merger للـ Java** – أضف المكتبة عبر Maven أو Gradle أو تحميل مباشر.  
- **معرفة أساسية بـ Java** – يجب أن تكون مرتاحًا مع الفئات (classes)، والطرق (methods)، ومعالجة الاستثناءات.

## إعداد GroupDocs.Merger للـ Java
أضف المكتبة إلى مشروعك باستخدام إحدى الطرق أدناه.

**Maven** – paste this dependency into your `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – include the following line in `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**تحميل مباشر** – يمكنك أيضًا الحصول على ملف JAR من صفحة الإصدارات الرسمية: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
ابدأ بنسخة تجريبية مجانية لاستكشاف الـ API. لأعباء العمل الإنتاجية، احصل على ترخيص مؤقت أو كامل من بوابة GroupDocs.

## كيفية تقسيم ملف نصي حسب الأسطر (تنفيذ Java)
فيما يلي شرح مختصر خطوة بخطوة. يتم شرح كل خطوة بلغة بسيطة قبل العنصر النائب الذي يحدد مكان وجود الكود الفعلي، لتعرف بالضبط ما يحدث.

### الخطوة 1: تحديد مسارات المصدر ومخرجات
First, tell the library where your original file lives and where the split fragments should be written.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### الخطوة 2: تكوين خيارات التقسيم
Create a `TextSplitOptions` instance that describes the line intervals you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and line 6, producing two parts: lines 1‑3 and lines 4‑6.  
**التعريف:** `TextSplitOptions` هو كائن تكوين يحتفظ بمصفوفة فواصل الأسطر وقواعد تسمية المخرجات الاختيارية.  
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### الخطوة 3: تهيئة Merger وتنفيذ التقسيم
Finally, instantiate `Merger` with the source file and call `split()` with the options you just built.  
**التعريف:** `Merger` هو الفئة الأساسية في GroupDocs.Merger التي تنسق عمليات معالجة المستندات مثل التقسيم، والدمج، واستخراج الصفحات.  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

عند انتهاء استدعاء `split()`، ستجد ملفين جديدين في `YOUR_OUTPUT_DIRECTORY`، كل منهما يحتوي على نطاقات الأسطر المحددة.

## تطبيقات عملية (لماذا هذا مهم)
1. **خطوط معالجة البيانات** – تقسيم ملفات السجل الضخمة إلى أجزاء أصغر للمعالجة المتوازية، مما يقلل بشكل كبير من الوقت الإجمالي للمعالجة.  
2. **إدارة المستندات** – تحويل تقرير واحد إلى ملفات على مستوى الفصول، مما يسهل توزيعه على الفرق المختلفة.  
3. **تقسيم المحتوى** – إعداد أقسام من مقالة كبيرة لمنصات نشر مستهدفة، مما يحسن تحسين محركات البحث (SEO) وقابلية القراءة.

## نصائح الأداء
- **تحسين I/O** – يفضَّل استخدام `Files.newBufferedReader` عند التعامل مع ملفات كبيرة جدًا للحفاظ على انخفاض استهلاك الذاكرة.  
- **إغلاق الموارد** – رغم أن GroupDocs.Merger يتعامل مع معظم عمليات التنظيف، فإن إغلاق أي تدفقات مخصصة صراحةً يمنع التسربات.  
- **مراقبة الذاكرة** – قد يكون تقسيم ملفات بحجم جيجابايت مستهلكًا للذاكرة؛ قم بتخصيص مساحة كافية للـ heap (`-Xmx2g` أو أعلى) إذا لزم الأمر.  
- **المعالجة الدفعية** – عند تقسيم العديد من الملفات، أعد استخدام كائن `Merger` واحد لتقليل عبء إنشاء الكائنات.

## المشكلات الشائعة والحلول
| المشكلة | لماذا يحدث | الحل |
|-------|----------------|-----|
| `OutOfMemoryError` | ملف المصدر كبير يجاوز سعة الـ heap. | زيادة سعة heap في JVM أو تقسيم باستخدام فواصل أصغر. |
| `FileNotFoundException` | مسار غير صحيح أو أذونات مفقودة. | تحقق من أن `filePath` و `filePathOut` مساران مطلقان وقابلان للكتابة. |
| ملفات الإخراج فارغة | مصفوفة الفواصل لا تغطي المستند بالكامل. | تأكد من أن الفاصل الأخير ينتهي عند أو بعد عدد الأسطر الكلي. |

## الأسئلة المتكررة

**س: هل يمكنني تقسيم الملفات بناءً على عدد الأحرف بدلاً من أرقام الأسطر؟**  
ج: حاليًا، يركز GroupDocs.Merger للـ Java على فواصل الأسطر. ومع ذلك، يمكنك معالجة النص مسبقًا لتطابق عدد الأحرف المطلوب لكل سطر قبل استخدام هذه الميزة.

**س: هل هناك حد لعدد الفواصل التي يمكنني تحديدها للتقسيم؟**  
ج: لا يوجد حد صريح في المكتبة؛ قد تتدهور الأداء إذا طلبت آلاف التقسيمات الصغيرة لأن كل تقسيم يضيف عبء I/O.

**س: كيف أتعامل مع الأخطاء أثناء تقسيم الملف؟**  
ج: ضع منطق التقسيم داخل كتلة try‑catch وسجِّل تفاصيل `MergerException`. توفر الـ API رسائل واضحة تحدد نقطة الفشل.

**س: هل تدعم المكتبة صيغ نصية أخرى مثل CSV أو TSV؟**  
ج: نعم، لأن ملفات CSV و TSV هي ملفات نصية عادية، ينطبق نفس منطق فواصل الأسطر. تعامل معها كملفات `.txt` عند استدعاء الـ API.

**س: هل يمكنني أتمتة التقسيم لعدة ملفات في مجلد؟**  
ج: بالتأكيد. قم بالتكرار على `Files.list(Paths.get("folder"))`، وطبق نفس `TextSplitOptions` على كل ملف، وجمع الأجزاء المولدة.

## موارد إضافية
- [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/)
- [توثيق GroupDocs.Merger للـ Java](https://docs.groupdocs.com/merger/java/)
- [مرجع API الخاص بـ GroupDocs](https://reference.groupdocs.com/merger/java/)
- [الإصدارات الأخيرة](https://releases.groupdocs.com/merger/java/)
- [شراء GroupDocs](https://purchase.groupdocs.com/buy)
- [تجربة GroupDocs المجانية](https://releases.groupdocs.com/merger/java/)
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [دعم GroupDocs](https://forum.groupdocs.com/c/merger)

**آخر تحديث:** 2026-07-25  
**تم الاختبار مع:** GroupDocs.Merger 23.12 للـ Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية تقسيم ملف نصي إلى مستندات سطرية منفصلة باستخدام GroupDocs.Merger للـ Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [تقسيم PDF Java: تقسيم المستندات باستخدام GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [تحميل مستند محلي Java باستخدام GroupDocs.Merger – دليل](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)