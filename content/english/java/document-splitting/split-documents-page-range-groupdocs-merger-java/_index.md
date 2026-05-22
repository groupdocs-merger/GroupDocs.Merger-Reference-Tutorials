---
title: "Extract Specific Pages with GroupDocs.Merger for Java"
description: "Learn how to extract specific pages and split documents by page range using GroupDocs.Merger for Java, including odd/even page filters."
date: "2026-02-06"
weight: 1
url: "/java/document-splitting/split-documents-page-range-groupdocs-merger-java/"
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
type: docs
---

# Extract Specific Pages with GroupDocs.Merger for Java

Efficiently **extract specific pages** from large PDFs, Word files, or presentations without manual copy‑paste. In this tutorial you’ll see how to split a document by page range, apply filters such as odd/even pages, and generate single‑page files—all with **GroupDocs.Merger for Java**.

## Quick Answers
- **What does “extract specific pages” mean?** It means creating new documents that contain only the pages you select from the source file.  
- **Which formats are supported?** PDF, DOCX, PPTX, and many other popular formats.  
- **Can I filter by odd or even pages?** Yes, using the `RangeMode` option (e.g., `OddPages`).  
- **Do I need a license?** A free trial works for evaluation; a permanent license is required for production.  
- **Is it suitable for large documents?** Yes—split large document sections to keep memory usage low.

## What is extracting specific pages?
Extracting specific pages is the process of taking a subset of pages from a source document and saving them as a new, independent file. This is useful for creating focused reports, sharing contract clauses, or preparing presentation handouts.

## Why use GroupDocs.Merger for Java to split PDFs and Word documents?
- **Unified API** – Works with PDF, Word, PowerPoint, and more, so you don’t need separate tools.  
- **Fine‑grained control** – Choose exact page ranges, odd/even filters, or single‑page splits.  
- **Performance‑focused** – Handles large files efficiently by streaming pages instead of loading the whole document into memory.  

## Prerequisites
- **GroupDocs.Merger for Java** (latest version)  
- **JDK 8+**  
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
To initialize GroupDocs.Merger, create an instance of `Merger` with your document path:
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## How to extract specific pages using GroupDocs.Merger for Java
This section walks you through splitting a document by page range while applying an odd‑page filter.

### Step 1: Define Input and Output Paths
Set the source file and the destination pattern for the split files:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Step 2: Configure Split Options (Range & Filter)
Create a `SplitOptions` object that tells the library which pages to extract and which filter to apply:
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – Destination file name pattern.  
- **3 and 7** – Start and end page numbers (inclusive).  
- **RangeMode.OddPages** – Keeps only odd pages within the range, effectively **extracting specific pages**.

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
If you need each page as an individual PDF, simply set the `RangeMode` to `AllPages` and specify a range that covers the whole document. The same `SplitOptions` class handles this scenario.

## How to split large document efficiently (split large document)
When dealing with very large files, consider splitting them in smaller ranges (e.g., 1‑100, 101‑200) to reduce memory pressure. Close the `Merger` instance after each operation to free resources.

## How to split PDF odd pages (split pdf odd pages)
The example above already demonstrates the `OddPages` filter. Swap `RangeMode.OddPages` with `RangeMode.EvenPages` to extract even pages instead.

## Practical Applications
1. **Document Segmentation** – Break contracts into clause‑level PDFs for easier review.  
2. **Report Management** – Extract a specific chapter or appendix from a lengthy annual report.  
3. **Presentation Preparation** – Isolate individual slides for targeted meetings.  

You can also integrate this logic with databases or content‑management systems to automate workflow pipelines.

## Performance Considerations
- **Memory Management** – Call `merger.close()` (or rely on try‑with‑resources) after processing to release file handles.  
- **Selective Ranges** – Only request the pages you truly need; this minimizes I/O and CPU usage.  

## Conclusion
You now have a clear, step‑by‑step method to **extract specific pages** from any supported document type using GroupDocs.Merger for Java. This capability streamlines your document workflows and empowers you to deliver precisely the content your users need.

### Next Steps
- Experiment with different `RangeMode` values (e.g., `EvenPages`, `AllPages`).  
- Combine splitting with the **merge** functionality to reorder or concatenate extracted pages.  
- Explore the full API for password‑protected documents, watermarks, and more.

## Frequently Asked Questions
**Q: What is GroupDocs.Merger for Java?**  
A: A robust library that enables merging, splitting, and reordering pages across many document formats.

**Q: Can I use GroupDocs.Merger with other programming languages?**  
A: Yes, similar capabilities exist for .NET and C++.

**Q: How do I handle exceptions during document processing?**  
A: Wrap calls in `try‑catch` blocks and inspect `MergerException` for detailed error information.

**Q: Is it possible to split documents without filtering by odd/even pages?**  
A: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split by exact page numbers.

**Q: What are the system requirements for using GroupDocs.Merger?**  
A: Java 8 or higher and a compatible IDE; no additional native dependencies.

## Resources
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download the Library](https://releases.groupdocs.com/merger/java/)
- [Purchase License](https://purchase.groupdocs.com/buy)
- [Free Trial and Temporary License](https://releases.groupdocs.com/merger/java/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger latest version (Java)  
**Author:** GroupDocs  

---