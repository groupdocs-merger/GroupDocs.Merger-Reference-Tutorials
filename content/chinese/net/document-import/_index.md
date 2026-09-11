---
date: 2026-09-11
description: 了解如何使用 GroupDocs.Merger for .NET 将 PDF 导入 Word 及其他格式，包括在几步内嵌入 PDF 到 Word
  和添加 PDF 附件。
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: 了解如何使用 GroupDocs.Merger for .NET 将 PDF 导入 Word 及其他格式，涵盖嵌入 PDF 到 Word、添加
  PDF 附件以及 OLE 嵌入。
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: 如何使用 GroupDocs.Merger for .NET 将 PDF 导入 Word
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: 如何使用 GroupDocs.Merger for .NET 将 PDF 导入 Word
type: docs
url: /zh/net/document-import/
weight: 10
---

# 如何使用 GroupDocs.Merger for .NET 将 PDF 导入 Word

在本指南中，您将了解如何使用 GroupDocs.Merger for .NET **将 PDF 导入 Word** 以及其他文档类型。无论您需要将 PDF 嵌入 Word 文件、将 PDF 附加到现有文档，还是在图表、演示文稿、电子表格和文字处理文件之间移动内容，本教程都将带您了解最常见的场景，解释其重要性，并展示快速完成任务的确切步骤。

## 快速答案
- **我可以将 PDF 导入 Word 文档吗？** 是的 – GroupDocs.Merger 允许您将 PDF 作为 OLE 对象或本机内容嵌入 .docx 文件。  
- **我需要单独的 PDF 库吗？** 不需要，Merger SDK 在没有额外依赖的情况下处理 PDF 导入。  
- **支持哪些 .NET 版本？** .NET Framework 4.5+、.NET Core 3.1+、.NET 5/6/7。  
- **生产环境需要许可证吗？** 生产环境需要商业许可证；可提供免费试用版用于评估。  
- **我可以导入多大的 PDF？** 支持每个文件最高 500 MB，且无需将整个文档加载到内存中。

## 什么是将 PDF 导入 Word？
将 PDF 导入 Word 意味着将 PDF 文件的内容放入 Microsoft Word (.docx) 文档中，既可以作为嵌入对象，也可以转换为本机元素，同时保留布局、图像和文本格式。该过程可以保留文本流、图像、表格和矢量图形，确保生成的 Word 文件尽可能接近原始 PDF 的布局。

## 为什么在此任务中使用 GroupDocs.Merger？
GroupDocs.Merger 支持 **30+ 输入和输出格式**，并且可以在不将文档完整加载到 RAM 中的情况下处理高达 **500 MB** 的文档，从而降低服务器端应用的内存压力。该库还提供 **内置 OLE 嵌入**，允许您在单个 API 调用中直接将 PDF 附加到 Word、Excel 或 PowerPoint 文件。

## 前提条件
- .NET 开发环境（Visual Studio 2022 或更高版本）。  
- 已安装 GroupDocs.Merger for .NET NuGet 包（`Install-Package GroupDocs.Merger`）。  
- 用于生产的有效 GroupDocs.Merger 许可证（可提供临时许可证用于测试）。

## 将 PDF 导入 Word 的逐步操作

### 如何将 PDF 文件嵌入 Word 文档？
`Merger` 是 GroupDocs.Merger SDK 的核心类，提供文档操作方法。  
`Insert` 在指定位置将源文档或对象插入目标文档。

使用 `Merger` 加载源 PDF 并调用 `Insert` 将其放入目标 `.docx`。该操作仅需两行代码，并自动处理 OLE 打包，使 PDF 以交互式对象的形式出现在 Word 中。

### 如何向现有 Word 文件添加 PDF 附件？
`AddAttachment` 将外部文件附加到容器文档中，存储在包内以供后续检索。

创建 `Merger` 实例，打开 Word 文档，然后使用 `AddAttachment` 方法附加 PDF。附件存储在 Word 包内部，可直接从文档的 “插入 > 对象” 对话框打开。

### 如何将 OLE 对象（如 PDF）嵌入 Excel 电子表格？
`InsertOleObject` 将 OLE 对象（如 PDF）嵌入电子表格单元格，允许在 Excel 中交互式打开。

在 Excel 工作簿上使用 `InsertOleObject` 方法。该方法接受 PDF 文件路径和单元格位置，将 PDF 作为 OLE 对象插入，可双击打开。

## 常见问题及解决方案
- **PDF 仅显示为图标：** 确保目标 Word 文件保存为 `.docx` 扩展名；旧的 `.doc` 文件不支持嵌入 OLE 对象。  
- **大 PDF 导入缓慢：** 在导入前调用 `MergerSettings.EnableMemoryOptimization = true` 以降低内存使用。  
- **嵌入的 PDF 无法点击：** 确认 PDF 文件未受密码保护；Merger 在未提供密码的情况下无法嵌入加密的 PDF。

## 常见问答

**Q: 我可以只将 PDF 的选定页面导入 Word 吗？**  
A: 可以 – 在调用 `Insert` 时使用 `PageRange` 选项指定要嵌入的页面。

**Q: 导入时库会保留 PDF 中的超链接吗？**  
A: 以 OLE 对象形式嵌入时，超链接在 PDF 查看器中保持可用；转换为本机 Word 内容时，大多数超链接会被保留。

**Q: 能否批量导入多个 PDF 到同一个 Word 文档？**  
A: 完全可以。遍历 PDF 集合，对每个文件调用 `Insert`；库会顺序合并它们。

**Q: 如果我的 PDF 包含矢量图形怎么办？**  
A: 当 PDF 作为 OLE 对象嵌入时，矢量图形会被保留，在任何缩放级别下都能清晰呈现。

**Q: GroupDocs.Merger 能在 Linux 容器上运行吗？**  
A: 能 – .NET Standard 构建可在 Linux、macOS 和 Windows 上运行，无需任何本机依赖。

## 可用教程

### [使用 GroupDocs.Merger for .NET 为 PDF 添加附件&#58; 分步指南](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
了解如何使用 GroupDocs.Merger for .NET 为 PDF 添加附件。本分步指南涵盖设置、实现和实际应用。

### [在 PowerPoint 中使用 GroupDocs.Merger for .NET 将 PDF 作为 OLE 嵌入&#58; 分步指南](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
了解如何使用 GroupDocs.Merger for .NET 将 PDF 文件无缝嵌入 PowerPoint 演示文稿。请遵循本综合指南。

### [使用 GroupDocs.Merger for .NET 将 PDF 嵌入 Word&#58; 分步指南](./embed-pdf-word-groupdocs-merger-dotnet/)
了解如何使用 GroupDocs.Merger for .NET 将 PDF 无缝嵌入 Microsoft Word 文档。高效提升文档的动态内容。

### [如何使用 GroupDocs.Merger for .NET 在 Excel 电子表格中嵌入 OLE 对象](./embed-ole-objects-groupdocs-merger-net/)
了解如何使用 GroupDocs.Merger for .NET 将 OLE 对象（如 PDF）嵌入 Excel 电子表格，提升数据展示和功能性。

## 其他资源

- [GroupDocs.Merger for .net 文档](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net API 参考](https://reference.groupdocs.com/merger/net/)
- [下载 GroupDocs.Merger for .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger)
- [免费支持](https://forum.groupdocs.com/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

---

**最后更新：** 2026-09-11  
**已测试：** GroupDocs.Merger 23.12 for .NET  
**作者：** GroupDocs

## 相关教程

- [使用 GroupDocs.Merger for .NET 将 PDF 嵌入 Word：分步指南](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [使用 GroupDocs.Merger for .NET 为 PDF 添加附件：分步指南](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [在 .NET 中使用 GroupDocs.Merger 从 URL 加载 PDF：综合指南](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)