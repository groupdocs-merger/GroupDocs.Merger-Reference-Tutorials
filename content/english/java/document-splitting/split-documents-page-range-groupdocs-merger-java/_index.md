---
date: '2026-07-25'
description: Learn how to split word document pages using GroupDocs.Merger for Java,
  with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
images:
- /java/document-splitting/split-documents-page-range-groupdocs-merger-java/og-image.png
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Learn how to split word document pages using GroupDocs.Merger for
  Java, with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Split Word Document Pages with GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Split Word Document Pages with GroupDocs.Merger for Java
type: docs
url: /java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Split Word Document Pages with GroupDocs.Merger for Java

In this tutorial you’ll learn how to **split word document pages**—and other formats like PDF and PPTX—using GroupDocs.Merger for Java. Whether you need to pull out a single contract clause, generate hand‑outs from a presentation, or break a massive report into manageable chunks, the API lets you specify exact page ranges, odd/even filters, or single‑page outputs with just a few lines of code.

## Quick Answers
- **What does “extract specific pages” mean?** It means creating new documents that contain only the pages you select from the source file.  
- **Which formats are supported?** PDF, DOCX, PPTX, and many other popular formats.  
- **Can I filter by odd or even pages?** Yes, using the `RangeMode` option (e.g., `OddPages`).  
- **Do I need a license?** A free trial works for evaluation; a permanent license is required for production.  
- **Is it suitable for large documents?** Yes—split large document sections to keep memory usage low.

## What is extracting specific pages?
Extracting specific pages means taking a selected subset of pages from an original document and creating a new, independent file that contains only those pages. This technique is valuable for generating focused reports, sharing individual contract clauses, or distributing specific presentation slides without exposing the entire source document.

## Why use GroupDocs.Merger for Java to split PDFs and Word documents?
Load only the pages you need and let GroupDocs.Merger handle the heavy lifting. The library supports **50+ input and output formats**, can process files up to **2 GB** without loading the whole document into memory, and provides a consistent API across PDF, DOCX, PPTX, and more—so you avoid juggling multiple tools.

## Prerequisites
- **GroupDocs.Merger for Java** (latest version)  
- **JDK 8+**  
- An IDE such as IntelliJ IDEA or Eclipse  
- Maven or Gradle for dependency management  

## Setting Up GroupDocs.Merger for Java
Add the library to your project using your preferred build tool.

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download**: You can also download the library directly from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### License Acquisition
You can acquire a license through:
- **Free Trial** – Test full features without limitations.  
- **Temporary License** – Extended evaluation period.  
- **Purchase** – Permanent production license.

**Basic Initialization and Setup**  
The `Merger` class is the entry point for all splitting operations. It represents a document in memory and provides methods to manipulate pages. To initialize GroupDocs.Merger, create an instance of `Merger` with your document path:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## How to extract specific pages using GroupDocs.Merger for Java
To extract specific pages, load the source document with a `Merger` instance, configure a `SplitOptions` object with the desired start and end pages and optionally set `RangeMode` (e.g., `OddPages` or `EvenPages`). Then call `merger.split(options)` which creates new files containing only the selected pages.

### Direct answer
Create a `Merger` instance, configure a `SplitOptions` object with `RangeMode.OddPages` and the desired start/end pages, then call `merger.split(options)`. This one‑step flow extracts only the odd pages within the specified range and writes them to the output pattern you provide.

### Step 1: Define Input and Output Paths
Set the source file and the destination pattern for the split files:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Step 2: Configure Split Options (Range & Filter)
The `SplitOptions` class tells the library which pages to extract and which filter to apply. `RangeMode` is an enumeration that specifies which pages to include, such as odd, even, or all pages. The `filePathOut` property defines the naming pattern, while `startPage` and `endPage` set the inclusive range. `RangeMode.OddPages` keeps only odd pages inside that range, effectively **extracting specific pages**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Step 3: Perform the Split Operation
Execute the split using the configured options:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Troubleshooting Tips
- Verify that the file paths are correct and accessible.  
- Ensure the page numbers are within the document’s total page count; otherwise an exception will be thrown.  

## How to split PDF into single pages (split pdf single pages)
To split a PDF into individual pages, open the file with a `Merger` instance and set `RangeMode.AllPages` in a `SplitOptions` object. Specify an output naming pattern, then invoke `merger.split(options)`. The library will generate one separate PDF file for each page, preserving original content and formatting.

## How to split large document efficiently (split large document)
When processing very large documents, split them in smaller page ranges (e.g., 1‑100, 101‑200) to reduce memory consumption. Create separate `SplitOptions` for each range, run `merger.split(options)` sequentially, and close the `Merger` instance after each batch. This approach keeps CPU and I/O usage manageable.

## How to split PDF odd pages (split pdf odd pages)
To extract only the odd-numbered pages from a PDF, configure a `SplitOptions` object with `RangeMode.OddPages`. Set the desired output pattern and optionally define a page range if you do not need the entire document. Call `merger.split(options)` and the library will produce files containing just the odd pages.

## Practical Applications
1. **Document Segmentation** – Break contracts into clause‑level PDFs for easier review.  
2. **Report Management** – Extract a specific chapter or appendix from a lengthy annual report.  
3. **Presentation Preparation** – Isolate individual slides for targeted meetings.  

You can also integrate this logic with databases or content‑management systems to automate workflow pipelines.

## Performance Considerations
- **Memory Management** – Call `merger.close()` (or rely on try‑with‑resources) after processing to release file handles.  
- **Selective Ranges** – Only request the pages you truly need; this minimizes I/O and CPU usage.  

## Conclusion
You now have a clear, step‑by‑step method to **split word document pages** (and other supported formats) using GroupDocs.Merger for Java. This capability streamlines your document workflows and empowers you to deliver precisely the content your users need.

### Next Steps
- Experiment with different `RangeMode` values (e.g., `EvenPages`, `AllPages`).  
- Combine splitting with the **merge** functionality to reorder or concatenate extracted pages.  
- Explore the full API for password‑protected documents, watermarks, and more.  

## Frequently Asked Questions
**Q: What is GroupDocs.Merger for Java?**  
A: GroupDocs.Merger for Java is a robust library that enables merging, splitting, and reordering pages across many document formats, including PDF, DOCX, and PPTX.

**Q: Can I use GroupDocs.Merger with other programming languages?**  
A: Yes, similar capabilities exist for .NET and C++.

**Q: How do I handle exceptions during document processing?**  
A: `MergerException` is the exception type thrown by GroupDocs.Merger when a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException` for detailed error information.

**Q: Is it possible to split documents without filtering by odd/even pages?**  
A: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split by exact page numbers.

**Q: What are the system requirements for using GroupDocs.Merger?**  
A: Java 8 or higher and a compatible IDE; no additional native dependencies are required.

## Resources
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download the Library](https://releases.groupdocs.com/merger/java/)
- [Purchase License](https://purchase.groupdocs.com/buy)
- [Free Trial and Temporary License](https://releases.groupdocs.com/merger/java/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-07-25  
**Tested With:** GroupDocs.Merger latest version (Java)  
**Author:** GroupDocs

## Related Tutorials

- [Efficiently Remove Pages from Word Documents Using GroupDocs.Merger for Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Master Document Management - Merge Word Documents with GroupDocs.Merger for Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [How to Split Documents into Multi-Page Files Using GroupDocs.Merger for Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)