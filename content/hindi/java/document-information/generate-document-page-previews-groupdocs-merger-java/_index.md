---
date: '2026-01-24'
description: GroupDocs.Merger for Java के साथ पेज प्रीव्यू बनाकर दस्तावेज़ों को कैसे
  प्रीव्यू करें, सीखें—पृष्ठों को छवियों में बदलने का तेज़ तरीका, जो दस्तावेज़ थंबनेल
  निर्माण के लिए उपयोगी है।
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: GroupDocs.Merger for Java के साथ दस्तावेज़ों का पूर्वावलोकन कैसे करें
type: docs
url: /hi/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java के साथ दस्तावेज़ प्रीव्यू कैसे करें

दस्तावेज़ पेज प्रीव्यू बनाना एक शक्तिशाली तरीका है **how to preview documents** को जल्दी से करने का, जिससे उपयोगकर्ताओं को पूरी फ़ाइल खोले बिना एक दृश्य स्नैपशॉट मिलता है। इस ट्यूटोरियल में आप सीखेंगे कि Group pages एप्लिकेशन में **document thumbnail generation** को सपोर्ट करती है।

## त्वरित उत्तर
- **What does “preview documents” mean?** प्रत्येक पेज की हल्की इमेज प्रतिनिधित्व बनाना।  
- **Which format is used for previews?** डिफ़ॉल्ट रूप से JPEG, लेकिन अन्य फ़ॉर्मेट भी समर्थित हैं।  
- **Do I need a license?** विकास के लिए एक फ्री ट्रायल काम करता है; प्रोडक्शन के लिए पेड लाइसेंस आवश्यक है।  
- **Can I customize the output path?** हाँ, एक कस्टम `PageStreamFactory` को इम्प्लीमेंट करके।  
- **What Java version is required?** JDK 8 या उसके बाद का संस्करण।

## “how to preview documents” क्या है?
दस्तावेज़ का प्रीव्यू बनाना मतलब प्रत्येक पेज के लिए दृश्य थंबनेल (आमतौर पर JPEG या PNG) बनाना है ताकि उपयोगकर्ता सामग्री को जल्दी से स्किम कर सकें। यह तकनीक दस्तावेज़ प्रबंधन सिस्टम, पोर्टल और किसी भी एप्लिकेशन में उपयोगकर्ता अनुभव को बेहतर बनाती है जो कई फ़ाइलों को संभालता है।

## GroupDocs.Merger for Java क्यों उपयोग करें?
- **Fast conversion** पेज को इमेज में तेज़ी से बदलना बिना UI में पूरी दस्तावेज़ खोले।  
- **Built‑in support** कई फ़ॉर्मेट्स (PDF, DOCX, XLSX, आदि) के लिए।  
- **Extensible API** आपको यह नियंत्रित करने देता है कि प्रीव्यू फ़ाइलें कहाँ और कैसे सेव हों।  

## पूर्वापेक्षाएँ
- **GroupDocs.Merger for Java** लाइब्रेरी (नीचे इंस्टॉलेशन देखें)।  
- **JDK 8+** आपके मशीन पर इंस्टॉल होना चाहिए।  
- एक IDE (IntelliJ IDEA, Eclipse, NetBeans) और डिपेंडेंसी मैनेजमेंट के लिए Maven या Gradle।  

## GroupDocs.Merger for Java सेटअप करना
अपने पसंदीदा बिल्ड टूल का उपयोग करके लाइब्रेरी को अपने प्रोजेक्ट में जोड़ें।

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

**Direct Download:**  
वैकल्पिक रूप से, नवीनतम संस्करण [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) से डाउनलोड करें।

### लाइसेंस प्राप्ति
- **Free Trial:** फीचर एक्सप्लोर करने के लिए फ्री ट्रायल डाउनलोड करके शुरू करें।  
- **Temporary License:** विकास के दौरान विस्तारित एक्सेस के लिए एक टेम्पररी लाइसेंस प्राप्त करें।  
- **Purchase:** पूर्ण प्रोडक्शन उपयोग के लिए, [GroupDocs](https://purchase.groupdocs.com/buy) से लाइसेंस खरीदें।

लाइब्रेरी जोड़ने के बाद, उसे उस दस्तावेज़ के पाथ के साथ इनिशियलाइज़ करें जिसे आप प्रीव्यू करना चाहते हैं:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## दस्तावेज़ प्रीव्यू कैसे करें: चरण‑दर‑चरण गाइड

### चरण 1: Merger को इनिशियलाइज़ करें और एक PageStreamFactory परिभाषित करें
`PageStreamFactory` लाइब्रेरी को बताता है कि प्रत्येक प्रीव्यू इमेज कहाँ लिखी जाए।

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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

### चरण 2: प्रीव्यू जेनरेट करें
आपके द्वारा कॉन्फ़िगर किए गए विकल्पों के साथ `generatePreview` मेथड को कॉल करें।

```java
merger.generatePreview(previewOption);
```

### पेज को इमेज में बदलें – कस्टम PageStreamFactory
यदि आपको फ़ाइल नामकरण या स्टोरेज लोकेशन पर अधिक नियंत्रण चाहिए, तो अपना खुद का फ़ैक्टरी इम्प्लीमेंट करें:

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

### हेल्पर मेथड्स – स्ट्रीम मैनेजमेंट
ये यूटिलिटी मेथड्स कोड को साफ़ रखते हैं और एक्सेप्शन को सुचारु रूप से हैंडल करते हैं।

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

## दस्तावेज़ थंबनेल जेनरेशन – व्यावहारिक अनुप्रयोग
प्रीव्यू जेनरेट करना विशेष रूप से उपयोगी है:

1. **Document Management Systems** – उपयोगकर्ता फ़ाइलें खोलें बिना स्किम कर सकते हैं।  
2. **Content Review Platforms** – अपलोड को स्वीकृति देने से पहले तेज़ विज़ुअल चेक।  
3. **Educational Tools** – छात्र लेक्चर स्लाइड्स या टेक्स्टबुक पेज को जल्दी देख सकते हैं।  

## प्रदर्शन संबंधी विचार
- **Release streams promptly** मेमोरी मुक्त करने के लिए स्ट्रीम्स को तुरंत रिलीज़ करें।  
- **Avoid loading whole documents** को मेमोरी में लोड करने से बचें; लाइब्रेरी को पेजिंग संभालने दें।  
- **Use appropriate image quality** सेटिंग्स का उपयोग करके गति और विज़ुअल फ़िडेलिटी के बीच संतुलन रखें।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: What is GroupDocs.Merger for Java used for?**  
A: यह दस्तावेज़ों को प्रभावी रूप से मर्ज, स्प्लिट और मैनेज करने के लिए उपयोग किया जाता है, जिसमें प्रीव्यू जेनरेशन भी शामिल है।

**Q: How do I handle exceptions during stream operations?**  
A: स्ट्रीम निर्माण और बंद करने को try‑catch ब्लॉक्स में रैप करें, जैसा कि हेल्पर मेथड्स में दिखाया गया है।

**Q: Can I generate previews in formats other than JPEG?**  
A: हाँ, `PreviewMode` एन्‍यूम को PNG, BMP आदि में बदलकर अपनी आवश्यकता के अनुसार उपयोग कर सकते हैं।

**Q: What are common issues with document preview generation?**  
A: सामान्य समस्याओं में गलत फ़ाइल पाथ और स्ट्रीम्स को बंद न करना शामिल है, जिससे मेमोरी लीक्स हो सकते हैं।

**Q: How can I integrate GroupDocs.Merger with other systems?**  
A: उसके API का उपयोग करके डेटाबेस, वेब सर्विसेज या अन्य Java एप्लिकेशन के साथ कनेक्ट करें, जिससे वर्कफ़्लो ऑटोमेशन सहज हो।

## अतिरिक्त संसाधन
- [Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Purchase](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-01-24  
**Tested With:** GroupDocs.Merger latest version (2025‑latest)  
**Author:** GroupDocs