---
date: 2026-08-10
description: GroupDocs.Merger for .NET के साथ PDF फ़ाइलों को कैसे विभाजित किया जाए,
  सीखें। C# ट्यूटोरियल्स आपको बड़े PDF को विभाजित करने, पृष्ठों को निकालने, और छवियों
  को PDF में कुशलतापूर्वक संयोजित करने में मार्गदर्शन करेंगे।
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: GroupDocs.Merger for .NET ट्यूटोरियल्स
og_description: GroupDocs.Merger for .NET के साथ PDF फ़ाइलों को कैसे विभाजित किया
  जाए, सीखें। C# ट्यूटोरियल्स आपको बड़े PDF को विभाजित करने, पृष्ठों को निकालने, और
  छवियों को PDF में कुशलतापूर्वक संयोजित करने में मार्गदर्शन करेंगे।
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: GroupDocs.Merger for .NET के साथ PDF को विभाजित करने का गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  headline: How to split PDF with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  name: How to split PDF with GroupDocs.Merger for .NET
  steps:
  - name: load the PDF document
    text: Create a `PdfDocument` instance by passing the file path or a stream. The
      constructor reads the document header without loading all pages into memory.
  - name: split by page range
    text: Use the `Split` method, providing a `PageRange` object that defines the
      start and end pages. The method returns a collection of new `PdfDocument` objects,
      each representing the requested segment.
  - name: save the resulting files
    text: Iterate over the split documents and call `Save` with a unique file name.
      You can also apply compression or password protection before saving.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then use `Split` or
      `Extract` as you would with an unprotected file.
    question: Can I split a password‑protected PDF?
  - answer: There is no hard limit; the library streams pages, so you can split PDFs
      with thousands of pages as long as you have sufficient disk space for the output
      files.
    question: How many pages can I split at once?
  - answer: It supports cross‑format merging, allowing you to combine PPTX slides
      with PDF pages into a single PDF output.
    question: Does GroupDocs.Merger support merging PowerPoint files with PDFs?
  - answer: Enable streaming mode (`PdfLoadOptions.Stream = true`) to keep memory
      usage low while splitting or extracting pages.
    question: What is the recommended way to handle very large PDFs?
  - answer: Yes. Use the `Bookmarks` collection to identify chapter start pages and
      programmatically call `Split` for each range.
    question: Is there a way to automate splitting of every chapter in a PDF?
  type: FAQPage
tags:
- split PDF
- GroupDocs.Merger
- C# document processing
- PDF manipulation
- document merging
title: GroupDocs.Merger for .NET के साथ PDF को कैसे विभाजित करें
type: docs
url: /hi/net/
weight: 10
---

# PDF को GroupDocs.Merger for .NET के साथ कैसे विभाजित करें

## GroupDocs.Merger के साथ उन्नत दस्तावेज़ प्रबंधन

`GroupDocs.Merger for .NET` एक .NET लाइब्रेरी है जो डेवलपर्स को 50 से अधिक फ़ाइल फ़ॉर्मैट्स में दस्तावेज़ों को संयोजित, विभाजित और संशोधित करने में सक्षम बनाती है। यदि आपको **PDF को कैसे विभाजित करें** जानना है, तो यह गाइड GroupDocs.Merger for .NET का उपयोग करके सटीक चरण दिखाता है, वास्तविक परिदृश्यों और सर्वोत्तम प्रैक्टिस टिप्स के साथ।

## त्वरित उत्तर

- **PDF को एकल पृष्ठों में कैसे विभाजित करें?** Call `PdfDocument.Split` with a page‑range of `1‑1` for each page.  
- **क्या मैं केवल विशिष्ट पृष्ठ निकाल सकता हूँ?** Yes – pass the desired page numbers to `Split` or `Extract`.  
- **क्या पासवर्ड सुरक्षा समर्थित है?** Absolutely; use `PdfDocument.Protect` before saving.  
- **इमेज को PDF में कैसे संयोजित करें?** Load each image as a `PdfPage` and add them to a new document.  
- **बड़े PDF के बारे में क्या?** Use streaming mode to avoid loading the whole file into memory.

## PDF को कैसे विभाजित करें क्या है?

**PDF को कैसे विभाजित करें** उस प्रक्रिया को दर्शाता है जिसमें एक बहु‑पृष्ठ PDF फ़ाइल को अलग‑अलग, छोटे PDF दस्तावेज़ों में तोड़ा जाता है—या तो व्यक्तिगत पृष्ठों, पृष्ठ रेंजों, या कस्टम मानदंडों द्वारा—प्रोग्रामेटिक APIs का उपयोग करके। यह आमतौर पर सेक्शन को अलग करने, फ़ाइल आकार घटाने, या वितरण के लिए दस्तावेज़ तैयार करने के लिए उपयोग किया जाता है। यह ऑपरेशन प्रोग्रामेटिक रूप से GroupDocs.Merger जैसी लाइब्रेरीज़ के माध्यम से किया जा सकता है, जो सटीक पृष्ठ रेंज और आउटपुट सेटिंग्स निर्दिष्ट करने के लिए मेथड्स प्रदान करती हैं।

## PDF विभाजन के लिए GroupDocs.Merger का उपयोग क्यों करें?

GroupDocs.Merger **55+** इनपुट और आउटपुट फ़ॉर्मैट्स को प्रोसेस करता है, **2 GB** तक के PDF को बिना पूरी मेमोरी लोड किए संभालता है, और सामान्य सर्वर पर 500‑पृष्ठ PDF को **3 सेकंड** से कम समय में विभाजित कर सकता है। ये मापी गई प्रदर्शन संख्याएँ इसे उच्च‑थ्रूपुट दस्तावेज़ पाइपलाइन के लिए एक विश्वसनीय विकल्प बनाती हैं।

## GroupDocs.Merger के साथ PDF फ़ाइलों को कैसे विभाजित करें?

PdfDocument वह मुख्य क्लास है जो GroupDocs.Merger के भीतर PDF फ़ाइल का प्रतिनिधित्व करता है। PDF को विभाजित करने के लिए, पहले स्रोत फ़ाइल को एक PdfDocument इंस्टेंस में लोड करें, फिर Split मेथड का उपयोग करके उन पृष्ठों को निर्दिष्ट करें जिन्हें आप निकालना चाहते हैं। यह मेथड प्रत्येक सेगमेंट के लिए अलग‑अलग PdfDocument ऑब्जेक्ट लौटाता है, जिन्हें आप फिर व्यक्तिगत रूप से सहेज सकते हैं। यह तरीका किसी भी दस्तावेज़ आकार के लिए काम करता है और केवल कुछ लाइनों के कोड की आवश्यकता होती है।

### चरण 1: PDF दस्तावेज़ लोड करें

फ़ाइल पाथ या स्ट्रीम पास करके एक `PdfDocument` इंस्टेंस बनाएं। कंस्ट्रक्टर दस्तावेज़ हेडर को पढ़ता है बिना सभी पृष्ठों को मेमोरी में लोड किए।

### चरण 2: पृष्ठ रेंज द्वारा विभाजित करें

`Split` मेथड का उपयोग करें, जिसमें एक `PageRange` ऑब्जेक्ट प्रदान किया जाता है जो प्रारंभ और समाप्ति पृष्ठों को परिभाषित करता है। यह मेथड नए `PdfDocument` ऑब्जेक्ट्स का संग्रह लौटाता है, प्रत्येक अनुरोधित सेगमेंट का प्रतिनिधित्व करता है।

### चरण 3: परिणामी फ़ाइलें सहेजें

विभाजित दस्तावेज़ों पर इटरेट करें और एक अनूठे फ़ाइल नाम के साथ `Save` को कॉल करें। आप सहेजने से पहले संपीड़न या पासवर्ड सुरक्षा भी लागू कर सकते हैं।

## इमेज को PDF में कैसे संयोजित करें?

PdfDocument GroupDocs.Merger में नई PDF फ़ाइलें बनाने के लिए मुख्य क्लास है। इमेज को संयोजित करने के लिए, प्रत्येक इमेज फ़ाइल को लोड करें और AddPage मेथड का उपयोग करके एक नए PdfDocument इंस्टेंस में एक नया पृष्ठ जोड़ें। सभी इमेज जोड़ने के बाद, दस्तावेज़ को सहेजें, जो मूल रिज़ॉल्यूशन को बनाए रखता है और जब फ़ॉर्मैट अनुमति देता है तो इमेज को वेक्टर‑आधारित पृष्ठों के रूप में एम्बेड करता है। इससे सभी प्रदान की गई इमेज वाले उच्च‑गुणवत्ता वाले PDF बनते हैं।

## PDF को पासवर्ड से कैसे सुरक्षित करें?

PdfDocument वह ऑब्जेक्ट है जो PDF दस्तावेज़ का प्रतिनिधित्व करता है और सुरक्षा सुविधाएँ प्रदान करता है। PdfDocument को लोड या बनाते बाद, उसके Protect मेथड को उपयोगकर्ता पासवर्ड और वैकल्पिक अनुमति फ़्लैग्स (जैसे प्रिंटिंग या कॉपी करना) के साथ कॉल करें। यह मेथड फ़ाइल को एन्क्रिप्ट करता है, और जब आप बाद में Save कॉल करते हैं, तो परिणामी PDF केवल उन उपयोगकर्ताओं द्वारा खोला जा सकता है जो पासवर्ड जानते हैं, जिससे गोपनीयता सुनिश्चित होती है।

## PDF से पृष्ठ कैसे निकालें?

PdfDocument GroupDocs.Merger में PDF फ़ाइल का प्रतिनिधित्व करने वाली मुख्य क्लास है। पृष्ठ निकालने के लिए, स्रोत फ़ाइल के साथ एक PdfDocument इंस्टैंसिएट करें, फिर Extract मेथड को कॉल करें, जिसमें आप उन पृष्ठ संख्याओं की सूची पास करें जिन्हें आप रखना चाहते हैं। यह मेथड केवल उन पृष्ठों को शामिल करने वाला नया PdfDocument लौटाता है, जिसे आप फिर एक अलग PDF के रूप में सहेज सकते हैं। यह तकनीक कस्टम रिपोर्ट बनाने या विशिष्ट सेक्शन साझा करने में उपयोगी है।

## PowerPoint प्रस्तुतियों को कैसे मिलाएँ?

Merge GroupDocs.Merger द्वारा प्रदान किया गया एक मेथड है जो कई दस्तावेज़ों को एकल आउटपुट फ़ाइल में जोड़ता है। PowerPoint प्रस्तुतियों को मिलाने के लिए, प्रत्येक .pptx फ़ाइल को एक Document ऑब्जेक्ट के रूप में लोड करें, फिर एक नए PdfDocument या PresentationDocument पर Merge मेथड को कॉल करें, जिसमें स्रोत दस्तावेज़ों का संग्रह पास किया जाए। लाइब्रेरी स्लाइड एनीमेशन, ट्रांज़िशन और फ़ॉर्मैटिंग को बनाए रखती है, जिससे एक संयुक्त प्रस्तुति बनती है जिसे PDF या PPTX के रूप में सहेजा जा सकता है।

## बड़े PDF पृष्ठों को कैसे विभाजित करें?

PdfLoadOptions.Stream एक प्रॉपर्टी है जो स्ट्रीमिंग मोड को सक्षम करती है, जिससे GroupDocs.Merger बड़े PDF फ़ाइलों को पूरी दस्तावेज़ को मेमोरी में लोड किए बिना प्रोसेस कर सकता है। बहुत बड़े PDF के साथ काम करते समय, फ़ाइल लोड करने से पहले PdfLoadOptions.Stream को true सेट करें। यह मेमोरी उपयोग को कम करता है और आपको पृष्ठों को कुशलतापूर्वक विभाजित या निकालने देता है, यहाँ तक कि 1 GB से बड़ी फ़ाइलों के लिए भी, जबकि प्रदर्शन बनाए रहता है।

## मुख्य विशेषताएँ और क्षमताएँ

- **Merge multiple documents** 55+ फ़ॉर्मैट्स में एकल सुसंगत फ़ाइल में मर्ज करें
- **Join specific pages or page ranges** विभिन्न स्रोत दस्तावेज़ों से विशिष्ट पृष्ठों या पृष्ठ रेंजों को जोड़ें
- **Split documents** पृष्ठ संख्याओं, रेंजों, या सम/विषम पृष्ठ मानदंडों द्वारा विभाजित करें
- **Manipulate page order** स्थानांतरित, हटाने, घुमाने, या बदलने के कार्यों के माध्यम से नियंत्रित करें
- **Secure documents** पासवर्ड सुरक्षा और सूक्ष्म अनुमति नियंत्रणों के साथ सुरक्षित करें
- **Extract specific pages** नई, लक्षित दस्तावेज़ बनाने के लिए निकालें
- **Process 55+ formats** PDF, Office, इमेज, और आर्काइव सहित 55+ फ़ॉर्मैट्स को एकीकृत API के साथ प्रोसेस करें

## GroupDocs.Merger for .NET ट्यूटोरियल श्रेणियाँ

### [फ़ाइलों को मर्ज और संपीड़ित करें](./merge-compress-files/)
7z, TAR, और ZIP जैसी आर्काइव फ़ॉर्मैट्स को कुशलतापूर्वक मर्ज और संपीड़ित करना सीखें। हमारे ट्यूटोरियल आपको GroupDocs.Merger for .NET के साथ आर्काइव को संयोजित करने के लिए पूर्ण C# उदाहरणों के साथ मार्गदर्शन करते हैं।

### [इमेज मर्जिंग](./image-merging/)
BMP, GIF, PNG, SVG, TIFF और अन्य इमेज फ़ॉर्मैट्स को मर्ज करने की तकनीकों में निपुण बनें। गुणवत्ता और फ़ॉर्मैटिंग को बनाए रखते हुए इमेज को एकल दस्तावेज़ में कैसे संयोजित करें, यह जानें।

### [डॉक्यूमेंट मर्जिंग](./document-merging/)
DOC, DOCX, PDF, RTF, और विभिन्न दस्तावेज़ फ़ॉर्मैट्स को एकीकृत फ़ाइलों में संयोजित करें। ये ट्यूटोरियल दस्तावेज़ मर्जिंग परिदृश्यों को विस्तृत कार्यान्वयन चरणों और सर्वोत्तम प्रैक्टिस के साथ कवर करते हैं।

### [स्प्रेडशीट मर्जिंग](./spreadsheet-merging/)
Excel फ़ाइलों (XLAM, XLS, XLSX, XLSM, XLTX) और अन्य स्प्रेडशीट फ़ॉर्मैट्स को डेटा इंटेग्रिटी, फ़ॉर्मूले, और फ़ॉर्मैटिंग बनाए रखते हुए मर्ज करें, इन चरण‑दर‑चरण गाइड्स के साथ।

### [विज़ियो मर्जिंग](./visio-merging/)
Visio डायग्राम और ड्रॉइंग्स (VDX, VSDM, VSDX, VSSM, VSSX) को कुशलतापूर्वक संयोजित करें, हमारे विशेष ट्यूटोरियल्स के साथ जो .NET एप्लिकेशन्स में डायग्राम दस्तावेज़ प्रबंधन के लिए हैं।

### [प्रेज़ेंटेशन मर्जिंग](./presentation-merging/)
PowerPoint और अन्य प्रेज़ेंटेशन फ़ॉर्मैट्स (PPS, PPSX, PPT, OTP) को स्लाइड्स, एनीमेशन, और फ़ॉर्मैटिंग को बनाए रखते हुए मर्ज करना सीखें, पूर्ण कोड उदाहरणों के साथ।

### [डॉक्यूमेंट लोडिंग](./document-loading/)
फ़ाइलों, स्ट्रीम्स, और URLs से दस्तावेज़ लोड करने के विभिन्न तरीकों की खोज करें, विभिन्न फ़ॉर्मैट्स के लिए उचित कॉन्फ़िगरेशन के साथ। दस्तावेज़ प्रोसेसिंग में आवश्यक पहला कदम में निपुण बनें।

### [डॉक्यूमेंट जानकारी](./document-information/)
दस्तावेज़ों से मूल्यवान मेटाडेटा निकालें, जिसमें फ़ॉर्मैट विवरण, पृष्ठ गिनती, और प्रॉपर्टीज़ शामिल हैं। प्रोसेसिंग से पहले प्रोग्रामेटिक रूप से दस्तावेज़ों का विश्लेषण करना सीखें।

### [डॉक्यूमेंट जॉइनिंग](./document-joining/)
उन्नत जॉइनिंग तकनीकों के साथ कई फ़ाइलों को सहजता से संयोजित करें। हमारे ट्यूटोरियल दिखाते हैं कि सामग्री और संरचना पर सटीक नियंत्रण के साथ दस्तावेज़ों को कैसे मर्ज करें।

### [फ़ॉर्मैट‑विशिष्ट मर्जिंग](./format-specific-merging/)
विशिष्ट फ़ाइल फ़ॉर्मैट्स के लिए अनुकूलित मर्जिंग ऑपरेशन्स की खोज करें। विभिन्न दस्तावेज़ प्रकारों के लिए विशेष तकनीकों को सीखें ताकि सर्वोत्तम परिणाम प्राप्त हो सकें।

### [उन्नत जॉइनिंग विकल्प](./advanced-joining-options/)
जटिल पृष्ठ चयन, क्रॉस‑फ़ॉर्मैट मर्जिंग, और कंटेंट प्रिज़र्वेशन रणनीतियों को कवर करने वाले इन उन्नत ट्यूटोरियल्स के साथ दस्तावेज़ मर्जिंग को अगले स्तर पर ले जाएँ।

### [डॉक्यूमेंट सुरक्षा](./document-security/)
अपने दस्तावेज़ों के लिए मजबूत सुरक्षा लागू करें। पासवर्ड जोड़ना, हटाना, और अपडेट करना, अनुमतियों का प्रबंधन, और अपने एप्लिकेशन्स में दस्तावेज़ गोपनीयता सुनिश्चित करना सीखें।

### [पेज ऑपरेशन्स](./page-operations/)
डॉक्यूमेंट पेजों पर सटीक नियंत्रण में निपुण बनें, क्रम बदलने, घुमाने, हटाने, और व्यक्तिगत पेजों को संशोधित करने के ट्यूटोरियल्स के साथ, कस्टमाइज़्ड डॉक्यूमेंट मैनेजमेंट के लिए।

### [डॉक्यूमेंट एक्सट्रैक्शन](./document-extraction/)
इन विस्तृत गाइड्स के साथ दस्तावेज़ों से विशिष्ट कंटेंट निकालें। न्यूनतम कोड के साथ विशेष पृष्ठों या सेक्शन को अलग फ़ाइलों के रूप में चुनना और सहेजना सीखें।

### [डॉक्यूमेंट इम्पोर्ट](./document-import/)
OLE ऑब्जेक्ट्स और एम्बेडेड फ़ाइलों सहित बाहरी कंटेंट के साथ दस्तावेज़ों को समृद्ध करें। विभिन्न स्रोतों से कंटेंट इम्पोर्ट करके अपने दस्तावेज़ों को समृद्ध करना सीखें।

### [इमेज ऑपरेशन्स](./image-operations/)
इमेज फ़ाइलों को प्रभावी ढंग से प्रोसेस करें, हमारे व्यापक ट्यूटोरियल्स के साथ जो इमेज मर्जिंग, कन्वर्ज़न, और मैनीपुलेशन तकनीकों को आपके .NET एप्लिकेशन्स में कवर करते हैं।

### [डॉक्यूमेंट स्प्लिटिंग](./document-splitting/)
पृष्ठ संख्याओं, रेंजों, और कस्टम मानदंडों द्वारा दस्तावेज़ विभाजन पर इन ट्यूटोरियल्स के साथ दस्तावेज़ों को बुद्धिमानी से छोटे घटकों में विभाजित करें।

### [टेक्स्ट ऑपरेशन्स](./text-operations/)
TXT, CSV, और अन्य टेक्स्ट फ़ॉर्मैट्स को प्रोसेस करने के हमारे गाइड्स का उपयोग करके टेक्स्ट‑आधारित दस्तावेज़ों के साथ कुशलता से काम करें, जिसमें लाइन‑आधारित विभाजन और मर्जिंग तकनीकें शामिल हैं।

### [लाइसेंसिंग](./licensing/)
सभी डिप्लॉयमेंट परिदृश्यों और वातावरणों को कवर करने वाले हमारे विस्तृत लाइसेंसिंग ट्यूटोरियल्स के साथ अपने प्रोजेक्ट्स में GroupDocs.Merger को सही ढंग से कॉन्फ़िगर करें।

## समर्थित फ़ाइल फ़ॉर्मैट्स

GroupDocs.Merger for .NET **55 से अधिक** लोकप्रिय दस्तावेज़ फ़ॉर्मैट्स का समर्थन करता है, जिसमें शामिल हैं:

- **दस्तावेज़ फ़ॉर्मैट्स**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **स्प्रेडशीट्स**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **प्रेज़ेंटेशन**: PPT, PPTX, PPS, PPSX, ODP
- **इमेज**: BMP, GIF, JPG, PNG, SVG, TIFF
- **डायग्राम**: VDX, VSDX, VSX, VTX, VSTX, VSSX
- **आर्काइव्स**: ZIP, TAR, 7Z
- **और कई और!**

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं पासवर्ड‑सुरक्षित PDF को विभाजित कर सकता हूँ?**  
**उत्तर:** हाँ। पासवर्ड पैरामीटर के साथ दस्तावेज़ लोड करें, फिर `Split` या `Extract` का उपयोग करें जैसे आप अनप्रोटेक्टेड फ़ाइल के साथ करेंगे।

**प्रश्न: मैं एक बार में कितने पृष्ठ विभाजित कर सकता हूँ?**  
**उत्तर:** कोई कठोर सीमा नहीं है; लाइब्रेरी पृष्ठों को स्ट्रीम करती है, इसलिए आप हजारों पृष्ठों वाले PDF को विभाजित कर सकते हैं जब तक आउटपुट फ़ाइलों के लिए पर्याप्त डिस्क स्पेस हो।

**प्रश्न: क्या GroupDocs.Merger PowerPoint फ़ाइलों को PDF के साथ मर्ज करने का समर्थन करता है?**  
**उत्तर:** यह क्रॉस‑फ़ॉर्मैट मर्जिंग का समर्थन करता है, जिससे आप PPTX स्लाइड्स को PDF पृष्ठों के साथ एकल PDF आउटपुट में संयोजित कर सकते हैं।

**प्रश्न: बहुत बड़े PDF को संभालने का अनुशंसित तरीका क्या है?**  
**उत्तर:** स्ट्रीमिंग मोड सक्षम करें (`PdfLoadOptions.Stream = true`) ताकि पृष्ठों को विभाजित या निकालते समय मेमोरी उपयोग कम रहे।

**प्रश्न: क्या PDF में प्रत्येक अध्याय को स्वचालित रूप से विभाजित करने का कोई तरीका है?**  
**उत्तर:** हाँ। `Bookmarks` कलेक्शन का उपयोग करके अध्याय की शुरुआत पृष्ठों की पहचान करें और प्रत्येक रेंज के लिए प्रोग्रामेटिक रूप से `Split` कॉल करें।

**अंतिम अपडेट:** 2026-08-10  
**परीक्षण किया गया संस्करण:** GroupDocs.Merger 23.9 for .NET  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [GroupDocs.Merger for .NET का उपयोग करके PDF फ़ाइलों को कुशलतापूर्वक मर्ज कैसे करें](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [GroupDocs.Merger for .NET के साथ विशिष्ट PDF पृष्ठों को मर्ज कैसे करें: एक व्यापक गाइड](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [GroupDocs.Merger for .NET का उपयोग करके बुकमार्क्स के साथ PDF फ़ाइलों को मर्ज कैसे करें](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)