---
date: '2026-06-26'
description: تعلم كيفية تحويل صفحات PDF إلى صور ومعاينة المستندات باستخدام GroupDocs.Merger
  for Java – الطريقة السريعة والموثوقة لإنشاء صور مصغرة للصفحات.
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: كيفية تحويل صفحات PDF إلى صور ومعاينة المستندات باستخدام GroupDocs.Merger for
  Java
type: docs
url: /ar/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# كيفية تحويل صفحات PDF إلى صور ومعاينة المستندات باستخدام GroupDocs.Merger للغة Java

في التطبيقات الحديثة غالبًا ما تحتاج إلى **تحويل صفحات pdf إلى صور** حتى يتمكن المستخدمون من إلقاء نظرة سريعة على المستند دون تنزيل الملف بالكامل. يشرح هذا الدليل كيفية إنشاء معاينات صفحات عالية الجودة باستخدام GroupDocs.Merger للغة Java، ويغطي كل شيء من الإعداد إلى التعامل مع التخزين المخصص. في النهاية، ستحصل على حل قابل لإعادة الاستخدام لتوليد صور مصغرة للمستندات يعمل على أي بيئة JDK 8+.

## إجابات سريعة
- **ماذا يعني “معاينة المستندات”؟** إنشاء تمثيلات صور خفيفة الوزن لكل صفحة.  
- **ما هو التنسيق المستخدم للمعاينات؟** JPEG بشكل افتراضي، لكن الصيغ الأخرى مدعومة.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يعمل للتطوير؛ يتطلب الترخيص المدفوع للإنتاج.  
- **هل يمكنني تخصيص مسار الإخراج؟** نعم، عن طريق تنفيذ `PageStreamFactory` مخصص.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أحدث.

## ما هو “معاينة المستندات”؟
معاينة المستند تعني إنشاء صور مصغرة بصرية (عادةً JPEG أو PNG) لكل صفحة حتى يتمكن المستخدمون من تصفح المحتوى بسرعة. تعزز هذه التقنية تجربة المستخدم في متصفحات الملفات، وبوابات مراجعة المحتوى، وأي نظام يدير أعدادًا كبيرة من المستندات، حيث توفر إشارة بصرية سريعة دون فتح الملف بالكامل.

## لماذا تستخدم GroupDocs.Merger للغة Java؟
GroupDocs.Merger يحول صفحات PDF إلى صور **أقل من 0.5 ثانية لكل صفحة على معالج 2 GHz نموذجي**، يدعم **أكثر من 50 تنسيق إدخال وإخراج**، ويسمح لك ببث المعاينات مباشرة إلى التخزين دون تحميل الملف بالكامل في الذاكرة. كما أن API القابلة للتوسيع تمنحك تحكمًا كاملاً في جودة الصورة، التنسيق، ومسار الوجهة.

## المتطلبات المسبقة
- **GroupDocs.Merger للغة Java** المكتبة (انظر التثبيت أدناه).  
- **JDK 8+** مثبت على جهازك.  
- بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، NetBeans) وMaven أو Gradle لإدارة التبعيات.  

## إعداد GroupDocs.Merger للغة Java
أضف المكتبة إلى مشروعك باستخدام أداة البناء المفضلة لديك.

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

**تحميل مباشر:**  
بدلاً من ذلك، قم بتنزيل أحدث نسخة من [إصدارات GroupDocs.Merger للغة Java](https://releases.groupdocs.com/merger/java/).

### الحصول على الترخيص
- **الإصدار التجريبي المجاني:** ابدأ بتنزيل الإصدار التجريبي المجاني لاستكشاف الميزات.  
- **ترخيص مؤقت:** احصل على ترخيص مؤقت للوصول الموسع أثناء التطوير.  
- **الشراء:** للاستخدام الإنتاجي الكامل، اشترِ ترخيصًا من [GroupDocs](https://purchase.groupdocs.com/buy).

بعد إضافة المكتبة، قم بتهيئتها باستخدام المسار إلى المستند الذي تريد معاينته:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## كيفية معاينة المستندات: دليل خطوة بخطوة
حمّل ملف المصدر، قم بتكوين `PageStreamFactory`، واستدعِ `generatePreview`.  
`generatePreview` هي طريقة تحول كل صفحة من المستند إلى صورة وفقًا للخيارات المقدمة.

### الخطوة 1: تهيئة Merger وتعريف PageStreamFactory
`Merger` هي الفئة الأساسية التي توفر طرقًا للدمج، التقسيم، وإنشاء معاينات المستندات.  
`PageStreamFactory` هي واجهة تخبر المكتبة أين تكتب كل صورة معاينة.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

هنا نقوم بإنشاء تنفيذ مخصص يكتب كل صورة صفحة إلى مجلد محدد باستخدام نظام تسمية متوقع.

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### الخطوة 2: إنشاء المعاينات
`generatePreview` يطلق عملية التحويل بناءً على الخيارات التي قدمتها. يقوم ببث كل صورة صفحة إلى `PageStreamFactory` التي حددتها، مما يضمن استهلاكًا منخفضًا للذاكرة.

```java
merger.generatePreview(previewOption);
```

### تحويل الصفحات إلى صور – PageStreamFactory مخصص
إذا كنت بحاجة إلى مزيد من التحكم في تسمية الملفات أو موقع التخزين، نفّذ مصنعك الخاص:

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### طرق المساعدة – إدارة التدفقات
هذه الطرق المساعدة تحافظ على نظافة الكود وتتعامل مع الاستثناءات بشكل منظم.

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## إنشاء صور مصغرة للمستندات – تطبيقات عملية
إنشاء المعاينات مفيد بشكل خاص لـ:
1. **أنظمة إدارة المستندات** – يمكن للمستخدمين تصفح الملفات دون فتحها.  
2. **منصات مراجعة المحتوى** – فحوصات بصرية سريعة قبل الموافقة على التحميلات.  
3. **أدوات تعليمية** – يمكن للطلاب إلقاء نظرة سريعة على شرائح المحاضرات أو صفحات الكتب الدراسية.  

## اعتبارات الأداء
- **إطلاق التدفقات بسرعة** لتحرير الذاكرة.  
- **تجنب تحميل المستندات بالكامل** في الذاكرة؛ دع المكتبة تتعامل مع التجزئة.  
- **استخدم إعدادات جودة الصورة المناسبة** لتحقيق التوازن بين السرعة والدقة البصرية.  

## الأسئلة المتكررة

**س: ما هو استخدام GroupDocs.Merger للغة Java؟**  
ج: يُستخدم للدمج، التقسيم، وإدارة المستندات بكفاءة، بما في ذلك إنشاء المعاينات وتحويل الصيغ.

**س: كيف يمكنني التعامل مع الاستثناءات أثناء عمليات التدفق؟**  
ج: غلف إنشاء وإغلاق التدفق بكتل try‑catch، كما هو موضح في طرق المساعدة، لمنع تسرب الذاكرة.

**س: هل يمكنني إنشاء معاينات بصيغ غير JPEG؟**  
ج: نعم، غيّر تعداد `PreviewMode` إلى PNG أو BMP أو TIFF وفقًا لمتطلباتك.

**س: ما هي المشكلات الشائعة في إنشاء معاينات المستندات؟**  
ج: تشمل المشكلات الشائعة مسارات ملفات غير صحيحة ونسيان إغلاق التدفقات، مما قد يسبب تسرب الذاكرة.

**س: كيف يمكنني دمج GroupDocs.Merger مع الأنظمة الأخرى؟**  
ج: استخدم API الخاصة به للاتصال بقاعدة البيانات، خدمات الويب، أو تطبيقات Java الأخرى لتحقيق أتمتة سلسة لسير العمل.

---

## الموارد
- [إصدارات GroupDocs.Merger للغة Java](https://releases.groupdocs.com/merger/java/)  
- [تنزيل](https://releases.groupdocs.com/merger/java/)  
- [التوثيق](https://docs.groupdocs.com/merger/java/)  
- [مرجع API](https://reference.groupdocs.com/merger/java/)  
- [الإصدار التجريبي المجاني](https://releases.groupdocs.com/merger/java/)  
- [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)  
- [شراء](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [الدعم](https://forum.groupdocs.com/c/merger/)

**آخر تحديث:** 2026-06-26  
**تم الاختبار مع:** GroupDocs.Merger أحدث نسخة (2025‑latest)  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [دروس عمليات صفحات المستند لـ GroupDocs.Merger Java](/merger/java/page-operations/)
- [كيفية تحميل PDF من عنوان URL باستخدام GroupDocs.Merger للغة Java: دليل شامل](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [إنشاء PDF صفحة واحدة باستخدام GroupDocs.Merger Java](/merger/java/document-splitting/)