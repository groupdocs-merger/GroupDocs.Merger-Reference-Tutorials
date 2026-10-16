---
date: '2026-10-16'
description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
  This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
  tips.
images:
- /java/document-joining/join-pages-groupdocs-merger-java-tutorial/og-image.png
keywords:
- extract and merge pages
- merge documents java
- groupdocs merger java
lastmod: '2026-10-16'
og_description: Learn how to extract and merge pages in Java using GroupDocs.Merger,
  a powerful library that supports over 50 formats and handles large documents efficiently.
og_image_alt: Guide showing how to extract and merge pages in Java with GroupDocs.Merger
og_title: How to extract and merge pages in Java with GroupDocs.Merger
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
title: How to extract and merge pages in Java with GroupDocs.Merger
type: docs
url: /java/document-joining/join-pages-groupdocs-merger-java-tutorial/
weight: 1
---

# How to extract and merge pages in Java with GroupDocs.Merger

In this comprehensive tutorial you’ll discover how to **extract and merge pages** from PDFs, DOCX files, spreadsheets, and many other document types using GroupDocs.Merger for Java. Whether you need to assemble custom brochures, pull chapters from multiple books, or generate a concise report from scattered source files, this guide walks you through the entire process with clear explanations and real‑world examples.

## Quick answers
- **What is the primary use case?** Combine selected pages from PDFs, DOCX, XLSX, PPTX, and other supported formats into a single output file.  
- **Which library handles this?** GroupDocs.Merger for Java.  
- **Do I need a license?** A free trial works for evaluation; a paid license is required for production use.  
- **What Java version is required?** Java 8 or higher.  
- **Can I merge more than two files?** Yes—call `join` repeatedly for each additional source document.

## What is extract and merge pages?
`extract and merge pages` is the process of selecting specific page numbers or ranges from one or more source documents and stitching them together into a new file. This eliminates manual copy‑paste and ensures the resulting document retains the original formatting, fonts, and images.

## Why use GroupDocs.Merger for Java?
GroupDocs.Merger for Java is a versatile library that enables developers to manipulate documents programmatically, offering support for over 50 formats, high‑speed processing, and low memory consumption, making it ideal for server‑side document workflows and large‑scale batch operations in enterprise environments.

- **Format flexibility:** Supports 50+ input and output formats—including PDF, DOCX, PPTX, XLSX, and image files—so you can work with virtually any office document.  
- **Performance‑focused:** Processes only the pages you request, which reduces memory consumption.  
- **Easy integration:** Available via Maven or Gradle, with clear API documentation and no external dependencies.  

## Prerequisites
- Basic Java programming knowledge.  
- Maven or Gradle for dependency management.  
- An IDE such as IntelliJ IDEA or Eclipse.  

## Setting up GroupDocs.Merger for Java

Add the library to your project using one of the following methods.

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

Alternatively, download the latest version directly from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### License acquisition
To unlock all features you’ll need a license. You can start with a free trial or purchase a full license on the [purchase page](https://purchase.groupdocs.com/buy). A temporary license is also available for short‑term evaluation.

## How do I extract and merge pages in Java?
The `Merger` class is the primary API component that creates and manages document merging operations. Load each source document with the `Merger` constructor, specify the exact page numbers you need, and call `join` to combine them. Finally, save the merged result to the desired format. This end‑to‑end flow requires only four method calls and works consistently across all supported file types.

## Step‑by‑step guide to extracting and merging specific pages

### Step 1: initialise the Merger with a primary document
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.PageJoinOptions;

String filePath = YOUR_DOCUMENT_DIRECTORY + "/sample.pdf"; // Source PDF document path
Merger merger = new Merger(filePath);
```

### Step 2: define the pages you want to join
```java
// Specify the page numbers you wish to join (e.g., pages 1 and 2)
PageJoinOptions joinOptions = new PageJoinOptions(1, 2);
```

### Step 3: join selected pages from a second document
```java
// Path to your DOCX file\ String docxFilePath = YOUR_DOCUMENT_DIRECTORY + "/sample.docx";
merger.join(docxFilePath, joinOptions);
```

### Step 4: save the result and release resources
```java
String outputFilePath = YOUR_OUTPUT_DIRECTORY + "/CrossJoinPagesFromVariousDocuments-output.pdf";
merger.save(outputFilePath);

try {
    merger.close();
} catch (Exception e) {
    // Handle exceptions appropriately
}
```

### Step 5 (optional): centralise file paths with constants
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

Using constants makes your code cleaner and simplifies future path changes.

## Practical applications
Here are a few real‑world scenarios where **extract and merge pages** shines:

1. **Document consolidation:** Pull selected chapters from several textbooks into a single PDF for quick review.  
2. **Report generation:** Combine key sections from financial PDFs and Excel‑derived PDFs into one executive summary.  
3. **Research compilation:** Merge excerpts from multiple academic papers (PDF, DOCX) into a single reference document.

## Performance considerations
- **Close the Merger** after you’re done to free native resources.  
- **Select only needed pages** instead of merging whole files; this cuts processing time dramatically.  
- **Handle exceptions** gracefully to avoid crashes when a source file is missing or corrupted.  

## Common issues & solutions
| Issue | Solution |
|-------|----------|
| **`OutOfMemoryError` on large files** | Process pages in smaller batches and close the Merger after each batch. |
| **Unsupported file format** | Verify the format is listed in the GroupDocs.Merger supported formats (PDF, DOCX, XLSX, PPTX, etc.). |
| **License not applied** | Ensure the license file is placed in the application’s root directory or set via `License license = new License(); license.setLicense("path/to/license.lic");`. |

## Frequently asked questions

**Q: Can I merge more than two documents?**  
A: Yes, simply call `merger.join()` repeatedly for each additional source file.

**Q: What file types does GroupDocs.Merger support?**  
A: It supports PDF, DOCX, DOC, PPTX, PPT, XLSX, XLS, and many other common office formats—over 50 in total.

**Q: How do I extract pages from a document without merging?**  
A: Use the `extract` method with `PageExtractOptions` to save selected pages as a new file. This is covered under the **extract pages java** use case.

**Q: Is there a limit to the number of pages I can join?**  
A: The library imposes no hard cap; practical limits depend on your system’s memory and CPU.

**Q: Can I generate dynamic output file names?**  
A: Absolutely—concatenate timestamps or UUIDs to the filename using `PathConstants.getOutputFilePath()` or custom logic.

## Resources
- [Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [Purchase a License](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

Explore these links to deepen your expertise and troubleshoot any challenges you encounter.

---

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Merger for Java latest-version  
**Author:** GroupDocs

## Related Tutorials

- [Extract Pages Groupdocs Merger Java Guide](/merger/java/document-extraction/extract-pages-groupdocs-merger-java-guide/)
- [Merge PDF Java: Efficiently Merge PDFs Using GroupDocs.Merger for Java – A Step-by-Step Guide](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [Move Pages Java – Document Page Operations Tutorials for GroupDocs.Merger](/merger/java/page-operations/)