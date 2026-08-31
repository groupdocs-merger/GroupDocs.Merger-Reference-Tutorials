---
date: 2026-08-31
description: Learn how to extract specific pages pdf using GroupDocs.Merger for .NET.
  Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
images:
- /net/document-extraction/og-image.png
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Learn how to extract specific pages pdf using GroupDocs.Merger for
  .NET. Detailed guides help you pull pages from PDF, Word, and DOCX files efficiently.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: How to extract specific pages pdf with GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: How to extract specific pages pdf with GroupDocs.Merger
type: docs
url: /net/document-extraction/
weight: 9
---

# How to extract specific pages pdf with GroupDocs.Merger

Extracting specific pages pdf is a common requirement when you need to reuse, share, or archive only a portion of a larger document. With GroupDocs.Merger for .NET you can programmatically pull out single pages, page ranges, or custom selections from PDF, Word, and DOCX files without manual editing. This tutorial walks you through the concepts, prerequisites, and step‑by‑step workflow so you can integrate page extraction into any .NET application.

## Quick answers
- **What does “extract specific pages pdf” mean?** It means selecting individual pages or ranges from a PDF (or other supported format) and saving them as a new, smaller document.  
- **Which formats are supported?** GroupDocs.Merger handles over 50 input and output formats, including PDF, DOCX, PPTX, and images.  
- **Do I need a license?** A temporary license works for testing; a full license is required for production use.  
- **Can I process large files?** Yes – the library processes multi‑hundred‑page files using streaming, keeping memory usage low.  
- **Is .NET Core supported?** Absolutely – the API works with .NET Framework 4.6+, .NET Core 3.1+, and .NET 6/7.

## What is extract specific pages pdf?
`extract specific pages pdf` refers to the operation of taking one or more pages from an existing PDF (or supported document) and creating a new PDF that contains only those pages. This allows you to share just the relevant sections while keeping the original file intact.

## Why extract specific pages pdf with GroupDocs.Merger?
GroupDocs.Merger processes up to **50+ file formats** and can extract pages from documents containing **500+ pages** in under **2 seconds** on a typical server‑grade CPU. The API works without requiring Microsoft Office or Adobe Acrobat installed, which reduces deployment complexity and licensing costs.

## Prerequisites
- .NET 6 SDK (or .NET Core 3.1 / .NET Framework 4.6+) installed on your development machine.  
- A valid GroupDocs.Merger for .NET NuGet package (`GroupDocs.Merger`) added to your project.  
- (Optional) A temporary or full license file if you plan to run the code beyond the evaluation period.

## How to extract specific pages pdf in C# with GroupDocs.Merger

Load the source document, specify the pages you need, and save the result. The library abstracts all format‑specific details, so the same code works for PDF, DOCX, PPTX, and more.

Load your source file and call the `Extract` method with the desired page numbers. The `Extract` method creates a new document containing only the specified pages. The method returns a new `Document` object that you can immediately save. A `Document` object represents an in‑memory representation of the resulting file.

### Step 1: create a merger instance
The `Merger` class is the entry point for loading and manipulating documents. Instantiate the `Merger` class by passing the path of the source file. This object represents the document you will work with.

### Step 2: specify pages to extract
Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"` to tell the library which pages to keep.

### Step 3: save the extracted document
Call `Save` on the `Document` object, supplying the output path and desired format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies the output file type, such as PDF. The operation writes a new file containing only the selected pages.

## Common issues and solutions
- **Pages are off‑by‑one:** GroupDocs.Merger uses 1‑based page numbering. Ensure your list starts at 1, not 0.  
- **Password‑protected files:** Pass the password to the `Merger` constructor or use the `LoadOptions` object. `LoadOptions` provides settings that control how a document is loaded, e.g., enabling memory caching.  
- **Large files cause timeouts:** Enable streaming by setting `LoadOptions.UseMemoryCache = true` to keep memory usage low.

## Frequently asked questions

**Q: Can I extract pages from a Word document as PDF?**  
A: Yes – the same `Extract` call works for DOCX, and you can save the result directly as PDF using `SaveFormat.Pdf`.

**Q: Is it possible to extract non‑consecutive pages?**  
A: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range `"1-2,5,8-10"`.

**Q: Does the library support encrypted PDFs?**  
A: Yes. Supply the password when opening the document; the API will decrypt it automatically.

**Q: How does GroupDocs.Merger handle images inside PDFs?**  
A: Images are preserved exactly as they appear on the selected pages; no extra conversion steps are needed.

**Q: What .NET versions are officially supported?**  
A: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.

## Available tutorials

### [Extract specific pages from documents with GroupDocs.Merger for .NET](./extract-pages-groupdocs-merger-net/)
Learn how to efficiently extract specific pages using GroupDocs.Merger for .NET. Ideal for managing Word, PDF, and more in professional environments.

### [How to extract specific pages from a document using GroupDocs.Merger for .NET in C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Learn how to extract specific pages from documents using GroupDocs.Merger for .NET with this comprehensive guide. Streamline your document management tasks effortlessly.

## Additional resources

- [GroupDocs.Merger for .net Documentation](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net API Reference](https://reference.groupdocs.com/merger/net/)
- [Download GroupDocs.Merger for .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-08-31  
**Tested with:** GroupDocs.Merger 23.9 for .NET  
**Author:** GroupDocs

## Related Tutorials

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Merge Specific Pages from Multiple Documents Using GroupDocs.Merger for .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Rotate PDF Pages in .NET Using GroupDocs.Merger: A Step-by-Step Guide](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)