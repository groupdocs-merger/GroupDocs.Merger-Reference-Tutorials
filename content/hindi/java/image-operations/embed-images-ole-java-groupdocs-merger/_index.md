---
date: '2026-06-26'
description: GroupDocs.Merger for Java का उपयोग करके इमेज को OLE में कैसे बदलें सीखें।
  Step‑by‑step guide, code snippets, और best practices for embedding images as OLE
  objects.
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
title: Java में GroupDocs.Merger के साथ इमेज को OLE में कैसे बदलें
type: docs
url: /hi/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# Java में GroupDocs.Merger का उपयोग करके Image को OLE में कैसे बदलें

दस्तावेज़ में सीधे छवियों को एम्बेड करना झंझटपूर्ण लग सकता है, लेकिन **convert image to OLE** GroupDocs.Merger for Java के साथ आसान हो जाता है। इस ट्यूटोरियल में आप देखेंगे कि OLE ऑब्जेक्ट क्यों उपयोगी हैं, अपने वातावरण को कैसे तैयार करें, और छवि को OLE डायग्राम के रूप में एम्बेड करने के सटीक चरण। अंत तक, आपके पास एक पुन: उपयोग योग्य कोड पैटर्न होगा जो Word, Excel, PowerPoint, और PDF फ़ाइलों में काम करता है।

## त्वरित उत्तर
- **मुख्य मेथड क्या है?** स्रोत दस्तावेज़ लोड करने के बाद `Merger.importOleDiagram()` का उपयोग करें।  
- **क्या मुझे लाइसेंस चाहिए?** डेवलपमेंट के लिए ट्रायल काम करता है; प्रोडक्शन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **कौन से इमेज फ़ॉर्मेट समर्थित हैं?** PNG, JPEG, BMP, GIF, और TIFF सभी स्वीकार किए जाते हैं।  
- **क्या मैं OLE का आकार और स्थिति सेट कर सकता हूँ?** हाँ—`OleDiagramOptions` आपको पेज, कॉर्डिनेट्स, चौड़ाई और ऊँचाई निर्धारित करने देता है।  
- **क्या प्रक्रिया मेमोरी‑कुशल है?** GroupDocs.Merger डेटा को स्ट्रीम करता है, इसलिए 500‑पेज की फ़ाइलें भी 200 MB RAM से कम रहती हैं।  

## “convert image to OLE” क्या है?
**Convert image to OLE** का अर्थ है रास्टर इमेज फ़ाइल को Object Linking and Embedding (OLE) डायग्राम में बदलना जो होस्ट दस्तावेज़ के अंदर संपादित किया जा सकता है। यह परिवर्तन अंतिम उपयोगकर्ताओं को छवि पर डबल‑क्लिक करने, इसे उसके मूल एडिटर में खोलने, और फ़ाइल छोड़े बिना कंटेनर दस्तावेज़ में बदलाव सहेजने की सुविधा देता है।

## OLE एम्बेडिंग के लिए GroupDocs.Merger क्यों उपयोग करें?
GroupDocs.Merger **50+ इनपुट और आउटपुट फ़ॉर्मेट** का समर्थन करता है—जिसमें DOCX, XLSX, PPTX, PDF, और सामान्य इमेज प्रकार शामिल हैं—और **300 MB** तक के दस्तावेज़ों में OLE ऑब्जेक्ट एम्बेड कर सकता है बिना पूरी फ़ाइल को मेमोरी में लोड किए। यह लाइब्रेरी एक सामान्य 2.6 GHz सर्वर पर 200‑पेज की Word फ़ाइल को तीन एम्बेडेड PNGs के साथ **3 सेकंड** से कम समय में प्रोसेस करती है, जिससे आपको गति और स्केलेबिलिटी दोनों मिलती हैं।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK) 8+** आपके IDE में स्थापित और कॉन्फ़िगर किया हुआ।  
- **GroupDocs.Merger for Java** को Maven या Gradle के माध्यम से जोड़ा गया (नवीनतम संस्करण की सिफारिश)।  
- Java I/O स्ट्रीम और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी परिचितता।  

## Java के लिए GroupDocs.Merger सेटअप करना

अपने प्रोजेक्ट में GroupDocs.Merger शामिल करने के लिए, अपनी बिल्ड फ़ाइल में डिपेंडेंसी जोड़ें। लाइब्रेरी Maven Central पर उपलब्ध है, इसलिए आप नीचे दिया गया स्निपेट अपने `pom.xml` या `build.gradle` में कॉपी कर सकते हैं।  

> **Note:** नीचे दिए गए प्लेसहोल्डर मूल ट्यूटोरियल के सटीक कोड ब्लॉक्स को दर्शाते हैं; इन्हें अपरिवर्तित रखें।

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

आप आधिकारिक रिलीज़ पेज से JAR सीधे डाउनलोड भी कर सकते हैं: [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/)।

### लाइसेंस प्राप्ति
- **Free Trial:** प्रोटोटाइपिंग और मूल्यांकन के लिए आदर्श।  
- **Temporary License:** सीमित अवधि के लिए ट्रायल फीचर को विस्तारित करता है।  
- **Full License:** सभी OLE‑संबंधित क्षमताओं को अनलॉक करता है और उपयोग सीमाओं को हटाता है।

डिपेंडेंसी जोड़ने के बाद, आप अपने Java कोड में लाइब्रेरी को इनिशियलाइज़ करने के लिए तैयार हैं।

## Java में Image को OLE में कैसे बदलें?
एक इमेज को OLE ऑब्जेक्ट में बदलने के लिए, `Merger` इंस्टेंस के साथ टार्गेट दस्तावेज़ लोड करें, इमेज फ़ाइल को बाइट एरे में पढ़ें, पेज, पोजीशन और साइज निर्दिष्ट करते हुए `OleDiagramOptions` ऑब्जेक्ट बनाएं, फिर `merger.importOleDiagram(imageBytes, options)` को कॉल करें। अंत में, `merger.save(outputPath)` का उपयोग करके दस्तावेज़ सहेजें। यह वर्कफ़्लो इमेज को एक संपादन योग्य OLE डायग्राम के रूप में एम्बेड करता है।

### चरण 1: फ़ाइल पाथ निर्धारित करें
स्रोत दस्तावेज़ और इमेज के स्थान को निर्दिष्ट करें। प्लेसहोल्डर को अपने मशीन पर वास्तविक पाथ से बदलें:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### चरण 2: इमेज बाइट्स पढ़ें
पूरी इमेज फ़ाइल को बाइट एरे में पढ़ें। यह बाइट एरे OLE पेलोड बन जाता है:

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### चरण 3: OLE डायग्राम विकल्प कॉन्फ़िगर करें
`OleDiagramOptions` GroupDocs को बताता है कि OLE ऑब्जेक्ट को कहाँ और कैसे रखें। यह क्लास **OLE डायग्राम इम्पोर्ट के लिए टॉप‑लेवल विकल्प होल्डर** है; यह आपको पेज नंबर, X/Y कॉर्डिनेट्स, चौड़ाई, और ऊँचाई सेट करने देता है।

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

### चरण 4: Merger को इनिशियलाइज़ करें और OLE डायग्राम इम्पोर्ट करें
`Merger` वह कोर क्लास है जो एक दस्तावेज़ का प्रतिनिधित्व करता है और मैनिपुलेशन के लिए मेथड प्रदान करता है। यह लक्ष्य फ़ाइल के सभी रीड/राइट ऑपरेशन्स को **एनकैप्सुलेट** करता है।

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## संशोधित दस्तावेज़ को सहेजना

एक बार OLE डायग्राम एम्बेड हो जाने पर, आपको बदलावों को डिस्क पर वापस लिखना होगा।

### चरण 1: स्रोत पाथ के साथ Merger को इनिशियलाइज़ करें
एक ही `Merger` इंस्टेंस को पुनः उपयोग करें या संशोधित दस्तावेज़ की ओर इशारा करने वाला नया बनाएं:

```java
Merger merger = new Merger(filePath);
```

### चरण 2: संशोधित दस्तावेज़ को सहेजें
इच्छित आउटपुट लोकेशन के साथ `save` मेथड को कॉल करें। GroupDocs.Merger फ़ाइल को स्ट्रीमिंग फ़ैशन में लिखता है, जिससे मेमोरी उपयोग कम रहता है:

```java
merger.save(outputPath);
```

## व्यावहारिक अनुप्रयोग
छवियों को OLE ऑब्जेक्ट के रूप में एम्बेड करने से कई वास्तविक‑दुनिया के परिदृश्य खुलते हैं:

- **Interactive Reports:** उपयोगकर्ता एम्बेडेड चार्ट पर डबल‑क्लिक करके, उसे Excel में संपादित कर सकते हैं, और तुरंत अपडेटेड विज़ुअल देख सकते हैं।  
- **Automated Document Generation:** वित्त और स्वास्थ्य देखभाल सिस्टम अनुबंधों या रोगी सारांशों में नवीनतम ग्राफिक्स डाल सकते हैं बिना मैन्युअल एडिटिंग के।  
- **Collaboration Platforms:** टीमें एक ही Word फ़ाइल साझा कर सकती हैं जहाँ प्रत्येक सदस्य अपना डायग्राम अपडेट करता है, जिससे संस्करण‑नियंत्रण की समस्याएँ कम होती हैं।  

## प्रदर्शन संबंधी विचार
बड़ी फ़ाइलों को प्रोसेस करते समय अपने एप्लिकेशन को प्रतिक्रियाशील रखने के लिए:

- **Stream Data:** GroupDocs.Merger इनपुट और आउटपुट दोनों को स्ट्रीम करता है, जिससे पूरी फ़ाइल को मेमोरी में लोड करने से बचा जा सके।  
- **Reuse Objects:** कई इम्पोर्ट्स के लिए एक ही `Merger` इंस्टेंस को पुनः उपयोग करने से ऑब्जेक्ट‑क्रिएशन ओवरहेड कम होता है।  
- **Monitor Heap:** 200 MB से बड़ी दस्तावेज़ों के लिए, `OutOfMemoryError` से बचने हेतु JVM हीप (`-Xmx1g`) बढ़ाने पर विचार करें।  

## सामान्य समस्याएँ और समाधान
| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| `Unsupported file format` error | छवि PNG/JPEG/BMP/GIF/TIFF में नहीं है | बाइट्स पढ़ने से पहले छवि को समर्थित फ़ॉर्मेट में बदलें। |
| OLE object appears at the wrong location | `OleDiagramOptions` में गलत `x`/`y` कॉर्डिनेट्स | सुनिश्चित करें कि कॉर्डिनेट्स पॉइंट्स में मापे गए हैं (1 pt ≈ 1/72 in)। |
| Output file is corrupted | इम्पोर्ट के बाद `save()` नहीं बुलाया गया | सभी संशोधनों के बाद `merger.save(outputPath)` को निष्पादित करना सुनिश्चित करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: OLE ऑब्जेक्ट क्या है?**  
A: OLE ऑब्जेक्ट एक एप्लिकेशन (जैसे, इमेज) से डेटा को दूसरे (जैसे, Word फ़ाइल) में एम्बेड करता है, जिससे होस्ट दस्तावेज़ को छोड़े बिना इन‑प्लेस एडिटिंग संभव होती है।

**Q: क्या मैं GroupDocs.Merger को व्यावसायिक प्रोजेक्ट्स के लिए उपयोग कर सकता हूँ?**  
A: हाँ—व्यावसायिक उपयोग के लिए वैध लाइसेंस आवश्यक है। मूल्यांकन के लिए ट्रायल उपलब्ध है, लेकिन प्रोडक्शन डिप्लॉयमेंट्स को लाइसेंस किया जाना चाहिए।

**Q: लाइब्रेरी बहुत बड़ी इमेजेज़ को कैसे संभालती है?**  
A: इमेजेज़ को बाइट एरे में पढ़ा जाता है, लेकिन आप `FileInputStream` का उपयोग करके बड़ी फ़ाइलों को स्ट्रीम कर सकते हैं और मेमोरी उपयोग कम रखने के लिए स्ट्रीम को `importOleDiagram` को पास कर सकते हैं।

**Q: कौन से दस्तावेज़ फ़ॉर्मेट OLE एम्बेडिंग का समर्थन करते हैं?**  
A: DOCX, XLSX, PPTX, और PDF पूरी तरह से समर्थित हैं। PDF के लिए, OLE ऑब्जेक्ट को एम्बेडेड फ़ाइल स्ट्रीम के रूप में संग्रहीत किया जाता है।

**Q: क्या दस्तावेज़ में OLE ऑब्जेक्ट्स की संख्या पर कोई सीमा है?**  
A: व्यावहारिक रूप से कोई नहीं—GroupDocs.Merger कई (दर्जनों) OLE डायग्राम एम्बेड कर सकता है, जो केवल होस्ट दस्तावेज़ के आकार और उपलब्ध मेमोरी पर निर्भर करता है।

## संसाधन
- [GroupDocs.Merger रिलीज़](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Java दस्तावेज़ीकरण](https://docs.groupdocs.com/merger/java/)
- [Java API रेफ़रेंस](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java रिलीज़](https://releases.groupdocs.com/merger/java/)
- [GroupDocs खरीद पेज](https://purchase.groupdocs.com/buy)
- [GroupDocs सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/merger)

## निष्कर्ष
अब आपके पास GroupDocs.Merger for Java का उपयोग करके **convert image to OLE** करने के लिए एक पूर्ण, प्रोडक्शन‑रेडी वर्कफ़्लो है। फ़ाइल पाथ निर्धारित करके, इमेज बाइट्स पढ़कर, `OleDiagramOptions` कॉन्फ़िगर करके, और `importOleDiagram` को कॉल करके आप किसी भी समर्थित दस्तावेज़ को इंटरैक्टिव ग्राफ़िक्स से समृद्ध कर सकते हैं। अतिरिक्त APIs—जैसे मर्जिंग, स्प्लिटिंग, और वाटरमार्किंग—का अन्वेषण करें ताकि एक पूर्ण‑फ़ीचर वाला दस्तावेज़ प्रोसेसिंग पाइपलाइन बना सकें।

---

**अंतिम अपडेट:** 2026-06-26  
**परीक्षित संस्करण:** GroupDocs.Merger 23.10 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [GroupDocs.Merger for Java का उपयोग करके Excel में PDF एम्बेड करने का तरीका - OLE ऑब्जेक्ट इम्पोर्ट – चरण‑दर‑चरण गाइड](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [GroupDocs.Merger for Java का उपयोग करके Word में PDF एम्बेड करने का तरीका – व्यापक गाइड](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [GroupDocs.Merger for Java का उपयोग करके PNG इमेजेज़ को मर्ज करने का तरीका - चरण‑दर‑चरण गाइड](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)