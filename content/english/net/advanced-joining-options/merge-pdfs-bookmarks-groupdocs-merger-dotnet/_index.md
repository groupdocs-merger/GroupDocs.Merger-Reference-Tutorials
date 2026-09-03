---
date: '2026-08-20'
description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
  including setup, code examples, and best practices for combining PDF documents.
images:
- /net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/og-image.png
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for
  .NET. Follow step‑by‑step code to combine PDF documents while preserving navigation.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
type: docs
url: /net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# How to merge pdfs with bookmarks using GroupDocs.Merger for .NET

Merging several PDF files while keeping their original bookmarks intact can save you hours of manual re‑organization. In this tutorial you’ll learn how to **merge pdfs with bookmarks** using GroupDocs.Merger for .NET, from project setup to a complete, production‑ready code sample.

## Quick answers
- **Which library supports bookmark‑preserving merges?** GroupDocs.Merger for .NET.  
- **Can I merge more than two PDFs at once?** Yes – add as many source files as you need.  
- **Do I need a license for development?** A free trial works for testing; a permanent license is required for production.  
- **Is .NET Core supported?** Absolutely – the library works with .NET Core, .NET 5/6 and the full .NET Framework.  
- **What’s the biggest file size it can handle?** Up to 2 GB per document, processed without loading the entire file into memory.

## What is merge pdfs with bookmarks?
**Merging pdfs with bookmarks** means taking several PDF documents and combining them into a single file while keeping each source document’s bookmark hierarchy intact. The resulting PDF retains the original navigation structure, allowing readers to jump directly to the sections that originated from each individual file, which is essential for large reports or compiled manuals.

## Why merge pdfs with bookmarks?
Preserving bookmarks when merging PDFs improves navigation in consolidated documents, letting users quickly locate specific chapters or sections without scrolling through the entire file. GroupDocs.Merger maintains the original outline hierarchy, reduces manual re‑organization effort, and supports large files up to 2 GB while using minimal memory, making it ideal for enterprise‑scale workflows.

## Prerequisites
- **.NET Core SDK** (3.1 or later) or **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** or any IDE that supports .NET development.  
- Basic C# knowledge and familiarity with file I/O.  

## Setting up GroupDocs.Merger for .NET

### Installation
Add the library to your project with one of the following commands:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Search for “GroupDocs.Merger” and install the latest version.

### License acquisition
- **Free trial:** Download from the [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) page.  
- **Temporary license:** Get one via the [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Full license:** Purchase at the [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Basic initialization
The `Merger` class is the entry point for all merging operations.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
This namespace gives you access to the full set of PDF manipulation features.

## How to merge pdfs with bookmarks in .NET

Load your primary PDF, configure bookmark handling, add additional files, and save the result – all in a few concise lines of code.

**Direct answer (40‑70 words):**  
Create a `Merger` instance with the first PDF, enable `PdfJoinOptions.UseBookmarks`, add each subsequent PDF via `Join`, and call `Save` to write the combined file. This approach preserves every original bookmark hierarchy and runs in a single pass, minimizing memory consumption.

### Step 1: define directory paths
Set up source and output folders so the code can locate the PDFs you want to merge.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Step 2: load the primary PDF
`Merger` represents the main document you’ll append others to.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Step 3: configure bookmark‑preserving options
`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag tells the engine to keep existing bookmarks.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Step 4: add additional PDFs
Call `Join` for each extra file. The library automatically merges their bookmark trees under the main document’s outline.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Step 5: save the merged PDF
Specify the output path and format; the library writes a single PDF that retains all bookmark entries.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Common issues and solutions
- **Missing bookmarks:** Verify `UseBookmarks = true` in `PdfJoinOptions`.  
- **Path errors:** Use `Path.Combine` and check file existence before merging.  
- **Large files cause memory spikes:** Process PDFs sequentially and dispose of the `Merger` object after each save.

## Practical applications
1. **Consolidating financial reports** – keep quarterly sections instantly reachable via bookmarks.  
2. **Course material packages** – merge lecture PDFs while preserving chapter navigation for students.  
3. **Project documentation bundles** – combine design specs, test plans, and release notes into a single, searchable file.

## Performance considerations
- Process one file at a time when merging more than 20 PDFs to keep RAM usage low.  
- Use the latest .NET runtime (e.g., .NET 6) for optimal JIT compilation and garbage‑collection efficiency.  
- For PDFs larger than 500 MB, enable streaming mode via `MergerSettings` to avoid loading the whole document into memory.

## Frequently asked questions

**Q: What is GroupDocs.Merger?**  
A: GroupDocs.Merger is a .NET library that lets you merge, split, rotate, and otherwise manipulate PDF and other document formats programmatically.

**Q: Can I merge more than two PDF files at a time?**  
A: Yes – call `Join` repeatedly or pass a collection of file paths to merge any number of PDFs in one operation.

**Q: How do I handle licensing for production use?**  
A: Obtain a permanent license from the GroupDocs purchase page; the trial license works only for evaluation and expires after 30 days.

**Q: My merged PDF shows no bookmarks—what went wrong?**  
A: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source PDF actually contains bookmarks before merging.

**Q: Is the library compatible with .NET Core and .NET Framework?**  
A: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework 4.6.1+.

## Resources
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**Last Updated:** 2026-08-20  
**Tested With:** GroupDocs.Merger 23.11 for .NET  
**Author:** GroupDocs

## Related Tutorials

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)