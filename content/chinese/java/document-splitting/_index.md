---
date: 2026-05-22
description: 了解如何使用 GroupDocs.Merger for Java 创建单页 PDF 文件并拆分 PDF。包括针对 split pdf java
  的分步指南以及更多内容。
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
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
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: 使用 GroupDocs.Merger Java 创建单页 PDF
type: docs
url: /zh/java/document-splitting/
weight: 12
---

# 使用 GroupDocs.Merger Java 创建单页 PDF

如果您需要从更大的文档中**创建单页 PDF**文件，或仅仅将 PDF 拆分为更易管理的片段，您来对地方了。本指南将带您了解最常见的拆分场景——多页文件、页码范围、奇偶页、DOCX 拆分，甚至基于文本的拆分——使用强大的 GroupDocs.Merger Java 库。教程结束时，您将清楚如何将这些技术集成到自己的应用中，提高文档处理性能，并保持代码库整洁可维护。

## 快速答案
- **“create single page PDF” 是什么意思？** 它指的是从源文档中提取一页并将其保存为独立的 PDF 文件。  
- **哪个库负责此工作？** GroupDocs.Merger for Java 提供了流畅的 API 来完成所有拆分操作。  
- **我需要许可证吗？** 临时许可证可用于开发；生产环境需要正式许可证。  
- **我可以拆分 PDF 的奇数页和偶数页吗？** 可以——GroupDocs.Merger 允许您按奇数/偶数页号过滤。  
- **支持 DOCX 拆分吗？** 当然；您可以按页或自定义范围拆分 DOCX 文件。  

## 什么是 “create single page PDF”？
创建单页 PDF 包括从多页源文档（PDF、DOCX、PPTX 等）中提取单独的一页并保存为独立的 PDF 文件。这在生成发票、证书或仅需特定页面的预览图像时非常有用。

## 为什么使用 GroupDocs.Merger for Java？
GroupDocs.Merger for Java 提供统一且一致的 API，能够处理多种文档格式，同时实现高性能和低内存占用。它通过抽象复杂的文件处理，使开发更简便，让您专注于业务逻辑，而非底层处理细节。

- **统一 API** – 支持 PDF、DOCX、PPTX、图像及其他多种格式。  
- **高性能** – 为大文件和批量操作优化；可在不将整个文件加载到内存的情况下处理高达 2 GB 的文档。  
- **细粒度控制** – 可按页码范围、奇偶页或自定义分隔符拆分。  
- **流式友好** – 输出可以保存为文件或作为流返回，以供 Web 服务使用。  

## 前提条件
- Java 8 或更高版本。  
- 已在项目中添加 GroupDocs.Merger for Java（Maven/Gradle）。  
- 有效的（临时或正式）GroupDocs 许可证文件。

## 如何创建单页 PDF？
使用 GroupDocs.Merger 创建单页 PDF 包括加载源文件、指定确切的页码或范围、调用拆分操作，最后保存结果。此工作流确保原始文档保持不变，同时将提取的页面保存为独立的 PDF 文件。

`Merger` 类是加载源文档并提供拆分功能的核心组件。

### 步骤 1：初始化 Merger
`Merger` 类是 GroupDocs.Merger 的核心组件，用于加载源文档并提供拆分操作。通过传入文件路径或输入流来创建实例。

### 步骤 2：定义拆分条件
选择所需的确切页码或范围。对于单页提取，您需要指定类似 `1‑1` 的范围。当需要**split pdf by range**时，您可以传入多个范围，例如 `1‑5, 6‑10`。

### 步骤 3：执行拆分
调用相应的 `split` 方法。例如，`merger.split(new int[]{1})` 提取第一页，而 `merger.splitByRange(new int[][]{{1,5},{6,10}})` 在一次调用中处理多个范围。

### 步骤 4：保存结果
将每个输出写入文件路径或返回为 `java.io.InputStream`。这使得与 Web API 集成或将结果存储在云存储中变得简便。

> **专业提示：** 处理大型 PDF 时，在拆分前调用 `merger.setOptimizeResources(true)` 以降低内存消耗。

## 如何将 PDF java 文件拆分为多页
`Merger` 类提供了加载和操作 PDF 文件的主要 API。要将 PDF 拆分为单页文件，只需使用 Merger 实例加载文档并调用无参数的 split 方法。库会自动为每页创建一个新的 PDF，保留原始内容和元数据，非常适合批量处理发票或报告。

## 如何拆分 PDF 的奇偶页
`Merger` 类是执行文档拆分操作的核心组件。当您只需要 PDF 的奇数页或偶数页时，向 split 函数提供所需页码列表。Merger 将生成仅包含这些页的新文档，帮助您快速创建奇数页或偶数页的独立文件。

## 如何拆分 docx 文件（how to split docx）
`Merger` 类同样支持 DOCX 文件。使用 `splitByPage` 可为每页生成一个 DOCX（或 PDF），如果需要 PDF 输出，可结合 `saveAsPdf` 使用。这一步完成了 **docx to pdf java** 转换工作流。

## 如何将文档拆分为多页文件
`Merger` 类负责拆分操作的分页和文件创建。如果您希望将大型文档拆分为固定大小的块，只需指定每个输出文件的页数。Merger 将遍历源文档，创建每个包含指定页数的新 PDF，这简化了大量文档的归档、分发和并行处理。

## 可用教程

### [使用 GroupDocs.Merger for Java 将文档拆分为多页文件](./split-documents-multi-page-files-java-groupdocs-merger/)
了解如何使用 GroupDocs.Merger for Java 高效地将大型文档拆分为更小的多页文件。轻松优化文档管理。

### [使用 GroupDocs.Merger for Java 按行间隔拆分文本文件 | 文档拆分指南](./split-text-file-line-intervals-groupdocs-merger-java/)
了解如何使用 GroupDocs.Merger for Java 按行间隔将文本文件拆分为可管理的部分。全面指南，帮助高效处理文档。

### [使用 GroupDocs.Merger for Java 按页码范围进行文档拆分](./split-documents-page-range-groupdocs-merger-java/)
了解如何使用 GroupDocs.Merger for Java 将文档拆分为特定页码范围。简化文档管理，并可应用奇偶页等过滤。

### [使用 GroupDocs.Merger 进行文档拆分&#58; 全面指南](./master-document-splitting-groupdocs-merger-java/)
了解如何使用 GroupDocs.Merger for Java 高效地将文档拆分为单页。本指南涵盖设置、实现以及实际应用。

### [使用 GroupDocs.Merger 进行 Java 文档拆分&#58; 将 DOCX 页面拆分为文件和流](./master-java-document-splitting-groupdocs-merger/)
了解如何使用 GroupDocs.Merger for Java 高效地将 DOCX 文档拆分为独立页面或流。指南涵盖设置、实现以及实际应用。

## 附加资源

- [GroupDocs.Merger for Java 文档](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API 参考](https://reference.groupdocs.com/merger/java/)
- [下载 GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger)
- [免费支持](https://forum.groupdocs.com/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

## 常见问题及解决方案

| 问题 | 解决方案 |
|-------|----------|
| **大 PDF 内存超载** | 启用资源优化：`merger.setOptimizeResources(true);` |
| **拆分后页码不正确** | 请记住页码索引从 1 开始，而不是 0。 |
| **未找到许可证** | 检查 `GroupDocs.Merger.lic` 文件的路径，并确保其已包含在 classpath 中。 |
| **拆分 DOCX 导致空页** | 确保源 DOCX 有正确的分页符；否则，可使用 `splitByParagraph` 作为备选。 |

## 常见问题

**Q: 我可以拆分受密码保护的 PDF 吗？**  
A: 可以。使用密码参数加载文档，然后照常执行任何拆分操作。

**Q: 如何仅拆分 PDF 的奇数页？**  
A: 向 `split` 方法提供仅包含奇数的页码列表（例如 1,3,5…）。

**Q: 能否直接将 DOCX 拆分为 PDF？**  
A: 完全可以。加载 DOCX 后，对每个拆分段调用 `saveAsPdf`。

**Q: GroupDocs.Merger 支持哪些格式的拆分？**  
A: PDF、DOCX、PPTX、TXT、HTML，以及多种图像格式（PNG、JPEG 等）。

**Q: 每种文件类型都需要单独的许可证吗？**  
A: 不需要。单个 GroupDocs.Merger 许可证覆盖所有受支持的格式。

---

**最后更新：** 2026-05-22  
**测试环境：** GroupDocs.Merger 23.11 for Java  
**作者：** GroupDocs

## 相关教程

- [split pdf java：使用 GroupDocs.Merger 进行文档拆分](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [使用 GroupDocs.Merger for Java 按页码范围进行文档拆分](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [使用 GroupDocs.Merger for Java 高效合并 PDF：一步步指南](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)