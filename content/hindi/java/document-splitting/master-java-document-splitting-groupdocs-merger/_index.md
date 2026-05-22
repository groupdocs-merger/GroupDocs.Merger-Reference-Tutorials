---
date: '2026-02-06'
description: GroupDocs.Merger for Java का उपयोग करके DOCX फ़ाइलों को कैसे विभाजित
  करें, सीखें, जिसमें DOCX को फ़ाइलों में विभाजित करना, जावा में विभाजन विकल्प, और
  स्ट्रीम निष्कर्षण शामिल हैं।
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: GroupDocs.Merger for Java के साथ DOCX को कैसे विभाजित करें
type: docs
url: /hi/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# GroupDocs.Merger के साथ जावा दस्तावेज़ विभाजन में निपुण बनें: DOCX पृष्ठों को फ़ाइलों और स्ट्रीम में विभाजित करें

इस ट्यूटोरियल में आप GroupDocs.Merger for Java के साथ **how to split docx** दस्तावेज़ों को कुशलतापूर्वक करने की विधि सीखेंगे। चाहे आपको बड़े अनुबंध को अलग-अलग पृष्ठों में विभाजित करना हो या विशिष्ट अनुभागों को स्ट्रीम के रूप में निकालना हो, हम आपको सेटअप से लेकर वास्तविक उपयोग तक हर कदम पर मार्गदर्शन करेंगे।

## त्वरित उत्तर
- **What library handles DOCX splitting in Java?** GroupDocs.Merger for Java.  
- **Can I split a DOCX into separate files?** Yes – use `SplitOptions` with page numbers.  
- **Is it possible to get pages as streams instead of files?** Absolutely, by providing a custom `SplitStreamFactory`.  
- **Do I need a license?** A temporary trial license is enough for evaluation; a full license is required for production.  
- **Which Java versions are supported?** Any JDK 8+ works with the latest GroupDocs.Merger release.

## “how to split docx” क्या है?
DOCX को विभाजित करने का मतलब है एक बहु‑पृष्ठ Word दस्तावेज़ को लेकर व्यक्तिगत फ़ाइलें (या स्ट्रीम) बनाना, जिनमें एक या अधिक चयनित पृष्ठ होते हैं। यह मॉड्यूलर दस्तावेज़ वितरण, अनुपालन कार्यप्रवाह, या ऑन‑द‑फ्लाई प्रोसेसिंग के लिए उपयोगी है जहाँ आप अस्थायी फ़ाइलें संग्रहीत नहीं करना चाहते।

## GroupDocs.Merger for Java का उपयोग क्यों करें?
- **Zero‑dependency processing:** Works with pure Java, no native binaries.  
- **Fine‑grained control:** Choose exact pages, output formats, and even in‑memory streams.  
- **Scalable performance:** Stream‑based splitting reduces memory pressure for large files.  

## पूर्वापेक्षाएँ

### आवश्यक लाइब्रेरी और निर्भरताएँ
- **Java Development Kit (JDK):** JDK 8 or newer.  
- **GroupDocs.Merger for Java:** The core library for document manipulation.

### निर्भरता जोड़ना
Maven या Gradle के माध्यम से लाइब्रेरी शामिल करें (कोड ब्लॉकों को जैसा है वैसा रखें):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

आप आधिकारिक साइट से नवीनतम रिलीज़ भी डाउनलोड कर सकते हैं: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### लाइसेंस प्राप्ति
- **Trial license:** Get a temporary key from the [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/) page.  
- **Production license:** Purchase a full license at [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## GroupDocs.Merger for Java सेटअप करना
अपने Java प्रोजेक्ट में लाइब्रेरी को इनिशियलाइज़ करें:

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

पर्यावरण तैयार होने पर, चलिए दो मुख्य तरीकों को देखें जिससे **split docx into files** या स्ट्रीम को विभाजित किया जा सकता है।

## GroupDocs.Merger के साथ DOCX को फ़ाइलों में विभाजित कैसे करें

### दस्तावेज़ को एकल पृष्ठों में विभाजित करें

#### अवलोकन
यह तरीका प्रत्येक चयनित पृष्ठ के लिए एक अलग फ़ाइल बनाता है, जो व्यक्तिगत अनुभागों के वितरण के लिए उपयुक्त है।

#### चरण‑दर‑चरण कार्यान्वयन

**चरण 1 – इनपुट और आउटपुट पाथ निर्दिष्ट करें**  
परिभाषित करें कि मूल DOCX कहाँ स्थित है और विभाजित फ़ाइलें कहाँ सहेजी जानी चाहिए।

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**चरण 2 – SplitOptions कॉन्फ़िगर करें (split options java)**  
लाइब्रेरी को बताएं कि कौन से पृष्ठ निकालने हैं।

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – वह फ़ोल्डर जहाँ प्रत्येक पृष्ठ फ़ाइल रखी जाएगी।  
- `new int[]{3,6,8}` – वे पृष्ठ संख्याएँ जिन्हें आप विभाजित करना चाहते हैं।

**चरण 3 – विभाजन निष्पादित करें**  
`Merger` इंस्टेंस के साथ ऑपरेशन चलाएँ।

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Pro tip:** यह सुनिश्चित करें कि आउटपुट डायरेक्टरी मौजूद है और आपके एप्लिकेशन के पास लिखने की अनुमति है; अन्यथा विभाजन विफल हो जाएगा।

### सामान्य समस्याएँ
- **आउटपुट फ़ोल्डर नहीं है:** API स्वचालित रूप से डायरेक्टरी नहीं बनाता।  
- **गलत पृष्ठ संख्याएँ:** पृष्ठ इंडेक्स 1 से शुरू होते हैं; 0 निर्दिष्ट करने पर त्रुटि होगी।

## DOCX पृष्ठों को स्ट्रीम (इन‑मेमोरी) में विभाजित कैसे करें

### अवलोकन
जब आपको अस्थायी पहुँच की आवश्यकता हो—जैसे वेब सेवा के माध्यम से पृष्ठ भेजना—पृष्ठों को स्ट्रीम के रूप में कैप्चर करने से डिस्क I/O से बचा जा सकता है।

#### चरण‑दर‑चरण कार्यान्वयन

**चरण 1 – इनपुट पाथ निर्धारित करें और स्ट्रीम के लिए सूची तैयार करें**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**चरण 2 – कस्टम SplitStreamFactory के साथ SplitOptions कॉन्फ़िगर करें**  

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```
- `createSplitStream` – प्रत्येक अनुरोधित पृष्ठ के लिए नया `OutputStream` बनाता है।  
- `closeSplitStream` – पूर्ण हुई स्ट्रीम को बाद में उपयोग के लिए संग्रहीत करता है।

**चरण 3 – विभाजन निष्पादित करें और स्ट्रीम प्राप्त करें**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

### समस्या निवारण टिप्स
- सुनिश्चित करें कि स्रोत DOCX पाथ सही है; टाइपो होने पर `FileNotFoundException` उत्पन्न होगा।  
- उपयोग समाप्त होने पर हमेशा स्ट्रीम को बंद करें ताकि मेमोरी मुक्त हो सके।

## व्यावहारिक अनुप्रयोग
1. **Legal contracts:** व्यक्तिगत क्लॉज़ को अलग‑अलग समीक्षा के लिए निकालें।  
2. **E‑learning platforms:** पूरे पाठ्यपुस्तक को उजागर किए बिना अध्याय‑दर‑अध्याय Word फ़ाइलें प्रदान करें।  
3. **Business reporting:** त्रैमासिक रिपोर्ट के केवल वित्तीय भाग को CFO को भेजें।

## प्रदर्शन संबंधी विचार
- **Memory‑efficient streams:** बड़े दस्तावेज़ों (>50 MB) के लिए स्ट्रीम दृष्टिकोण को प्राथमिकता दें।  
- **Batch processing:** कई विभाजन कार्यों को एक ही JVM सत्र में समूहित करें ताकि स्टार्टअप ओवरहेड कम हो।  
- **Resource cleanup:** `merger.close()` कॉल करें और सभी स्ट्रीम को बंद करें ताकि लीक न हो।

## निष्कर्ष
अब आप GroupDocs.Merger for Java का उपयोग करके **how to split docx** फ़ाइलों को अलग‑अलग फ़ाइलों या इन‑मेमोरी स्ट्रीम में विभाजित करना जानते हैं। ये तकनीकें आपको किसी भी व्यावसायिक आवश्यकता के अनुसार दस्तावेज़ वितरण को अनुकूलित करने की लचीलापन देती हैं।

**अगले कदम**
- विभिन्न पृष्ठ रेंज और आउटपुट फ़ॉर्मेट (PDF, HTML, आदि) के साथ प्रयोग करें।  
- विभाजन को मर्जिंग के साथ संयोजित करके ऑन‑द‑फ्लाई कस्टम बंडल पुनः बनाएं।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: GroupDocs.Merger for Java क्या है?**  
A: यह एक Java लाइब्रेरी है जो DOCX, PDF, PPTX आदि सहित विभिन्न दस्तावेज़ फ़ॉर्मेट को मर्ज, स्प्लिट और कनवर्ट करने में सक्षम बनाती है।

**Q: GroupDocs.Merger के लिए लाइसेंस कैसे प्राप्त करें?**  
A: आप मूल्यांकन के लिए [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) से एक अस्थायी ट्रायल लाइसेंस प्राप्त कर सकते हैं। उत्पादन उपयोग के लिए, उसी साइट पर पूर्ण लाइसेंस खरीदें।

**Q: क्या मैं उसी API का उपयोग करके PDF फ़ाइलें भी विभाजित कर सकता हूँ?**  
A: हाँ, `split` मेथड PDF, DOCX, PPTX और अन्य समर्थित फ़ॉर्मेट के साथ काम करता है।

**Q: क्या दस्तावेज़ को डिस्क पर लिखे बिना विभाजित करना संभव है?**  
A: बिल्कुल—ऊपर दिखाए गए स्ट्रीम‑आधारित दृष्टिकोण का उपयोग करके सब कुछ मेमोरी में रखें।

**Q: मुझे कौन सा GroupDocs.Merger संस्करण उपयोग करना चाहिए?**  
A: हमेशा नवीनतम स्थिर रिलीज़ को लक्ष्य बनाएं ताकि प्रदर्शन सुधार और बग फिक्स का लाभ मिल सके।

---

**अंतिम अपडेट:** 2026-02-06  
**परीक्षण किया गया:** GroupDocs.Merger for Java latest-version  
**लेखक:** GroupDocs