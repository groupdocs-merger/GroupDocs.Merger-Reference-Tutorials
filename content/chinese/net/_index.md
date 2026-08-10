---
date: 2026-08-10
description: 了解如何使用 GroupDocs.Merger for .NET 拆分 PDF 文件。C# 教程指导您高效拆分大型 PDF、提取页面以及将图像合并为
  PDF。
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: GroupDocs.Merger for .NET 教程
og_description: 了解如何使用 GroupDocs.Merger for .NET 拆分 PDF 文件。C# 教程指导您高效拆分大型 PDF、提取页面以及将图像合并为
  PDF。
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: 如何使用 GroupDocs.Merger for .NET 拆分 PDF – 指南
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
title: 如何使用 GroupDocs.Merger for .NET 拆分 PDF
type: docs
url: /zh/net/
weight: 10
---

# 如何使用 GroupDocs.Merger for .NET 拆分 PDF

## 使用 GroupDocs.Merger 的高级文档管理

`GroupDocs.Merger for .NET` 是一个 .NET 库，能够让开发者合并、拆分和操作超过 50 种文件格式的文档。如果您需要了解 **如何拆分 PDF**，本指南将展示使用 GroupDocs.Merger for .NET 的具体步骤，包含真实场景和最佳实践提示。

## 快速答案
- **如何将 PDF 拆分为单页？** 调用 `PdfDocument.Split` 并为每页使用 `1‑1` 的页范围。  
- **我只能提取特定页面吗？** 可以——将所需的页码传递给 `Split` 或 `Extract`。  
- **是否支持密码保护？** 当然；在保存之前使用 `PdfDocument.Protect`。  
- **如何将图像合并为 PDF？** 将每个图像加载为 `PdfPage` 并添加到新文档中。  
- **大 PDF 怎么处理？** 使用流模式以避免将整个文件加载到内存中。

## 什么是拆分 PDF？
**How to split PDF** 指的是将多页 PDF 文件拆分为独立的、更小的 PDF 文档的过程——可以按单页、页范围或自定义条件进行，使用编程 API 实现。它常用于隔离章节、减小文件大小或为分发准备文档。该操作可以通过诸如 GroupDocs.Merger 的库以编程方式完成，这些库提供了指定精确页范围和输出设置的方法。

## 为什么在 PDF 拆分中使用 GroupDocs.Merger？
GroupDocs.Merger 支持 **55+** 种输入和输出格式，能够在不完整加载到内存的情况下处理高达 **2 GB** 的 PDF，并且在普通服务器上可在 **3 秒** 内拆分 500 页的 PDF。这些量化的性能数据使其成为高吞吐量文档流水线的可靠选择。

## 如何使用 GroupDocs.Merger 拆分 PDF 文件？
PdfDocument 是 GroupDocs.Merger 中表示 PDF 文件的核心类。要拆分 PDF，首先将源文件加载到 PdfDocument 实例中，然后使用 Split 方法指定要提取的页码。该方法返回每个段落的独立 PdfDocument 对象，您可以分别保存。此方法适用于任何文档大小，仅需几行代码。

### 步骤 1：加载 PDF 文档
通过传入文件路径或流来创建 `PdfDocument` 实例。构造函数只读取文档头部，而不会将所有页面加载到内存中。

### 步骤 2：按页范围拆分
使用 `Split` 方法，提供定义起始页和结束页的 `PageRange` 对象。该方法返回一个新的 `PdfDocument` 对象集合，每个对象代表所请求的段落。

### 步骤 3：保存生成的文件
遍历拆分后的文档并使用唯一文件名调用 `Save`。您还可以在保存前应用压缩或密码保护。

## 如何将图像合并为 PDF？
PdfDocument 是在 GroupDocs.Merger 中用于创建新 PDF 文件的主要类。要合并图像，加载每个图像文件并使用 AddPage 方法将其作为新页添加到全新的 PdfDocument 实例中。所有图像添加完毕后，保存文档，保持原始分辨率，并在格式支持时将图像嵌入为基于矢量的页面。这样即可得到包含所有提供图像的高质量 PDF。

## 如何使用密码保护 PDF？
PdfDocument 是表示 PDF 文档并提供安全功能的对象。加载或创建 PdfDocument 后，使用用户密码和可选的权限标志（如打印或复制）调用其 Protect 方法。该方法对文件进行加密，随后调用 Save 时，生成的 PDF 只能由知道密码的用户打开，从而确保机密性。

## 如何从 PDF 中提取页面？
PdfDocument 是 GroupDocs.Merger 中表示 PDF 文件的主要类。要提取页面，使用源文件实例化 PdfDocument，然后调用 Extract 方法，传入要保留的页码列表。该方法返回仅包含这些页面的新 PdfDocument，您可以将其另存为单独的 PDF。此技术适用于创建自定义报告或共享特定章节。

## 如何合并 PowerPoint 演示文稿？
Merge 是 GroupDocs.Merger 提供的用于将多个文档连接为单个输出文件的方法。要合并 PowerPoint 演示文稿，先将每个 .pptx 文件加载为 Document 对象，然后在新的 PdfDocument 或 PresentationDocument 上调用 Merge 方法，传入源文档集合。该库保留幻灯片动画、过渡和格式，生成的合并演示文稿可保存为 PDF 或 PPTX。

## 如何拆分大 PDF 页面？
PdfLoadOptions.Stream 是一个属性，可启用流模式，使 GroupDocs.Merger 在不将整个文档加载到内存的情况下处理大 PDF 文件。处理超大 PDF 时，在加载文件前将 PdfLoadOptions.Stream 设置为 true。这样可降低内存消耗，并能够高效地拆分或提取页面，即使文件大于 1 GB，仍能保持性能。

## 关键特性与功能

- **合并多个文档** 跨 55+ 种格式为单个统一文件
- **从不同源文档中加入特定页面或页范围**
- **拆分文档** 按页码、范围或奇偶页标准
- **操作页面顺序** 通过移动、删除、旋转或交换操作
- **保护文档** 使用密码保护和细粒度权限控制
- **提取特定页面** 以创建新的目标文档
- **处理 55+ 种格式** 包括 PDF、Office、图像和归档文件，使用统一的 API

## GroupDocs.Merger for .NET 教程分类

### [合并压缩文件](./merge-compress-files/)
学习高效合并和压缩 7z、TAR、ZIP 等归档格式。我们的教程将引导您使用 GroupDocs.Merger for .NET 合并归档，并提供完整的 C# 示例。

### [图像合并](./image-merging/)
掌握合并 BMP、GIF、PNG、SVG、TIFF 等图像格式的技术。了解如何在保持质量和格式的前提下将图像合并为单个文档。

### [文档合并](./document-merging/)
将 DOC、DOCX、PDF、RTF 等多种文档格式合并为统一文件。这些教程涵盖文档合并场景，提供详细的实现步骤和最佳实践。

### [电子表格合并](./spreadsheet-merging/)
合并 Excel 文件（XLAM、XLS、XLSX、XLSM、XLTX）及其他电子表格格式，同时保持数据完整性、公式和格式，提供一步步指南。

### [Visio 合并](./visio-merging/)
高效合并 Visio 图表和绘图（VDX、VSDM、VSDX、VSSM、VSSX），我们的专门教程帮助在 .NET 应用中进行图表文档管理。

### [演示文稿合并](./presentation-merging/)
学习合并 PowerPoint 及其他演示稿格式（PPS、PPSX、PPT、OTP），在保留幻灯片、动画和格式的同时提供完整代码示例。

### [文档加载](./document-loading/)
了解从文件、流和 URL 加载文档的各种方法，并为不同格式进行适当配置。掌握文档处理的关键第一步。

### [文档信息](./document-information/)
提取文档的有价值元数据，包括格式详情、页数和属性。学习在处理前以编程方式分析文档。

### [文档合并](./document-joining/)
使用高级合并技术无缝合并多个文件。我们的教程展示如何精确控制内容和结构进行文档合并。

### [特定格式合并](./format-specific-merging/)
探索针对特定文件格式的优化合并操作。学习不同文档类型的专用技术，以获得最佳效果。

### [高级合并选项](./advanced-joining-options/)
通过这些高级教程，将文档合并提升到新水平，涵盖复杂的页面选择、跨格式合并和内容保留策略。

### [文档安全](./document-security/)
为文档实现强大的保护。学习添加、删除、更新密码，管理权限，并在应用中确保文档机密性。

### [页面操作](./page-operations/)
通过教程掌握对文档页面的精确控制，包括重新排序、旋转、删除和修改单个页面，以实现定制化文档管理。

### [文档提取](./document-extraction/)
使用这些详细指南从文档中提取特定内容。学习以最少代码选择并保存特定页面或章节为独立文件。

### [文档导入](./document-import/)
通过外部内容（包括 OLE 对象和嵌入文件）增强文档。学习从各种来源导入内容以丰富文档。

### [图像操作](./image-operations/)
通过我们的综合教程有效处理图像文件，涵盖图像合并、转换和在 .NET 应用中的操作技术。

### [文档拆分](./document-splitting/)
通过这些教程，按页码、范围和自定义条件智能地将文档拆分为更小的组件。

### [文本操作](./text-operations/)
使用我们的指南高效处理基于文本的文档，包括 TXT、CSV 等文本格式的处理，涵盖基于行的拆分和合并技术。

### [授权](./licensing/)
通过我们的详细授权教程，在项目中正确配置 GroupDocs.Merger，涵盖所有部署场景和环境。

## 支持的文件格式

GroupDocs.Merger for .NET 支持 **超过 55** 种流行文档格式，包括：

- **文档格式**：PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **电子表格**：XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **演示文稿**：PPT, PPTX, PPS, PPSX, ODP
- **图像**：BMP, GIF, JPG, PNG, SVG, TIFF
- **图表**：VDX, VSDX, VSX, VTX, VSTX, VSSX
- **归档**：ZIP, TAR, 7Z
- **以及更多！**

## 常见问题

**问：我可以拆分受密码保护的 PDF 吗？**  
答：可以。使用密码参数加载文档，然后像处理未受保护文件一样使用 `Split` 或 `Extract`。

**问：一次可以拆分多少页？**  
答：没有硬性限制；库会流式处理页面，只要有足够的磁盘空间存放输出文件，就可以拆分包含数千页的 PDF。

**问：GroupDocs.Merger 是否支持将 PowerPoint 文件与 PDF 合并？**  
答：支持跨格式合并，允许您将 PPTX 幻灯片与 PDF 页面合并为单个 PDF 输出。

**问：处理超大 PDF 的推荐方法是什么？**  
答：启用流模式（`PdfLoadOptions.Stream = true`），在拆分或提取页面时保持低内存使用。

**问：有没有办法自动拆分 PDF 中的每个章节？**  
答：有。使用 `Bookmarks` 集合识别章节起始页，并以编程方式对每个范围调用 `Split`。

---

**最后更新：** 2026-08-10  
**测试版本：** GroupDocs.Merger 23.9 for .NET  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Merger for .NET 高效合并 PDF 文件](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [如何使用 GroupDocs.Merger for .NET 合并特定 PDF 页面：完整指南](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [如何使用 GroupDocs.Merger for .NET 通过书签合并 PDF 文件](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)