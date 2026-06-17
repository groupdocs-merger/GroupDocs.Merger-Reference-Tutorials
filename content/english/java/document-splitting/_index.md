---
title: "Create Single Page PDF with GroupDocs.Merger Java"
description: "Learn how to create single page PDF files and split PDFs using GroupDocs.Merger for Java. Includes step-by-step guides for split pdf java and more."
weight: 12
date: 2026-05-22
url: "/java/document-splitting/"
type: docs
keywords:
  - create single page pdf
  - docx to pdf java
  - split pdf java
  - pdf split by range
  - split pdf odd even
schemas:
- type: TechArticle
  headline: Create Single Page PDF with GroupDocs.Merger Java
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  dateModified: '2026-05-22'
  author: GroupDocs
- type: HowTo
  name: Create Single Page PDF with GroupDocs.Merger Java
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
- type: FAQPage
  questions:
  - question: Can I split a password‑protected PDF?
    answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
  - question: How do I split only the odd pages of a PDF?
    answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
  - question: Is it possible to split a DOCX directly into PDFs?
    answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
  - question: What formats does GroupDocs.Merger support for splitting?
    answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
  - question: Do I need a separate license for each file type?
    answer: No. A single GroupDocs.Merger license covers all supported formats.
---

# Create Single Page PDF with GroupDocs.Merger Java

If you need to **create single page PDF** files from larger documents or simply split PDFs into more manageable pieces, you’ve come to the right place. This guide walks you through the most common splitting scenarios—multi‑page files, page ranges, odd/even pages, DOCX splitting, and even text‑based splits—using the powerful GroupDocs.Merger library for Java. By the end of this tutorial you’ll know exactly how to integrate these techniques into your own applications, improve document handling performance, and keep your codebase clean and maintainable.

## Quick Answers
- **What does “create single page PDF” mean?** It means extracting one page from a source document and saving it as an independent PDF file.  
- **Which library handles the job?** GroupDocs.Merger for Java provides a fluent API for all splitting operations.  
- **Do I need a license?** A temporary license works for development; a full license is required for production.  
- **Can I split PDF odd and even pages?** Yes—GroupDocs.Merger lets you filter pages by odd/even numbers.  
- **Is DOCX splitting supported?** Absolutely; you can split DOCX files page‑by‑page or by custom ranges.  

## What is “create single page PDF”?
Creating a single‑page PDF involves taking a multi‑page source document (PDF, DOCX, PPTX, etc.) and extracting just one page into its own PDF file. This is useful for generating invoices, certificates, or preview images where only a specific page is required.

## Why use GroupDocs.Merger for Java?
GroupDocs.Merger for Java offers a single, consistent API that handles many document formats while delivering high performance and low memory usage. It simplifies development by abstracting complex file handling, allowing you to focus on business logic rather than low‑level processing details.

- **Unified API** – Works with PDF, DOCX, PPTX, images, and many other formats.  
- **High performance** – Optimized for large files and batch operations; it can process documents up to 2 GB without loading the entire file into memory.  
- **Fine‑grained control** – Split by page range, odd/even pages, or custom delimiters.  
- **Stream‑friendly** – Output can be saved to a file or returned as a stream for web services.

## Prerequisites
- Java 8 or newer.  
- GroupDocs.Merger for Java added to your project (Maven/Gradle).  
- A valid (temporary or full) GroupDocs license file.

## How to create single page PDF?
Creating a single‑page PDF with GroupDocs.Merger involves loading the source file, specifying the exact page or range, invoking the split operation, and finally persisting the result. This workflow ensures the original document remains untouched while the extracted page is saved as an independent PDF file.

The `Merger` class is the core component that loads source documents and provides split functionality.

### Step 1: Initialize the Merger
The `Merger` class is GroupDocs.Merger's core component that loads a source document and provides split operations. Create an instance by passing the file path or an input stream.

### Step 2: Define the split criteria
Choose the exact page number or range you need. For a single‑page extraction, you’ll specify a range like `1‑1`. When you need to **split pdf by range**, you can pass multiple ranges such as `1‑5, 6‑10`.

### Step 3: Execute the split
Call the appropriate `split` method. For example, `merger.split(new int[]{1})` extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})` handles multiple ranges in one call.

### Step 4: Save the result
Write each output to a file path or return it as a `java.io.InputStream`. This makes it easy to integrate with web APIs or store the result in cloud storage.

> **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)` before splitting to reduce memory consumption.

## How to split PDF java files into multiple pages
The `Merger` class provides the primary API for loading and manipulating PDF files. To divide a PDF into separate one‑page files, you simply load the document with the Merger instance and call the split method without parameters. The library automatically creates a new PDF for each page, preserving original content and metadata, which is ideal for batch processing of invoices or reports.

## How to split PDF odd even pages
The `Merger` class is the core component that performs split operations on documents. When you need only odd or even pages from a PDF, provide a list of the desired page numbers to the split function. The Merger will generate a new document containing just those pages, allowing you to quickly create separate files for odd‑numbered or even‑numbered content.

## How to split docx files (how to split docx)
The `Merger` class also works with DOCX files. Use `splitByPage` to generate one DOCX (or PDF) per page, or combine it with `saveAsPdf` if you need PDF output. This covers the **docx to pdf java** conversion workflow in a single step.

## How to split documents into multi‑page files
The `Merger` class handles pagination and file creation for split operations. If you prefer to break a large document into fixed‑size chunks, specify the number of pages per output file. The Merger will iterate through the source, creating new PDFs each containing the defined page count, which simplifies archiving, distribution, and parallel processing of extensive documents.

## Available Tutorials

### [How to Split Documents into Multi-Page Files Using GroupDocs.Merger for Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Learn how to efficiently split large documents into smaller, multi-page files using GroupDocs.Merger for Java. Optimize document management with ease.

### [How to Split a Text File by Line Intervals Using GroupDocs.Merger for Java | Document Splitting Guide](./split-text-file-line-intervals-groupdocs-merger-java/)
Learn how to split text files into manageable sections using line intervals with GroupDocs.Merger for Java. A comprehensive guide for efficient document handling.

### [Master Document Splitting by Page Range with GroupDocs.Merger for Java](./split-documents-page-range-groupdocs-merger-java/)
Learn how to split documents into specific page ranges using GroupDocs.Merger for Java. Streamline document management and apply filters like odd/even pages.

### [Master Document Splitting with GroupDocs.Merger&#58; A Comprehensive Guide](./master-document-splitting-groupdocs-merger-java/)
Learn how to efficiently split documents into single pages using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

### [Master Java Document Splitting with GroupDocs.Merger&#58; Split DOCX Pages into Files and Streams](./master-java-document-splitting-groupdocs-merger/)
Learn how to efficiently split DOCX documents into separate pages or streams using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

## Additional Resources

- [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API Reference](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Common Issues and Solutions
| Issue | Solution |
|-------|----------|
| **Memory overload on large PDFs** | Enable resource optimization: `merger.setOptimizeResources(true);` |
| **Incorrect page numbers after splitting** | Remember that page indexing starts at 1, not 0. |
| **License not found** | Verify the path to your `GroupDocs.Merger.lic` file and ensure it’s included in the classpath. |
| **Splitting DOCX results in empty pages** | Ensure the source DOCX has proper page breaks; otherwise, use `splitByParagraph` as a fallback. |

## Frequently Asked Questions

**Q: Can I split a password‑protected PDF?**  
A: Yes. Load the document with the password parameter, then perform any split operation as usual.

**Q: How do I split only the odd pages of a PDF?**  
A: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the `split` method.

**Q: Is it possible to split a DOCX directly into PDFs?**  
A: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.

**Q: What formats does GroupDocs.Merger support for splitting?**  
A: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).

**Q: Do I need a separate license for each file type?**  
A: No. A single GroupDocs.Merger license covers all supported formats.

---

**Last Updated:** 2026-05-22  
**Tested With:** GroupDocs.Merger 23.11 for Java  
**Author:** GroupDocs

## Related Tutorials

- [split pdf java: Document Splitting with GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Master Document Splitting by Page Range with GroupDocs.Merger for Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Efficiently Merge PDFs Using GroupDocs.Merger for Java: A Step‑by‑Step Guide](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
