---
date: '2026-02-06'
description: تعلم كيفية استخراج صفحات محددة وتقسيم المستندات حسب نطاق الصفحات باستخدام
  GroupDocs.Merger للغة Java، بما في ذلك فلاتر الصفحات الفردية/الزوجية.
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: استخراج صفحات محددة باستخدام GroupDocs.Merger للـ Java
type: docs
url: /ar/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# استخراج صفحات محددة باستخدام GroupDocs.Merger للـ Java

استخراج **صفحات محددة** بكفاءة من ملفات PDF الكبيرة، ملفات Word، أو العروض التقديمية دون الحاجة إلى النسخ واللصق اليدوي. في هذا الدرس ستتعرف على كيفية تقسيم مستند حسب نطاق الصفحات، تطبيق فلاتر مثل الصفحات الفردية/الزوجية، وإنشاء ملفات صفحة واحدة — كل ذلك باستخدام **GroupDocs.Merger للـ Java**.

## إجابات سريعة
- **ماذا يعني “استخراج صفحات محددة”?** يعني إنشاء مستندات جديدة تحتوي فقط على الصفحات التي تختارها من الملف الأصلي.  
- **ما الصيغ المدعومة؟** PDF, DOCX, PPTX، والعديد من الصيغ الشائعة الأخرى.  
- **هل يمكنني الفلترة حسب الصفحات الفردية أو الزوجية؟** نعم، باستخدام خيار `RangeMode` (مثال: `OddPages`).  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يكفي للتقييم؛ الترخيص الدائم مطلوب للإنتاج.  
- **هل هو مناسب للمستندات الكبيرة؟** نعم — قسّم أقسام المستند الكبيرة للحفاظ على استهلاك الذاكرة منخفضًا.

## ما هو استخراج الصفحات المحددة؟
استخراج صفحات محددة هو عملية أخذ مجموعة فرعية من الصفحات من مستند أصلي وحفظها كملف جديد ومستقل. هذا مفيد لإنشاء تقارير مركزة، مشاركة بنود العقود، أو إعداد ملخصات العروض التقديمية.

## لماذا تستخدم GroupDocs.Merger للـ Java لتقسيم ملفات PDF و Word؟
- **واجهة برمجة تطبيقات موحدة** – تعمل مع PDF، Word، PowerPoint، وأكثر، لذا لا تحتاج إلى أدوات منفصلة.  
- **تحكم دقيق** – اختر نطاقات صفحات محددة، فلاتر فردية/زوجية، أو تقسيمات صفحة واحدة.  
- **تركيز على الأداء** – يتعامل مع الملفات الكبيرة بكفاءة عن طريق تدفق الصفحات بدلاً من تحميل المستند بالكامل في الذاكرة.  

## المتطلبات المسبقة
- **GroupDocs.Merger للـ Java** (أحدث إصدار)  
- **JDK 8+**  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse  
- Maven أو Gradle لإدارة التبعيات  

## إعداد GroupDocs.Merger للـ Java
أضف المكتبة إلى مشروعك باستخدام أداة البناء المفضلة لديك.

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

**Direct Download**: يمكنك أيضًا تنزيل المكتبة مباشرةً من [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
يمكنك الحصول على ترخيص عبر:
- **Free Trial** – اختبار جميع الميزات دون قيود.  
- **Temporary License** – فترة تقييم ممتدة.  
- **Purchase** – ترخيص إنتاج دائم.

**Basic Initialization and Setup**  
لتهيئة GroupDocs.Merger، أنشئ مثيلًا من `Merger` مع مسار المستند الخاص بك:
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## كيفية استخراج صفحات محددة باستخدام GroupDocs.Merger للـ Java
هذا القسم يشرح لك كيفية تقسيم مستند حسب نطاق الصفحات مع تطبيق مرشح الصفحات الفردية.

### الخطوة 1: تحديد مسارات الإدخال والإخراج
حدد ملف المصدر ونمط الوجهة للملفات المقسمة:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### الخطوة 2: تكوين خيارات التقسيم (النطاق والفلتر)
أنشئ كائن `SplitOptions` يحدد للمكتبة الصفحات التي يجب استخراجها والفلتر الذي يجب تطبيقه:
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – نمط اسم ملف الوجهة.  
- **3 and 7** – رقم الصفحة البداية والنهاية (شامل).  
- **RangeMode.OddPages** – يحتفظ فقط بالصفحات الفردية داخل النطاق، مما يؤدي فعليًا إلى **استخراج صفحات محددة**.

### الخطوة 3: تنفيذ عملية التقسيم
نفذ التقسيم باستخدام الخيارات المكوَّنة:
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### نصائح استكشاف الأخطاء وإصلاحها
- تحقق من أن مسارات الملفات صحيحة ويمكن الوصول إليها.  
- تأكد من أن أرقام الصفحات ضمن العدد الإجمالي لصفحات المستند؛ وإلا سيُرمى استثناء.  

## كيفية تقسيم PDF إلى صفحات منفردة (split pdf single pages)
إذا كنت بحاجة إلى كل صفحة كملف PDF منفرد، ما عليك سوى ضبط `RangeMode` إلى `AllPages` وتحديد نطاق يغطي المستند بالكامل. فئة `SplitOptions` نفسها تتعامل مع هذا السيناريو.

## كيفية تقسيم مستند كبير بكفاءة (split large document)
عند التعامل مع ملفات ضخمة جدًا، فكر في تقسيمها إلى نطاقات أصغر (مثال: 1‑100، 101‑200) لتقليل الضغط على الذاكرة. أغلق مثيل `Merger` بعد كل عملية لتحرير الموارد.

## كيفية تقسيم PDF للصفحات الفردية (split pdf odd pages)
المثال أعلاه يوضح بالفعل مرشح `OddPages`. استبدل `RangeMode.OddPages` بـ `RangeMode.EvenPages` لاستخراج الصفحات الزوجية بدلاً من ذلك.

## تطبيقات عملية
1. **Document Segmentation** – تقسيم العقود إلى ملفات PDF على مستوى البنود لتسهيل المراجعة.  
2. **Report Management** – استخراج فصل أو ملحق محدد من تقرير سنوي طويل.  
3. **Presentation Preparation** – عزل شرائح فردية لاجتماعات محددة.  

يمكنك أيضًا دمج هذه المنطق مع قواعد البيانات أو أنظمة إدارة المحتوى لأتمتة خطوط سير العمل.

## اعتبارات الأداء
- **Memory Management** – استدعِ `merger.close()` (أو اعتمد على try‑with‑resources) بعد المعالجة لتحرير مقابض الملفات.  
- **Selective Ranges** – اطلب فقط الصفحات التي تحتاجها فعلاً؛ هذا يقلل من عمليات الإدخال/الإخراج واستخدام المعالج.  

## الخلاصة
أصبح لديك الآن طريقة واضحة خطوة بخطوة **لاستخراج صفحات محددة** من أي نوع مستند مدعوم باستخدام GroupDocs.Merger للـ Java. هذه القدرة تُبسط سير عمل المستندات وتُمكنك من تقديم المحتوى الدقيق الذي يحتاجه المستخدمون.

### الخطوات التالية
- جرّب قيم `RangeMode` المختلفة (مثال: `EvenPages`, `AllPages`).  
- اجمع بين التقسيم ووظيفة **merge** لإعادة ترتيب أو ربط الصفحات المستخرجة.  
- استكشف الـ API الكامل للمستندات المحمية بكلمة مرور، العلامات المائية، وأكثر.

## الأسئلة المتكررة
**س: ما هو GroupDocs.Merger للـ Java؟**  
ج: مكتبة قوية تمكّن من دمج، تقسيم، وإعادة ترتيب الصفحات عبر العديد من صيغ المستندات.

**س: هل يمكنني استخدام GroupDocs.Merger مع لغات برمجة أخرى؟**  
ج: نعم، توجد قدرات مماثلة لـ .NET و C++.

**س: كيف أتعامل مع الاستثناءات أثناء معالجة المستند؟**  
ج: غلف الاستدعاءات بكتل `try‑catch` وتفقد `MergerException` للحصول على معلومات تفصيلية عن الخطأ.

**س: هل يمكن تقسيم المستندات دون الفلترة حسب الصفحات الفردية/الزوجية؟**  
ج: بالتأكيد — اضبط `RangeMode.AllPages` أو احذف معامل الفلتر لتقسيم حسب أرقام الصفحات الدقيقة.

**س: ما هي متطلبات النظام لاستخدام GroupDocs.Merger؟**  
ج: Java 8 أو أعلى وبيئة تطوير متكاملة متوافقة؛ لا توجد تبعيات أصلية إضافية.

## الموارد
- [توثيق GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)  
- [مرجع API](https://reference.groupdocs.com/merger/java/)  
- [تحميل المكتبة](https://releases.groupdocs.com/merger/java/)  
- [شراء الترخيص](https://purchase.groupdocs.com/buy)  
- [الإصدار التجريبي والترخيص المؤقت](https://releases.groupdocs.com/merger/java/)  
- [منتدى الدعم](https://forum.groupdocs.com/c/merger/)  

---

**آخر تحديث:** 2026-02-06  
**تم الاختبار مع:** أحدث إصدار من GroupDocs.Merger (Java)  
**المؤلف:** GroupDocs