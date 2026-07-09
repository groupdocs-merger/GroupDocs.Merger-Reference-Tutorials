---
date: '2026-07-06'
description: GroupDocs.Merger for Java के साथ समर्थित file types को प्राप्त करना सीखें,
  समर्थित extensions जावा की जाँच करें, और सूची को अपने workflow में एकीकृत करें।
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: GroupDocs.Merger समर्थित फ़ॉर्मेट – Java में प्रकार प्राप्त करें
type: docs
url: /hi/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger समर्थित फ़ॉर्मेट – जावा में प्रकार प्राप्त करें

जावा में विभिन्न प्रकार के दस्तावेज़ फ़ॉर्मेट के साथ काम करना जल्दी ही सिरदर्द बन सकता है यदि आप नहीं जानते कि आपकी लाइब्रेरी वास्तव में कौन से फ़ॉर्मेट सपोर्ट करती है। **GroupDocs.Merger supported formats** आपको एक विश्वसनीय संदर्भ बिंदु प्रदान करता है, जिससे आप अपलोड्स को वैध कर सकते हैं, रनटाइम त्रुटियों से बच सकते हैं, और अधिक स्मार्ट दस्तावेज़‑प्रबंधन पाइपलाइन डिज़ाइन कर सकते हैं। इस ट्यूटोरियल में आप देखेंगे कि GroupDocs.Merger for Java का उपयोग करके समर्थित फ़ाइल प्रकारों की सूची कैसे प्राप्त की जाए, यह क्यों महत्वपूर्ण है, और इस जानकारी को वास्तविक‑दुनिया के अनुप्रयोगों में कैसे शामिल किया जाए।

### त्वरित उत्तर
- **“retrieve supported file types” क्या करता है?**  
  यह GroupDocs.Merger द्वारा प्रोसेस किए जा सकने वाले प्रत्येक दस्तावेज़ फ़ॉर्मेट की सूची लौटाता है।
- **सूची प्रदान करने वाली विधि कौन सी है?**  
  `FileType.getSupportedFileTypes()` from the `com.groupdocs.merger.domain` package.
- **क्या इस विधि को कॉल करने के लिए लाइसेंस आवश्यक है?**  
  प्रोडक्शन उपयोग के लिए ट्रायल या पूर्ण लाइसेंस आवश्यक है; विधि मूल्यांकन मोड में काम करती है।
- **क्या मैं केवल उन एक्सटेंशन के लिए सूची फ़िल्टर कर सकता हूँ जो मुझे चाहिए?**  
  हाँ – लौटाई गई सूची को इटररेट करें और उन एक्सटेंशन को रखें जिनमें आपकी रुचि है।
- **क्या यह ऑपरेशन प्रदर्शन‑भारी है?**  
  नहीं, यह केवल एक स्थैतिक संग्रह को पढ़ता है, इसलिए यह तुरंत चलता है।

## GroupDocs.Merger समर्थित फ़ॉर्मेट क्या हैं?

GroupDocs.Merger **70+** इनपुट और आउटपुट फ़ॉर्मेट का समर्थन करता है—PDF, DOCX, PPTX, XLSX, HTML, और सामान्य इमेज टाइप्स सहित—जिससे आप लगभग किसी भी व्यापारिक दस्तावेज़ के साथ काम कर सकते हैं। लाइब्रेरी की फ़ॉर्मेट टेबल आंतरिक रूप से एक स्थैतिक संग्रह के रूप में संग्रहीत होती है, इसलिए इसे प्राप्त करना O(1) ऑपरेशन है जो कुछ मिलीसेकंड में पूरा हो जाता है, यहाँ तक कि मध्यम हार्डवेयर पर भी।

## जावा में समर्थित एक्सटेंशन कैसे जांचें?

स्टैटिक `FileType.getSupportedFileTypes()` मेथड को कॉल करें, फिर लौटाए गए संग्रह पर लूप करके प्रत्येक एक्सटेंशन पढ़ें। यह एक‑लाइन कॉल आपको एक तैयार‑उपयोग `List<FileType>` देता है जिसे आप फ़िल्टर, डिस्प्ले या बाद में वैधता के लिए स्टोर कर सकते हैं।

## प्रोसेसिंग से पहले समर्थित फ़ाइल प्रकारों को प्राप्त क्यों करें?

सटीक फ़ॉर्मेट सूची जानने से बचने योग्य एक्सेप्शन से बचाव होता है, डिफेंसिव कोडिंग की आवश्यकता कम होती है, और आप उपयोगकर्ताओं को स्पष्ट “अनुमत फ़ाइल प्रकार” संदेश दिखा सकते हैं। यह आपको डायनामिक UI कॉम्पोनेन्ट—जैसे फ़ाइल‑पिकर फ़िल्टर—बनाने में सक्षम बनाता है जो केवल संगत एक्सटेंशन दिखाते हैं, जिससे कुल उपयोगकर्ता अनुभव बेहतर होता है।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:
- **Java Development Kit (JDK):** संस्करण 8 या उससे ऊपर की सिफ़ारिश की जाती है।  
- **Integrated Development Environment (IDE):** IntelliJ IDEA या Eclipse जैसी कोई भी IDE काम करेगी।  
- **GroupDocs.Merger Library:** इस लाइब्रेरी को अपने प्रोजेक्ट डिपेंडेंसीज़ में शामिल करें।  

बुनियादी Java प्रोग्रामिंग अवधारणाओं की परिचितता और Maven या Gradle वातावरण में लाइब्रेरीज़ के साथ काम करने का अनुभव भी लाभदायक है। यदि आप इन टूल्स में नए हैं, तो पहले उनकी डॉक्यूमेंटेशन देखें।

## जावा के लिए GroupDocs.Merger सेटअप

GroupDocs.Merger for Java का उपयोग करने के लिए, लाइब्रेरी को अपने प्रोजेक्ट में Maven, Gradle, या आधिकारिक साइट से सीधे डाउनलोड करके सेटअप करें।

### Maven इंस्टॉलेशन

अपने `pom.xml` फ़ाइल में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle इंस्टॉलेशन

अपने `build.gradle` फ़ाइल में यह लाइन शामिल करें:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### डायरेक्ट डाउनलोड

वैकल्पिक रूप से, नवीनतम संस्करण को यहाँ से डाउनलोड करें: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)।

#### लाइसेंस प्राप्ति चरण
1. **फ़्री ट्रायल:** लाइब्रेरी की सुविधाओं को आज़माने के लिए एक फ़्री ट्रायल शुरू करें।  
2. **अस्थायी लाइसेंस:** यदि आपको बिना सीमाओं के विस्तारित एक्सेस चाहिए तो एक अस्थायी लाइसेंस प्राप्त करें।  
3. **खरीदें:** दीर्घकालिक उपयोग के लिए पूर्ण लाइसेंस खरीदने पर विचार करें।

## बेसिक इनिशियलाइज़ेशन और सेटअप

अपने Java एप्लिकेशन में GroupDocs.Merger को इनिशियलाइज़ करने के लिए आवश्यक क्लासेज़ इम्पोर्ट करें:

```java
import com.groupdocs.merger.domain.FileType;
```

अब, चलिए उस फीचर को लागू करने की ओर बढ़ते हैं जो समर्थित फ़ाइल प्रकारों को प्राप्त करता है।

## FileType क्लास क्या है?

`FileType` क्लास GroupDocs.Merger में एक कोर मॉडल है जो एकल दस्तावेज़ फ़ॉर्मेट का प्रतिनिधित्व करता है, इसके एक्सटेंशन, MIME टाइप, और एक उपयोगकर्ता‑मैत्रीपूर्ण डिस्प्ले नाम को उजागर करता है। आप इस क्लास के साथ तब इंटरैक्ट करते हैं जब आप `FileType.getSupportedFileTypes()` को कॉल करके फ़ॉर्मेट्स की पूरी कैटलॉग प्राप्त करते हैं।

## समर्थित फ़ाइल प्रकारों को कैसे प्राप्त करें?

समर्थित फ़ॉर्मेट्स को प्राप्त करने के लिए, आप बस GroupDocs.Merger लाइब्रेरी द्वारा प्रदान किए गए स्टैटिक मेथड `FileType.getSupportedFileTypes()` को कॉल करते हैं। यह कॉल एक `List<FileType>` लौटाता है जिसमें लाइब्रेरी द्वारा संभाले जा सकने वाले सभी फ़ॉर्मेट शामिल होते हैं। यह ऑपरेशन हल्का है और एप्लिकेशन स्टार्टअप पर या फ़ाइल अपलोड वैधता के समय किया जा सकता है।

### चरण 1: समर्थित फ़ाइल प्रकार प्राप्त करें

पहले `FileType` क्लास से समर्थित फ़ाइल प्रकारों की सूची प्राप्त करें:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

यह मेथड सभी फ़ाइल प्रकारों की एक सूची लौटाता है जो GroupDocs.Merger सपोर्ट करता है।

### चरण 2: समर्थित एक्सटेंशन दिखाएँ

अब प्रत्येक `FileType` ऑब्जेक्ट पर इटररेट करें और उसका एक्सटेंशन प्रिंट करें। यह वह भाग है जहाँ हम **display supported extensions** डेवलपर्स या एंड‑यूज़र्स के लिए दिखाते हैं:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

लूप प्रत्येक समर्थित फ़ाइल प्रकार के माध्यम से जाता है और उसका एक्सटेंशन कंसोल में आउटपुट करता है।

### चरण 3: पुष्टि संदेश

अंत में, सफलतापूर्वक प्राप्ति को दर्शाने वाला एक पुष्टि संदेश आउटपुट करें:

```java
System.out.println("Supported file types retrieved successfully.");
```

## व्यावहारिक अनुप्रयोग

समर्थित फ़ाइल प्रकारों को समझना विभिन्न अनुप्रयोगों के लिए आवश्यक है:
1. **डॉक्यूमेंट मैनेजमेंट सिस्टम:** फ़ाइल प्रकार के आधार पर दस्तावेज़ों को स्वचालित रूप से वर्गीकृत करें।  
2. **फ़ाइल कन्वर्ज़न टूल्स:** फ़ॉर्मेट्स के बीच कन्वर्ट करने से पहले संगतता सुनिश्चित करें।  
3. **मर्जिंग एप्लिकेशन:** त्रुटियों से बचने के लिए मर्ज करने से पहले इनपुट फ़ाइलों को वैध करें।  

क्लाउड स्टोरेज या डॉक्यूमेंट‑प्रोसेसिंग सेवाओं जैसे अन्य सिस्टम्स के साथ इंटीग्रेशन कार्यक्षमता को और बढ़ा सकता है।

## प्रदर्शन संबंधी विचार

जावा में GroupDocs.Merger के साथ काम करते समय निम्नलिखित प्रदर्शन टिप्स पर विचार करें:
- **मेमोरी उपयोग को ऑप्टिमाइज़ करें:** जब ऑब्जेक्ट्स की अब आवश्यकता न हो तो उन्हें डिस्पोज़ करें।  
- **बैच प्रोसेसिंग:** संसाधन खपत को कम करने के लिए फ़ाइलों को बैच में प्रोसेस करें।  
- **असिंक्रोनस ऑपरेशन्स:** नॉन‑ब्लॉकिंग ऑपरेशन्स के लिए असिंक्रोनस मेथड्स का उपयोग करें।  

## सामान्य समस्याएँ और समाधान

- **डिपेंडेंसी समस्याएँ:** सुनिश्चित करें कि Maven या Gradle डिपेंडेंसीज़ सही ढंग से घोषित हैं; संस्करणों का मेल न होने से class‑not‑found एरर हो सकता है।  
- **लाइब्रेरी संस्करण:** नवीनतम GroupDocs.Merger रिलीज़ का उपयोग करें ताकि नए जोड़े गए फ़ॉर्मेट और बग फिक्सेस मिल सकें।  
- **लाइसेंस एरर:** यदि लाइसेंसिंग एक्सेप्शन दिख रहा है, तो पुष्टि करें कि ट्रायल या परमानेंट लाइसेंस फ़ाइल आपके कोड में सही तरीके से रेफ़रेंस की गई है।

## अक्सर पूछे जाने वाले प्रश्न

**Q: GroupDocs.Merger for Java क्या है?**  
A: यह एक Java लाइब्रेरी है जो Microsoft Office की आवश्यकता के बिना विभिन्न दस्तावेज़ फ़ॉर्मेट को मर्ज, स्प्लिट और कन्वर्ट करने में सक्षम बनाती है।

**Q: GroupDocs.Merger के साथ कैसे शुरू करें?**  
A: Maven या Gradle डिपेंडेंसी जोड़ें, ट्रायल या पूर्ण लाइसेंस प्राप्त करें, और सेटअप सेक्शन में दिखाए अनुसार लाइब्रेरी को इनिशियलाइज़ करें।

**Q: क्या मैं GroupDocs.Merger मुफ्त में उपयोग कर सकता हूँ?**  
A: हाँ, मूल्यांकन के लिए एक फ़्री ट्रायल उपलब्ध है; प्रोडक्शन डिप्लॉयमेंट के लिए पूर्ण लाइसेंस आवश्यक है।

**Q: GroupDocs.Merger कौन‑से फ़ाइल प्रकार सपोर्ट करता है?**  
A: `FileType.getSupportedFileTypes()` मेथड का उपयोग करके **70+** समर्थित फ़ॉर्मेट की सूची प्राप्त करें, जिसमें PDF, DOCX, PPTX, XLSX, HTML, और इमेज टाइप्स शामिल हैं।

**Q: असमर्थित फ़ाइल प्रकारों को कैसे हैंडल करें?**  
A: अपलोड को प्रोसेस करने से पहले समर्थित सूची के विरुद्ध वैधता जांचें; असमर्थित फ़ाइलों को रीजेक्ट या पहले कन्वर्ट करें ताकि रनटाइम एरर से बचा जा सके।

**Q: क्या मैं केवल उन एक्सटेंशन को दिखाने के लिए सूची फ़िल्टर कर सकता हूँ जो मुझे चाहिए?**  
A: हाँ। `getSupportedFileTypes()` कॉल करने के बाद सूची को इटररेट करें और केवल इच्छित एक्सटेंशन रखें।

**Q: क्या विकास बिल्ड के लिए लाइसेंस आवश्यक है?**  
A: विकास और टेस्टिंग के लिए ट्रायल लाइसेंस काम करता है; व्यावसायिक प्रोडक्शन उपयोग के लिए पूर्ण लाइसेंस आवश्यक है।

**Q: क्या यह मेथड एप्लिकेशन स्टार्टअप समय को प्रभावित करता है?**  
A: नहीं। समर्थित फ़ाइल‑टाइप सूची स्थैतिक है, इसलिए प्राप्ति लगभग तुंरत होती है।

**Q: क्या नई लाइब्रेरी संस्करणों के साथ सूची बदल सकती है?**  
A: नई रिलीज़ में फ़ॉर्मेट जोड़ या डिप्रिकेट हो सकते हैं; हमेशा नवीनतम संस्करण का उपयोग करें ताकि सबसे अद्यतन सूची मिले।

## संसाधन
- [दस्तावेज़ीकरण](https://docs.groupdocs.com/merger/java/)
- [API रेफ़रेंस](https://reference.groupdocs.com/merger/java/)
- [डाउनलोड](https://releases.groupdocs.com/merger/java/)
- [खरीदें](https://purchase.groupdocs.com/buy)
- [फ़्री ट्रायल](https://releases.groupdocs.com/merger/java/)
- [अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/)
- [सपोर्ट](https://forum.groupdocs.com/c/merger/) 

इन संसाधनों का अन्वेषण करें अधिक विस्तृत जानकारी और सहायता के लिए। Happy coding!

**अंतिम अपडेट:** 2026-07-06  
**परीक्षित संस्करण:** GroupDocs.Merger नवीनतम संस्करण (2026 तक)  
**लेखक:** GroupDocs  

## संबंधित ट्यूटोरियल

- [GroupDocs.Merger for Java: लाइसेंस सेटअप & फ़ाइल अस्तित्व जांच गाइड](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Load Local Document Java Using GroupDocs.Merger – गाइड](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Merge Specific Pages Java – Document Joining ट्यूटोरियल्स for GroupDocs.Merger](/merger/java/document-joining/)