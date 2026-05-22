---
date: '2026-02-06'
description: GroupDocs.Merger for Java का उपयोग करके टेक्स्ट फ़ाइल को पंक्तियों के
  आधार पर कैसे विभाजित करें, सीखें। जावा प्रोजेक्ट्स में कुशल दस्तावेज़ विभाजन के
  लिए चरण‑दर‑चरण मार्गदर्शिका।
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: GroupDocs.Merger for Java के साथ फ़ाइल को पंक्तियों द्वारा विभाजित कैसे करें
type: docs
url: /hi/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# How to Split File by Lines Using GroupDocs.Merger for Java

एक बड़े टेक्स्ट फ़ाइल को छोटे, अधिक प्रबंधनीय टुकड़ों में **लाइन‑द्वारा** विभाजित करना एक सामान्य आवश्यकता है जब आप ‑ उदाहरण के लिए ‑ लॉग प्रोसेस करते हैं, बैच‑इम्पोर्ट डेटा, या लंबी रिपोर्ट को पुनः व्यवस्थित करते हैं। इस ट्यूटोरियल में आप सीखेंगे कि **फ़ाइल को लाइनों द्वारा कैसे विभाजित करें** GroupDocs.Merger for Java के साथ, यह समझेंगे कि यह तरीका समय कैसे बचाता है, और एक तैयार‑चलाने‑योग्य कोड नमूना प्राप्त करेंगे।

## Quick Answers
- **“split file by lines” का क्या मतलब है?** यह मूल दस्तावेज़ से प्रत्येक में परिभाषित लाइन नंबर रेंज वाले अलग‑अलग टेक्स्ट फ़ाइलें बनाता है।  
- **कौन सा लाइब्रेरी विभाजन को संभालता है?** GroupDocs.Merger for Java लाइन‑इंटरवल विभाजन के लिए एक सरल API प्रदान करता है।  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए एक फ्री ट्रायल काम करता है; उत्पादन उपयोग के लिए एक स्थायी लाइसेंस आवश्यक है।  
- **क्या मैं कैरेक्टर काउंट के आधार पर विभाजित कर सकता हूँ?** सीधे नहीं — विभाजन से पहले फ़ाइल को पुनः आकार देने के लिए एक प्री‑प्रोसेसिंग स्टेप उपयोग करें।  
- **कौन सा Java संस्करण समर्थित है?** कोई भी Java 8+ रनटाइम संगत है।

## What is “split file by lines”?
फ़ाइल को लाइनों द्वारा विभाजित करना मतलब एक ही टेक्स्ट दस्तावेज़ को कई फ़ाइलों में तोड़ना है, जहाँ प्रत्येक फ़ाइल में लगातार लाइनों की एक विशिष्ट रेंज होती है (उदाहरण के लिए, लाइन्स 1‑3, 4‑6, आदि)। यह तकनीक बैच प्रोसेसिंग, समानांतर विश्लेषण, या केवल पठनीयता सुधारने के लिए आदर्श है।

## Why Use GroupDocs.Merger for Java?
GroupDocs.Merger लो‑लेवल फ़ाइल‑I/O कार्य को एब्स्ट्रैक्ट करता है, जिससे आप बिज़नेस लॉजिक पर ध्यान केंद्रित कर सकते हैं। यह बड़े फ़ाइलों को कुशलता से संभालता है, कई दस्तावेज़ फ़ॉर्मेट को सपोर्ट करता है, और एक साफ़, फ़्लुएंट API प्रदान करता है जो Maven या Gradle बिल्ड्स के साथ आसानी से इंटीग्रेट होता है।

## Prerequisites
- **Java Development Kit (JDK) 8 या उससे ऊपर** – सुनिश्चित करें कि `java` और `javac` आपके PATH में हैं।  
- **GroupDocs.Merger for Java** – लाइब्रेरी को Maven, Gradle, या सीधे डाउनलोड के माध्यम से जोड़ें।  
- **Basic Java knowledge** – आपको क्लासेज़, मेथड्स, और एक्सेप्शन हैंडलिंग में सहज होना चाहिए।

## Setting Up GroupDocs.Merger for Java
नीचे दिए गए किसी एक तरीके से लाइब्रेरी को अपने प्रोजेक्ट में जोड़ें।

**Maven** – इस डिपेंडेंसी को अपने `pom.xml` में पेस्ट करें:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – `build.gradle` में निम्न पंक्ति शामिल करें:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – आप आधिकारिक रिलीज़ पेज से JAR भी डाउनलोड कर सकते हैं: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)।

### License Acquisition
API का पता लगाने के लिए फ्री ट्रायल से शुरू करें। उत्पादन वर्कलोड के लिए, GroupDocs पोर्टल से एक टेम्पररी या फुल लाइसेंस प्राप्त करें।

## How to Split Text File by Lines (Java Implementation)

नीचे एक संक्षिप्त, step‑by‑step walkthrough दिया गया है। प्रत्येक स्टेप कोड ब्लॉक से पहले साधारण भाषा में समझाया गया है, ताकि आप ठीक‑ठीक जान सकें क्या हो रहा है।

### Step 1: Define Source and Output Paths
पहले, लाइब्रेरी को बताएं कि आपका मूल फ़ाइल कहाँ स्थित है और विभाजित भाग कहाँ लिखे जाने चाहिए।
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Step 2: Configure the Split Options
एक `TextSplitOptions` इंस्टेंस बनाएं जो आप चाहते हैं लाइन इंटरवल को वर्णन करता है। `new int[] { 3, 6 }` एरे API को लाइन 3 और लाइन 6 के बाद कट करने को कहता है, जिससे दो भाग बनते हैं: लाइन्स 1‑3 और लाइन्स 4‑6।
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Step 3: Initialise the Merger and Execute the Split
अंत में, `Merger` को स्रोत फ़ाइल के साथ इंस्टैंशिएट करें और आपने जो विकल्प बनाए हैं, उनके साथ `split()` कॉल करें।
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

बस! कॉल पूरा होने के बाद, आप `YOUR_OUTPUT_DIRECTORY` में दो नई फ़ाइलें पाएँगे, प्रत्येक में निर्दिष्ट लाइन रेंज होगी।

## Practical Applications (Why This Matters)
1. **Data Processing Pipelines** – बड़े लॉग फ़ाइलों को छोटे हिस्सों में तोड़ें ताकि **parallel parsing** आसान हो सके।  
2. **Document Management** – एक ही रिपोर्ट को चैप्टर‑लेवल फ़ाइलों में बदलें ताकि वितरण आसान हो।  
3. **Content Segmentation** – बड़े लेख के सेक्शन को लक्षित प्रकाशन प्लेटफ़ॉर्म के लिए तैयार करें।

## Performance Tips
- **Stream‑line I/O** – बहुत बड़े फ़ाइलों के साथ काम करते समय मेमोरी उपयोग कम रखने के लिए `Files.newBufferedReader` को प्राथमिकता दें।  
- **Close Resources** – यद्यपि GroupDocs.Merger अधिकांश क्लीन‑अप संभालता है, किसी भी कस्टम स्ट्रीम को स्पष्ट रूप से बंद करना लीक्स से बचाता है।  
- **Monitor Memory** – गीगाबाइट‑साइज़ फ़ाइलों को विभाजित करना मेमोरी‑इंटेंसिव हो सकता है; आवश्यक होने पर पर्याप्त हीप (`-Xmx2g` या उससे अधिक) आवंटित करें।

## Common Issues and Solutions
| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| `OutOfMemoryError` | बड़ी स्रोत फ़ाइल हीप को ओवरफ़्लो कर देती है। | JVM हीप बढ़ाएँ या छोटे इंटरवल्स के साथ विभाजन करें। |
| `FileNotFoundException` | पाथ गलत है या अनुमतियाँ नहीं हैं। | `filePath` और `filePathOut` को पूर्ण पाथ और लिखने योग्य सुनिश्चित करें। |
| Empty output files | इंटरवल एरे पूरे दस्तावेज़ को कवर नहीं करता। | सुनिश्चित करें कि अंतिम इंटरवल कुल लाइन काउंट के बराबर या उससे अधिक हो। |

## FAQ Section

**Q: क्या मैं फ़ाइलों को लाइन नंबरों के बजाय कैरेक्टर काउंट के आधार पर विभाजित कर सकता हूँ?**  
A: वर्तमान में, GroupDocs.Merger for Java लाइन इंटरवल पर केंद्रित है। हालांकि, आप इस फीचर को उपयोग करने से पहले अपने टेक्स्ट को इच्छित कैरेक्टर काउंट प्रति लाइन के अनुसार प्री‑प्रोसेस कर सकते हैं।

**Q: विभाजन के लिए मैं कितनी इंटरवल्स निर्दिष्ट कर सकता हूँ?**  
A: लाइब्रेरी स्वयं में कोई विशिष्ट सीमा नहीं है; हालांकि, बहुत अधिक विभाजनों से प्रोसेसिंग आवश्यकताओं के कारण प्रदर्शन घट सकता है।

**Q: फ़ाइल विभाजन के दौरान त्रुटियों को कैसे संभालूँ?**  
A: अपने कोड के आसपास try‑catch ब्लॉक्स लागू करें ताकि एक्सेप्शन को प्रभावी रूप से कैच और मैनेज किया जा सके। GroupDocs.Merger विस्तृत त्रुटि संदेश प्रदान करता है जो समस्या निवारण में मदद करते हैं।

**Q: क्या लाइब्रेरी CSV या TSV जैसे अन्य टेक्स्ट‑आधारित फ़ॉर्मेट को सपोर्ट करती है?**  
A: हाँ, चूँकि CSV और TSV प्लेन‑टेक्स्ट फ़ाइलें हैं, वही लाइन‑इंटरवल लॉजिक लागू होता है। इन्हें API में `.txt` फ़ाइलों की तरह ट्रीट करें।

**Q: क्या मैं फ़ोल्डर में कई फ़ाइलों के लिए स्वचालित रूप से विभाजन कर सकता हूँ?**  
A: बिल्कुल। ऊपर दिए गए लॉजिक को एक लूप में रैप करें जो `Files.list(Paths.get("folder"))` पर इटररेट करता है और प्रत्येक फ़ाइल पर समान `TextSplitOptions` लागू करता है।

## Resources
- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase and Licensing:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support Forum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger 23.12 for Java  
**Author:** GroupDocs