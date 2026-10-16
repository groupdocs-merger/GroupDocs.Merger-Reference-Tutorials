---
date: '2026-10-16'
description: تعلم كيفية استخراج ودمج الصفحات في Java باستخدام GroupDocs.Merger. يغطي
  هذا الدليل الإعداد، اختيار نطاقات الصفحات، دمج PDFs/DOCX، ونصائح الأداء.
keywords:
- extract and merge pages
- merge documents java
- groupdocs merger java
lastmod: '2026-10-16'
og_description: تعلم كيفية استخراج ودمج الصفحات في Java باستخدام GroupDocs.Merger،
  مكتبة قوية تدعم أكثر من 50 تنسيقًا وتتعامل مع المستندات الكبيرة بكفاءة.
og_image_alt: Guide showing how to extract and merge pages in Java with GroupDocs.Merger
og_title: كيفية استخراج ودمج الصفحات في Java باستخدام GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  headline: How to extract and merge pages in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  name: How to extract and merge pages in Java with GroupDocs.Merger
  steps:
  - name: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
    text: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
  - name: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
    text: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
  - name: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
    text: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
  type: HowTo
- questions:
  - answer: Yes, simply call `merger.join()` repeatedly for each additional source
      file.
    question: Can I merge more than two documents?
  - answer: It supports PDF, DOCX, DOC, PPTX, PPT, XLSX, XLS, and many other common
      office formats—over 50 in total.
    question: What file types does GroupDocs.Merger support?
  - answer: Use the `extract` method with `PageExtractOptions` to save selected pages
      as a new file. This is covered under the **extract pages java** use case.
    question: How do I extract pages from a document without merging?
  - answer: The library imposes no hard cap; practical limits depend on your system’s
      memory and CPU.
    question: Is there a limit to the number of pages I can join?
  - answer: Absolutely—concatenate timestamps or UUIDs to the filename using `PathConstants.getOutputFilePath()`
      or custom logic.
    question: Can I generate dynamic output file names?
  type: FAQPage
tags:
- merge pages
- GroupDocs.Merger
- Java document processing
- PDF manipulation
- DOCX merging
title: كيفية استخراج ودمج الصفحات في Java باستخدام GroupDocs.Merger
type: docs
url: /ar/java/document-joining/join-pages-groupdocs-merger-java-tutorial/
weight: 1
---

# كيفية استخراج ودمج الصفحات في Java باستخدام GroupDocs.Merger

في هذا الدرس الشامل ستكتشف كيفية **استخراج ودمج الصفحات** من ملفات PDF، DOCX، جداول البيانات، والعديد من أنواع المستندات الأخرى باستخدام GroupDocs.Merger للـ Java. سواء كنت بحاجة إلى تجميع كتيبات مخصصة، سحب فصول من عدة كتب، أو إنشاء تقرير مختصر من ملفات مصدر متفرقة، فإن هذا الدليل يمرّ بك عبر العملية بالكامل مع شروحات واضحة وأمثلة واقعية.

## إجابات سريعة
- **ما هو الاستخدام الأساسي؟** دمج الصفحات المحددة من ملفات PDF، DOCX، XLSX، PPTX، وغيرها من الصيغ المدعومة في ملف إخراج واحد.  
- **أي مكتبة تتعامل مع ذلك؟** GroupDocs.Merger للـ Java.  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تكفي للتقييم؛ الترخيص المدفوع مطلوب للاستخدام في الإنتاج.  
- **ما نسخة Java المطلوبة؟** Java 8 أو أعلى.  
- **هل يمكنني دمج أكثر من ملفين؟** نعم—استدعِ `join` بشكل متكرر لكل مستند مصدر إضافي.

## ما هو استخراج ودمج الصفحات؟
`extract and merge pages` هو عملية اختيار أرقام صفحات أو نطاقات محددة من مستند أو أكثر ثم تجميعها في ملف جديد. هذا يلغي الحاجة إلى النسخ واللصق اليدوي ويضمن أن المستند الناتج يحتفظ بالتنسيق الأصلي، الخطوط، والصور.

## لماذا نستخدم GroupDocs.Merger للـ Java؟
GroupDocs.Merger للـ Java مكتبة متعددة الاستخدامات تمكّن المطورين من معالجة المستندات برمجيًا، وتدعم أكثر من 50 صيغة، وتقدم معالجة سريعة واستهلاك منخفض للذاكرة، مما يجعلها مثالية لتدفقات عمل المستندات على الخادم والعمليات الدفعية واسعة النطاق في بيئات الشركات.

- **مرونة الصيغ:** تدعم أكثر من 50 صيغة إدخال وإخراج—بما في ذلك PDF، DOCX، PPTX، XLSX، وملفات الصور—لتتمكن من العمل مع أي مستند مكتبي تقريبًا.  
- **تركيز على الأداء:** تعالج فقط الصفحات التي تطلبها، مما يقلل استهلاك الذاكرة.  
- **تكامل سهل:** متاحة عبر Maven أو Gradle، مع وثائق API واضحة ولا تعتمد على مكتبات خارجية.  

## المتطلبات المسبقة
- معرفة أساسية ببرمجة Java.  
- Maven أو Gradle لإدارة الاعتمادات.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  

## إعداد GroupDocs.Merger للـ Java

أضف المكتبة إلى مشروعك باستخدام إحدى الطرق التالية.

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

بدلاً من ذلك، قم بتحميل أحدث نسخة مباشرةً من [إصدارات GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
لفتح جميع الميزات ستحتاج إلى ترخيص. يمكنك البدء بنسخة تجريبية مجانية أو شراء ترخيص كامل عبر [صفحة الشراء](https://purchase.groupdocs.com/buy). ترخيص مؤقت متاح أيضًا للتقييم قصير المدى.

## كيف يمكنني استخراج ودمج الصفحات في Java؟
فئة `Merger` هي المكوّن الأساسي في الـ API الذي ينشئ ويدير عمليات دمج المستندات. حمّل كل مستند مصدر باستخدام مُنشئ `Merger`، حدد أرقام الصفحات المطلوبة، واستدعِ `join` لدمجها. أخيرًا، احفظ النتيجة المدمجة بالصّيغة المطلوبة. هذا التدفق من البداية إلى النهاية يتطلب أربع استدعاءات فقط للطرق ويعمل بشكل ثابت عبر جميع صيغ الملفات المدعومة.

## دليل خطوة بخطوة لاستخراج ودمج صفحات محددة

### الخطوة 1: تهيئة Merger بالمستند الأساسي
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.PageJoinOptions;

String filePath = YOUR_DOCUMENT_DIRECTORY + "/sample.pdf"; // Source PDF document path
Merger merger = new Merger(filePath);
```

### الخطوة 2: تحديد الصفحات التي تريد دمجها
```java
// Specify the page numbers you wish to join (e.g., pages 1 and 2)
PageJoinOptions joinOptions = new PageJoinOptions(1, 2);
```

### الخطوة 3: دمج الصفحات المختارة من مستند ثانٍ
```java
// Path to your DOCX file\ String docxFilePath = YOUR_DOCUMENT_DIRECTORY + "/sample.docx";
merger.join(docxFilePath, joinOptions);
```

### الخطوة 4: حفظ النتيجة وإطلاق الموارد
```java
String outputFilePath = YOUR_OUTPUT_DIRECTORY + "/CrossJoinPagesFromVariousDocuments-output.pdf";
merger.save(outputFilePath);

try {
    merger.close();
} catch (Exception e) {
    // Handle exceptions appropriately
}
```

### الخطوة 5 (اختياري): توحيد مسارات الملفات باستخدام الثوابت
```java
import java.nio.file.Paths;
import java.io.File;

public class PathConstants {
    public static final String DOCUMENT_BASE_PATH = YOUR_DOCUMENT_DIRECTORY;
    public static final String OUTPUT_BASE_PATH = YOUR_OUTPUT_DIRECTORY;

    public static String getDocumentPath(String fileName) {
        return DOCUMENT_BASE_PATH + "/" + fileName;
    }

    public static String getOutputFilePath() {
        File outputFile = new File(OUTPUT_BASE_PATH, "CrossJoinPagesFromVariousDocuments-output.pdf");
        return outputFile.getPath();
    }
}
```

استخدام الثوابت يجعل الكود أنظف ويسهّل تعديل المسارات مستقبلاً.

## تطبيقات عملية
إليك بعض السيناريوهات الواقعية حيث يبرز **استخراج ودمج الصفحات**:

1. **تجميع المستندات:** سحب فصول مختارة من عدة كتب دراسية إلى ملف PDF واحد للمراجعة السريعة.  
2. **إنشاء تقارير:** دمج أقسام رئيسية من ملفات PDF المالية وملفات PDF المستخرجة من Excel في ملخص تنفيذي واحد.  
3. **تجميع أبحاث:** دمج مقتطفات من عدة أوراق أكاديمية (PDF، DOCX) في مستند مرجعي موحد.

## اعتبارات الأداء
- **أغلق Merger** بعد الانتهاء لتحرير الموارد الأصلية.  
- **اختر الصفحات المطلوبة فقط** بدلاً من دمج الملفات بالكامل؛ هذا يقلل وقت المعالجة بشكل كبير.  
- **تعامل مع الاستثناءات** برفق لتجنب الأعطال عندما يكون ملف المصدر مفقودًا أو معطوبًا.  

## المشكلات الشائعة والحلول
| المشكلة | الحل |
|-------|----------|
| **`OutOfMemoryError` عند التعامل مع ملفات كبيرة** | عالج الصفحات على دفعات أصغر وأغلق Merger بعد كل دفعة. |
| **صيغة ملف غير مدعومة** | تأكد من أن الصيغة مدرجة في صيغ GroupDocs.Merger المدعومة (PDF، DOCX، XLSX، PPTX، إلخ). |
| **الترخيص غير مُطبق** | تأكد من وضع ملف الترخيص في دليل جذر التطبيق أو تعيينه عبر `License license = new License(); license.setLicense("path/to/license.lic");`. |

## الأسئلة المتكررة

**س: هل يمكنني دمج أكثر من مستندين؟**  
ج: نعم، ما عليك سوى استدعاء `merger.join()` بشكل متكرر لكل ملف مصدر إضافي.

**س: ما أنواع الملفات التي يدعمها GroupDocs.Merger؟**  
ج: يدعم PDF، DOCX، DOC، PPTX، PPT، XLSX، XLS، والعديد من صيغ المكتب الشائعة—أكثر من 50 صيغة إجمالًا.

**س: كيف يمكنني استخراج صفحات من مستند دون دمجها؟**  
ج: استخدم طريقة `extract` مع `PageExtractOptions` لحفظ الصفحات المختارة كملف جديد. يتم شرح ذلك ضمن حالة الاستخدام **extract pages java**.

**س: هل هناك حد لعدد الصفحات التي يمكن دمجها؟**  
ج: لا تفرض المكتبة حدًا ثابتًا؛ الحدود العملية تعتمد على ذاكرة النظام ووحدة المعالجة المركزية.

**س: هل يمكنني توليد أسماء ملفات إخراج ديناميكية؟**  
ج: بالتأكيد—يمكنك ربط طوابع زمنية أو UUIDs باسم الملف باستخدام `PathConstants.getOutputFilePath()` أو منطق مخصص.

## موارد
- [الوثائق](https://docs.groupdocs.com/merger/java/)
- [مرجع API](https://reference.groupdocs.com/merger/java/)
- [تحميل GroupDocs.Merger للـ Java](https://releases.groupdocs.com/merger/java/)
- [شراء ترخيص](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية مجانية](https://releases.groupdocs.com/merger/java/)
- [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [منتدى الدعم](https://forum.groupdocs.com/c/merger/)

استكشف هذه الروابط لتعميق خبرتك وحل أي تحديات قد تواجهها.

---

**آخر تحديث:** 2026-10-16  
**تم الاختبار مع:** أحدث نسخة من GroupDocs.Merger للـ Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [دليل استخراج الصفحات Groupdocs Merger Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java-guide/)
- [دمج PDF Java: دمج ملفات PDF بفعالية باستخدام GroupDocs.Merger للـ Java – دليل خطوة بخطوة](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [نقل الصفحات Java – دروس عمليات صفحات المستند لـ GroupDocs.Merger](/merger/java/page-operations/)