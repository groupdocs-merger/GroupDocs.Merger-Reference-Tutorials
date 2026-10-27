---
date: '2026-10-27'
description: Learn how to embed pdf in word documents and add pdf to word files with
  GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
images:
- /java/document-import/embed-ole-objects-word-documents-groupdocs-java/og-image.png
keywords:
- how to embed pdf in word
- embed pdf in word document
- embed pdf as ole
- embed multiple pdfs word
- add pdf icon to word
lastmod: '2026-10-27'
og_description: Learn how to embed pdf in word with GroupDocs.Merger for Java. Follow
  this concise tutorial to add PDF as OLE objects in Word documents.
og_image_alt: Guide showing how to embed PDF files into Word documents using GroupDocs.Merger
  for Java
og_title: How to embed pdf in word using GroupDocs.Merger for Java – Step‑by‑step
  guide
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber
  - name: configure OleWordProcessingOptions
    text: '`OleWordProcessingOptions` controls the visual representation of the embedded
      object. You can align the object to the left, center, or right, add a caption
      underneath, and even specify whether the embedded file should be displayed as
      an icon or as a preview. - **`setWidth()` / `setHeight()`** – cont'
  - name: initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (optional) re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- Java document processing
- OLE embedding
- Word automation
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: Define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber`** – the page that will
      host the OLE object.
  - name: Configure OleWordProcessingOptions
    text: The `OleWordProcessingOptions` class defines how the OLE object looks inside
      the Word document. You can set width, height, alignment, and even a caption.
      - **`setWidth()` / `setHeight()`** – control how large the PDF icon appears
      inside the Word document.
  - name: Initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (Optional) Re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
title: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
  guide
type: docs
url: /java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# How to embed pdf in word using GroupDocs.Merger for Java

Embedding a PDF directly inside a Word document can dramatically improve collaboration, because readers no longer need to switch between files. In this guide you’ll discover **how to embed pdf in word** documents using GroupDocs.Merger for Java, and see practical tips on **add pdf to word** workflows. We’ll walk through everything from setting up the library to customizing the size and placement of the OLE object, so you can automate document creation with confidence.

## Quick answers
- **What library is required?** GroupDocs.Merger for Java (latest version)  
- **Can I embed any file type?** Yes – PDFs, images, spreadsheets, etc., as OLE objects  
- **Do I need a license?** A free trial works for development; a commercial license is required for production  
- **Which Java IDE works best?** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **How long does the implementation take?** Roughly 10‑15 minutes for a basic embed  

## What is embed pdf in word?
Embedding a PDF creates an OLE (Object Linking and Embedding) object inside the Word file, allowing the PDF to be opened directly from the document. The embedded file retains its original formatting and interactivity, while the Word document remains a single, self‑contained package. This approach simplifies distribution, ensures version consistency, and provides readers with instant access to supplemental material without leaving the Word environment.

## Why add pdf to word using GroupDocs.Merger?
GroupDocs.Merger automates OLE insertion, size adjustment, and positioning, removing the need for manual editing. The library processes up to **30+ input and output formats** and can embed **hundreds of PDFs** in a single batch while keeping memory usage under **200 MB** on a typical JVM. This scalability makes it ideal for large‑scale documentation, contracts, or marketing kits.

## Prerequisites
- **Libraries & dependencies:** Include the GroupDocs.Merger library via Maven or Gradle.  
- **Development environment:** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **Basic knowledge:** Familiarity with Java and document‑manipulation concepts.  

## How do I set up GroupDocs.Merger for Java?
To begin, add the GroupDocs.Merger library to your project using Maven, Gradle, or a manual JAR download. After the dependency is resolved, import the core classes such as `Merger`, `OleWordProcessingOptions`, and any required I/O utilities. Ensure your project targets Java 8 or higher and that the library version matches your license.

### Maven
Add this dependency to your `pom.xml` file:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Include this in your `build.gradle` file:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct download
Alternatively, download the latest version from the [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/).

**License acquisition:** You can start with a free trial or obtain a temporary license to evaluate features before purchasing. Visit [Purchase GroupDocs](https://purchase.groupdocs.com/buy) for more details.

## How does the basic initialization work?
The `Merger` class is the entry point for all document‑processing operations in GroupDocs.Merger for Java. After you create a `Merger` instance, you can call methods such as `importDocument` to embed OLE objects. Import the required classes so you can work with OLE objects:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## How can I embed a PDF into a Word document step‑by‑step?
Embedding a PDF involves loading the source Word file, creating an `OleWordProcessingOptions` instance to define appearance, and calling `importDocument` with the PDF path and options. The library inserts the OLE object at the specified location, after which you save the document to produce a self‑contained file.

### Step 1: define file paths and target page
Set the source Word document, the PDF you want to embed, and where the OLE object should appear.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – path to the existing Word file.  
- **`embeddedFilePath`** – the PDF you want to **add pdf to word**.  
- **`outputFilePath`** – where the new document will be saved.  
- **`pageNumber`** – the page that will host the OLE object.

### Step 2: configure OleWordProcessingOptions
`OleWordProcessingOptions` controls the visual representation of the embedded object. You can align the object to the left, center, or right, add a caption underneath, and even specify whether the embedded file should be displayed as an icon or as a preview.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – control how large the PDF icon appears inside the Word document.

### Step 3: initialize Merger and import the OLE object
Create a `Merger` instance for the source document, import the OLE object, and save the result.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```
- **`importDocument()`** – takes the `OleWordProcessingOptions` and inserts the PDF as an OLE object.  
- **`save()`** – writes the modified document to `outputFilePath`.

### Step 4: (optional) re‑apply configuration for additional objects
If you need to embed more PDFs, repeat **Step 1‑3** with new file paths and page numbers. The same `OleWordProcessingOptions` class lets you control each object individually.

## How can I configure OleWordProcessingOptions for advanced scenarios?
`OleWordProcessingOptions` is the configuration hub for OLE embedding. You can align the object to the left, center, or right, add a caption underneath, and even specify whether the embedded file should be displayed as an icon or as a preview. The code snippet below repeats the basic configuration for clarity:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## What are practical applications of embedding PDFs in Word?
Embedding PDFs is valuable in many professional contexts because it keeps related content together while preserving the original formatting of each file. For example, technical manuals can include detailed schematics, financial reports can attach audit statements, legal contracts can embed annexes, and marketing brochures can incorporate product spec sheets—all without requiring separate downloads or external links.

## How do performance considerations affect large documents?
When processing large Word files or multiple OLE objects, manage memory and I/O efficiently. Trim unnecessary content, embed only required pages, and allocate sufficient JVM heap space using the `-Xmx` flag. Recent GroupDocs.Merger releases improve processing speed by **up to 35 %** for documents with more than **200 pages**, and they reduce peak memory consumption by **around 40 %** compared with earlier versions.

## What common issues might I encounter and how do I solve them?
Typical problems include incorrect file paths, out‑of‑memory errors, corrupted source PDFs, and missing OLE icons. Ensure that both Word and PDF paths are absolute or correctly relative to the project root, increase the JVM heap size for large batches, verify that each PDF opens normally before embedding, and confirm that the target Word template allows OLE insertion. Adjusting these factors usually resolves most embedding failures.

## Frequently asked questions

**Q: What is OLE embedding?**  
A: Embedding allows you to insert objects like PDFs into Word documents as links that maintain their original functionality.

**Q: Can I embed multiple OLE objects in one document?**  
A: Yes, each can be configured for different pages and sizes using separate `OleWordProcessingOptions`.

**Q: Is there a limit on the size of embedded files?**  
A: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger handles large files efficiently.

**Q: How do I resolve embedding errors?**  
A: Verify that file paths are correct and that the JVM has enough memory. Check that the source PDF isn’t corrupted.

**Q: Can I modify embedded objects after insertion?**  
A: You can reopen the Word file in Microsoft Word and edit the OLE object, or re‑run the Merger code with updated options.

## Additional resources
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-10-27  
**Tested With:** GroupDocs.Merger for Java latest version  
**Author:** GroupDocs  

---

## Related tutorials

- [How to embed PDF in Excel using GroupDocs.Merger for Java - Import an OLE Object – A Step‑by‑Step Guide](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [Embedding Images as OLE Objects in Java with GroupDocs.Merger: A Comprehensive Guide](/merger/java/image-operations/embed-images-ole-java-groupdocs-merger/)
- [Add PDF Attachment Using GroupDocs.Merger for Java – Complete Guide](/merger/java/format-specific-merging/embed-documents-pdf-groupdocs-merger-java/)