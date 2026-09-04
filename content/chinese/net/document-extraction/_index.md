---
date: 2026-08-31
description: 了解如何使用 GroupDocs.Merger for .NET 提取特定页面 PDF。分步指南涵盖 Word、PDF 和 DOCX 的提取场景。
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: 了解如何使用 GroupDocs.Merger for .NET 提取特定页面 PDF。详细指南帮助您高效地从 PDF、Word 和
  DOCX 文件中提取页面。
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: 使用 GroupDocs.Merger 提取特定页面 PDF 的方法
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
title: 使用 GroupDocs.Merger 提取特定页面 PDF 的方法
type: docs
url: /zh/net/document-extraction/
weight: 9
---

# 如何使用 GroupDocs.Merger 提取特定页面的 PDF

提取特定页面的 PDF 是在需要复用、共享或仅归档大型文档的一部分时的常见需求。使用 GroupDocs.Merger for .NET，您可以以编程方式从 PDF、Word 和 DOCX 文件中提取单页、页码范围或自定义选择，而无需手动编辑。本教程将带您了解概念、先决条件以及逐步工作流程，帮助您在任何 .NET 应用程序中集成页面提取功能。

## 快速答案
- **“提取特定页面的 PDF” 是什么意思？** 它指的是从 PDF（或其他受支持的格式）中选择单个页面或范围，并将其保存为一个新的、更小的文档。  
- **支持哪些格式？** GroupDocs.Merger 支持超过 50 种输入和输出格式，包括 PDF、DOCX、PPTX 和图像。  
- **我需要许可证吗？** 临时许可证可用于测试；生产环境需要正式许可证。  
- **我可以处理大文件吗？** 可以——库使用流式处理多百页文件，保持低内存占用。  
- **支持 .NET Core 吗？** 完全支持——API 可在 .NET Framework 4.6+、.NET Core 3.1+ 和 .NET 6/7 上运行。

## 什么是提取特定页面的 PDF？
`extract specific pages pdf` 指的是从现有 PDF（或受支持的文档）中取出一个或多个页面，并创建仅包含这些页面的新 PDF 的操作。这使您能够仅共享相关章节，同时保持原始文件完整。

## 为什么使用 GroupDocs.Merger 提取特定页面的 PDF？
GroupDocs.Merger 支持处理超过 **50 种文件格式**，并且能够在典型服务器级 CPU 上在 **2 秒** 内从包含 **500+ 页** 的文档中提取页面。该 API 无需安装 Microsoft Office 或 Adobe Acrobat，即可工作，从而降低部署复杂性和许可证成本。

## 先决条件
- .NET 6 SDK（或 .NET Core 3.1 / .NET Framework 4.6+）已在开发机器上安装。  
- 已在项目中添加有效的 GroupDocs.Merger for .NET NuGet 包（`GroupDocs.Merger`）。  
- （可选）如果计划在评估期后运行代码，需要临时或正式许可证文件。

## 如何在 C# 中使用 GroupDocs.Merger 提取特定页面的 PDF

加载源文档，指定所需页面，并保存结果。库抽象了所有特定格式的细节，因此相同的代码可用于 PDF、DOCX、PPTX 等。

加载源文件并使用所需的页码调用 `Extract` 方法。`Extract` 方法会创建仅包含指定页面的新文档。该方法返回一个新的 `Document` 对象，您可以立即保存。`Document` 对象表示结果文件的内存表示。

### 步骤 1：创建 Merger 实例
`Merger` 类是加载和操作文档的入口点。通过传入源文件路径实例化 `Merger` 类。该对象代表您将要处理的文档。

### 步骤 2：指定要提取的页面
提供页索引列表（基于 1 的编号）或类似 `"1-3,5"` 的范围字符串，以告知库保留哪些页面。

### 步骤 3：保存提取的文档
在 `Document` 对象上调用 `Save`，提供输出路径和所需格式（例如 `SaveFormat.Pdf`）。`SaveFormat` 是一个枚举，用于指定输出文件类型，如 PDF。此操作会写入仅包含所选页面的新文件。

## 常见问题及解决方案
- **页面偏移一页：** GroupDocs.Merger 使用基于 1 的页码。确保列表从 1 开始，而不是 0。  
- **受密码保护的文件：** 将密码传递给 `Merger` 构造函数或使用 `LoadOptions` 对象。`LoadOptions` 提供控制文档加载方式的设置，例如启用内存缓存。  
- **大文件导致超时：** 通过设置 `LoadOptions.UseMemoryCache = true` 启用流式处理，以保持低内存使用。

## 常见问答

**Q: 我可以将 Word 文档的页面提取为 PDF 吗？**  
A: 可以——相同的 `Extract` 调用适用于 DOCX，您可以直接使用 `SaveFormat.Pdf` 将结果保存为 PDF。

**Q: 是否可以提取非连续页面？**  
A: 完全可以。提供逗号分隔的列表，如 `"2,4,7"`，或混合范围 `"1-2,5,8-10"`。

**Q: 库是否支持加密的 PDF？**  
A: 支持。打开文档时提供密码，API 会自动解密。

**Q: GroupDocs.Merger 如何处理 PDF 中的图像？**  
A: 图像会保持在所选页面上的原始显示方式，无需额外的转换步骤。

**Q: .NET 版本官方支持哪些？**  
A: .NET Framework 4.6+、.NET Core 3.1+ 和 .NET 5/6/7 均得到完整支持。

## 可用教程

### [使用 GroupDocs.Merger for .NET 从文档中提取特定页面](./extract-pages-groupdocs-merger-net/)
Learn how to efficiently extract specific pages using GroupDocs.Merger for .NET. Ideal for managing Word, PDF, and more in professional environments.

### [如何在 C# 中使用 GroupDocs.Merger for .NET 提取文档的特定页面](./extract-pages-groupdocs-merger-dotnet-csharp/)
Learn how to extract specific pages from documents using GroupDocs.Merger for .NET with this comprehensive guide. Streamline your document management tasks effortlessly.

## 其他资源

- [GroupDocs.Merger for .net 文档](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net API 参考](https://reference.groupdocs.com/merger/net/)
- [下载 GroupDocs.Merger for .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger)
- [免费支持](https://forum.groupdocs.com/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

**最后更新：** 2026-08-31  
**已测试：** GroupDocs.Merger 23.9 for .NET  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Merger for .NET 合并特定 PDF 页面：完整指南](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [如何使用 GroupDocs.Merger for .NET 合并多个文档的特定页面](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [.NET 中使用 GroupDocs.Merger 旋转 PDF 页面：分步指南](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)