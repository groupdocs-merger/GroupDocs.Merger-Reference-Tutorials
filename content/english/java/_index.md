---
title: "How to Split PDF and Merge PDFs with GroupDocs.Merger for Java"
linktitle: "GroupDocs.Merger for Java Tutorials"
weight: 10
url: /java/
description: "Learn how to split PDF and merge PDFs with GroupDocs.Merger for Java – step-by-step guide covering split pdf java, merge pdf java, protect pdf java, and more."
date: 2026-06-16
is_root: true
type: docs
keywords:
- split pdf java
- java combine pdf files
- groupdocs merger for java
- protect pdf java
- merge multiple pdfs java
schemas:
- type: TechArticle
  headline: How to Split PDF and Merge PDFs with GroupDocs.Merger for Java
  description: Learn how to split PDF and merge PDFs with GroupDocs.Merger for Java
    – step-by-step guide covering split pdf java, merge pdf java, protect pdf java,
    and more.
  dateModified: '2026-06-16'
  author: GroupDocs
- type: FAQPage
  questions:
  - question: How do I split PDFs using GroupDocs.Merger in Java?
    answer: Instantiate a `Merger`, call `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`,
      and specify an output folder—each range becomes a separate PDF file.
  - question: Can I merge PDFs and Excel sheets together?
    answer: Yes—GroupDocs.Merger supports cross‑format merging, allowing you to combine
      PDFs with Excel files (`merge excel files java`) into a single PDF output.
  - question: How do I add password protection after merging?
    answer: After calling `merge()`, invoke `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))`
      to encrypt the final document.
  - question: Is it possible to merge PDFs without loading the entire file into memory?
    answer: Enable streaming (`Merger.setStreaming(true)`) to process files in a buffered
      fashion, which dramatically reduces memory consumption for large documents.
  - question: What licensing is required for production use?
    answer: A commercial GroupDocs.Merger license is mandatory for production deployments;
      a free 30‑day trial is available for development and testing.
---

# How to Split PDF and Merge PDFs with GroupDocs.Merger for Java

In modern Java applications, **split pdf java** is a frequent requirement—whether you need to break a massive report into bite‑size chapters or combine several invoices into a single archive. GroupDocs.Merger for Java makes both splitting and merging PDFs (and over 50 other formats) a breeze, delivering high‑performance processing with just a few lines of code. In this tutorial we’ll explore the core API, walk through real‑world scenarios, and point you to deeper tutorials for every document‑processing need you might encounter.

## Quick Answers
- **What is the primary use of GroupDocs.Merger?** Combine, split, and manipulate documents across more than 50 formats, including PDFs, Word, Excel, and images.  
- **Can I split PDFs in Java?** Yes – the API offers a dedicated “split pdf java” method that lets you define page ranges or size‑based splits.  
- **How do I merge multiple PDFs in Java?** Use the `Merger` class with the “merge pdf java” workflow to join files instantly.  
- **Is password protection available after merging?** Absolutely; the “protect pdf java” feature encrypts the result with a password you choose.  
- **Do I need a license for production?** A commercial GroupDocs.Merger license is required for any production deployment; a free trial is available for evaluation.

## What is “how to merge PDFs” with GroupDocs.Merger?
`GroupDocs.Merger for Java` is a library that programmatically combines multiple PDF files (or any supported format) into a single, well‑structured document. It automatically preserves page ordering, metadata, and optional security settings, letting you achieve complex document workflows with minimal code.

## Why use GroupDocs.Merger for Java?
Load your source PDFs, specify the pages you want, and call `merge()`—the API handles the heavy lifting. It delivers **50+ input and output formats**, processes **hundreds of pages per second**, and works in both on‑premises and cloud environments without external dependencies.

## Master Document Manipulation with GroupDocs.Merger

GroupDocs.Merger for Java is a powerful API that enables Java developers to combine, split, and manipulate documents across over 50 popular file formats. Our comprehensive tutorial series provides detailed, step‑by‑step guidance on leveraging the full capabilities of GroupDocs.Merger to streamline your document management workflows.

Whether you need to **merge multiple PDFs**, combine Word documents, join spreadsheets, consolidate presentations, or work with images – these tutorials will help you implement robust document processing features in your Java applications with minimal code.

## What You Can Accomplish with GroupDocs.Merger

- **Merge multiple documents** into a single file while preserving formatting and content integrity.  
- **Join specific pages or ranges** from different source documents.  
- **Split large documents** into smaller, more manageable files.  
- **Manipulate page order** through moving, removing, rotating, or swapping operations.  
- **Protect documents** with password encryption and permissions management.  
- **Extract content** from specific document sections.  
- **Process documents** across numerous formats including PDF, Word, Excel, PowerPoint, and more.

## GroupDocs.Merger for Java Tutorial Categories

### [Document Loading](./document-loading/)
Master the essential first step in document processing. Learn various techniques for loading documents from files, streams, and URLs with proper configuration for different formats.

### [Document Information](./document-information/)
Extract valuable metadata from your documents. These tutorials show you how to access document properties, page counts, and format details for better document management.

### [Document Joining](./document-joining/)
Combine multiple documents seamlessly. Discover how to merge entire files or select specific pages from various sources into a single cohesive document.

### [Format‑Specific Merging](./format-specific-merging/)
Optimize merging operations for particular file types. Learn specialized techniques for joining PDFs, Word documents, Excel spreadsheets, PowerPoint presentations, and more.

### [Advanced Joining Options](./advanced-joining-options/)
Take document merging to the next level. Explore complex joining scenarios with custom page selection, cross‑format merging, and content preservation options.

### [Document Security](./document-security/)
Implement robust protection for your documents. Learn to add, remove, or update passwords, manage permissions, and ensure document confidentiality.

### [Page Operations](./page-operations/)
Gain precise control over document pages. Discover techniques for reordering, rotating, removing, and modifying individual pages within your documents.

### [Document Extraction](./document-extraction/)
Extract specific content from larger documents. Learn how to select and save particular pages or sections as separate files.

### [Document Import](./document-import/)
Enhance documents with external content. These tutorials demonstrate how to import content from various sources, including OLE objects and attachments.

### [Image Operations](./image-operations/)
Process image files effectively. Explore methods for working with images, including merging, converting, and embedding within documents.

### [Document Splitting](./document-splitting/)
Divide documents strategically. Learn techniques for splitting files by page numbers, ranges, or specific criteria to create multiple output documents.

### [Text Operations](./text-operations/)
Manipulate text‑based documents efficiently. Discover approaches for processing text files, including merging, splitting by lines, and format conversion.

### [Licensing](./licensing/)
Set up GroupDocs.Merger properly in your projects. Learn about licensing options, configuration approaches, and deployment considerations.

## Supported File Formats

GroupDocs.Merger for Java supports a wide range of document formats, including:

- **Word Processing**: DOCX, DOC, RTF, ODT, DOTX, DOTM, DOT  
- **Spreadsheets**: XLSX, XLS, XLSM, XLSB, ODS, XLT, XLTX  
- **Presentations**: PPTX, PPT, PPSX, PPS, ODP, POT  
- **Portable Documents**: PDF, XPS  
- **Visio Diagrams**: VSDX, VSDM, VSTX, VSSX, VDX, VSX, VTX  
- **eBooks**: EPUB  
- **Images**: BMP, JPG, PNG, TIFF  
- **Web**: HTML, MHT, MHTML  
- **Text**: TXT, CSV, TSV  
- **And many more!** (over 50 formats total)

## Getting Started

The tutorials in this section follow a practical, code‑first approach with complete examples that you can implement directly in your applications. Each tutorial includes:

- Clear explanation of the feature and its use cases  
- Step‑by‑step implementation instructions  
- Complete code examples with comments (code is provided in the linked sub‑tutorials)  
- Configuration options and alternative approaches  
- Performance considerations and best practices  

Start exploring our tutorials today to unlock the full potential of GroupDocs.Merger for Java in your document processing workflows!

## How to Split PDF Java?

Split a PDF into individual pages or custom ranges in just three lines of Java. Call the `split()` method on a `Merger` instance, pass the source file path, and specify the desired page range or size. The library writes each segment to a separate file while preserving original quality and metadata.

You can also split by size (e.g., 5 MB chunks) or by a list of page numbers, which is ideal for generating chapter‑wise PDFs from a single master document. The operation runs in linear time relative to the number of pages, making it suitable for large‑scale batch processing.

## How to Merge Multiple PDFs Java?

Load each source PDF with `Merger`’s `addDocument()` method, arrange them in the desired order, and invoke `merge()`. The API automatically harmonises page dimensions, updates bookmarks, and consolidates document properties. You can also merge PDFs with other formats—such as Word or Excel—by converting them on the fly, resulting in a single, unified PDF output.

For high‑throughput scenarios, enable streaming mode to avoid loading entire files into memory. This reduces heap usage by up to 80 % when processing documents with hundreds of pages.

## Understanding the Merger Class

The `Merger` class is the core component of GroupDocs.Merger for Java that orchestrates document combination, splitting, and security operations. It exposes fluent methods like `addDocument()`, `split()`, `protect()`, and `merge()` to build concise processing pipelines.

### Key Methods Overview
- `addDocument(String path)`: Queues a source file for later merging.  
- `split(String source, SplitOptions options)`: Divides a document based on page ranges or size limits.  
- `protect(String output, ProtectionOptions options)`: Applies password protection and permission restrictions.  
- `merge(String output)`: Executes the queued operations and writes the final document.

These methods are thread‑safe and can be chained for expressive, readable code.

## Common Issues and Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| **Out‑of‑memory errors on large PDFs** | Loading whole file into memory | Enable streaming mode (`Merger.setStreaming(true)`) or split the file into smaller chunks before merging. |
| **Page orientation mismatch** | Source PDFs have mixed portrait/landscape pages | Use `rotatePage(int pageNumber, RotationAngle angle)` before merging to standardise orientation. |
| **Password‑protected source cannot be opened** | Missing decryption password | Provide the password via `DocumentLoadOptions.setPassword("yourPwd")` when adding the document. |
| **Metadata lost after merge** | Default merge discards custom metadata | Call `setPreserveMetadata(true)` on the `Merger` instance to retain original properties. |

## Frequently Asked Questions

**Q: How do I split PDFs using GroupDocs.Merger in Java?**  
A: Instantiate a `Merger`, call `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`, and specify an output folder—each range becomes a separate PDF file.

**Q: Can I merge PDFs and Excel sheets together?**  
A: Yes—GroupDocs.Merger supports cross‑format merging, allowing you to combine PDFs with Excel files (`merge excel files java`) into a single PDF output.

**Q: How do I add password protection after merging?**  
A: After calling `merge()`, invoke `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))` to encrypt the final document.

**Q: Is it possible to merge PDFs without loading the entire file into memory?**  
A: Enable streaming (`Merger.setStreaming(true)`) to process files in a buffered fashion, which dramatically reduces memory consumption for large documents.

**Q: What licensing is required for production use?**  
A: A commercial GroupDocs.Merger license is mandatory for production deployments; a free 30‑day trial is available for development and testing.

---

**Last Updated:** 2026-06-16  
**Tested With:** GroupDocs.Merger for Java 23.12 (latest at time of writing)  
**Author:** GroupDocs

## Related Tutorials

- [Efficiently Merge PDFs Using GroupDocs.Merger for Java: A Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [How to Merge DOCX Files Easily with GroupDocs.Merger for Java: Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-docx-files-groupdocs-merger-java/)
- [How to Merge PowerPoint Files in Java Using GroupDocs.Merger: A Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-powerpoint-files-java-groupdocs-merger-guide/)
