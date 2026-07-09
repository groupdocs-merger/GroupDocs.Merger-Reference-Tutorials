---
date: 2026-06-16
description: 了解如何使用 GroupDocs.Merger for Java 拆分 PDF 并合并 PDF —— 步骤指南，涵盖 split pdf
  java、merge pdf java、protect pdf java 等内容。
is_root: true
keywords:
- split pdf java
- java combine pdf files
- groupdocs merger for java
- protect pdf java
- merge multiple pdfs java
linktitle: GroupDocs.Merger for Java 教程
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to split PDF and merge PDFs with GroupDocs.Merger for Java
    – step-by-step guide covering split pdf java, merge pdf java, protect pdf java,
    and more.
  headline: How to Split PDF and Merge PDFs with GroupDocs.Merger for Java
  type: TechArticle
- questions:
  - answer: Instantiate a `Merger`, call `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`,
      and specify an output folder—each range becomes a separate PDF file.
    question: How do I split PDFs using GroupDocs.Merger in Java?
  - answer: Yes—GroupDocs.Merger supports cross‑format merging, allowing you to combine
      PDFs with Excel files (`merge excel files java`) into a single PDF output.
    question: Can I merge PDFs and Excel sheets together?
  - answer: After calling `merge()`, invoke `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))`
      to encrypt the final document.
    question: How do I add password protection after merging?
  - answer: Enable streaming (`Merger.setStreaming(true)`) to process files in a buffered
      fashion, which dramatically reduces memory consumption for large documents.
    question: Is it possible to merge PDFs without loading the entire file into memory?
  - answer: A commercial GroupDocs.Merger license is mandatory for production deployments;
      a free 30‑day trial is available for development and testing.
    question: What licensing is required for production use?
  type: FAQPage
title: 如何使用 GroupDocs.Merger for Java 拆分 PDF 并合并 PDF
type: docs
url: /zh/java/
weight: 10
---

# 如何使用 GroupDocs.Merger for Java 拆分 PDF 并合并 PDF

在现代 Java 应用程序中，**split pdf java** 是一个常见需求——无论是需要将庞大的报告拆分成易于阅读的章节，还是将多个发票合并为一个归档。GroupDocs.Merger for Java 让拆分和合并 PDF（以及超过 50 种其他格式）变得轻而易举，只需几行代码即可实现高性能处理。在本教程中，我们将探讨核心 API，演示真实场景，并指引您深入学习每一种文档处理需求的更高级教程。

## 快速答案
- **GroupDocs.Merger 的主要用途是什么？** 合并、拆分和操作超过 50 种格式的文档，包括 PDF、Word、Excel 和图像。  
- **我可以在 Java 中拆分 PDF 吗？** 是的——API 提供了专门的 “split pdf java” 方法，允许您定义页面范围或基于大小的拆分。  
- **如何在 Java 中合并多个 PDF？** 使用 `Merger` 类的 “merge pdf java” 工作流即可立即合并文件。  
- **合并后可以进行密码保护吗？** 当然；“protect pdf java” 功能可使用您选择的密码加密结果。  
- **生产环境需要许可证吗？** 任何生产部署都需要商业版 GroupDocs.Merger 许可证；提供免费试用供评估使用。

## 什么是使用 GroupDocs.Merger “how to merge PDFs”？
`GroupDocs.Merger for Java` 是一个库，能够以编程方式将多个 PDF 文件（或任何受支持的格式）合并为一个结构良好的文档。它自动保留页面顺序、元数据以及可选的安全设置，让您只需极少代码即可实现复杂的文档工作流。

## 为什么使用 GroupDocs.Merger for Java？
加载源 PDF，指定所需页面，然后调用 `merge()`——API 会处理所有繁重工作。它支持 **50+ 输入和输出格式**，每秒处理 **数百页**，并且可在本地或云环境中运行，无需外部依赖。

## 使用 GroupDocs.Merger 掌握文档操作

GroupDocs.Merger for Java 是一个强大的 API，帮助 Java 开发者在超过 50 种流行文件格式之间进行合并、拆分和操作。我们的完整教程系列提供了详细的分步指导，帮助您充分利用 GroupDocs.Merger 的全部功能，简化文档管理工作流。

无论您需要 **合并多个 PDF**、合并 Word 文档、合并电子表格、整合演示文稿，还是处理图像——这些教程都将帮助您在 Java 应用中以最少代码实现强大的文档处理功能。

## 使用 GroupDocs.Merger 可以实现的功能

- **将多个文档合并为单个文件**，同时保留格式和内容完整性。  
- **从不同源文档中选择特定页面或范围**进行合并。  
- **将大型文档拆分为更小、更易管理的文件**。  
- **通过移动、删除、旋转或交换操作**来操控页面顺序。  
- **使用密码加密和权限管理**来保护文档。  
- **从特定文档章节提取内容**。  
- **在包括 PDF、Word、Excel、PowerPoint 等众多格式中处理文档**。

## GroupDocs.Merger for Java 教程分类

### [文档加载](./document-loading/)
掌握文档处理的第一步。学习从文件、流和 URL 加载文档的各种技术，并针对不同格式进行适当配置。

### [文档信息](./document-information/)
提取文档的有价值元数据。这些教程展示如何访问文档属性、页数和格式细节，以实现更好的文档管理。

### [文档合并](./document-joining/)
无缝合并多个文档。了解如何将整个文件或来自不同源的特定页面合并为一个统一的文档。

### [特定格式合并](./format-specific-merging/)
针对特定文件类型优化合并操作。学习合并 PDF、Word 文档、Excel 表格、PowerPoint 演示文稿等的专用技术。

### [高级合并选项](./advanced-joining-options/)
将文档合并提升到更高水平。探索自定义页面选择、跨格式合并以及内容保留选项的复杂场景。

### [文档安全](./document-security/)
为文档实现强大的保护。学习添加、删除或更新密码，管理权限，确保文档机密性。

### [页面操作](./page-operations/)
对文档页面进行精确控制。发现重新排序、旋转、删除和修改单个页面的技术。

### [文档提取](./document-extraction/)
从大型文档中提取特定内容。学习如何选择并保存特定页面或章节为独立文件。

### [文档导入](./document-import/)
使用外部内容增强文档。这些教程演示如何从各种来源（包括 OLE 对象和附件）导入内容。

### [图像操作](./image-operations/)
高效处理图像文件。探索合并、转换以及在文档中嵌入图像的方法。

### [文档拆分](./document-splitting/)
有策略地划分文档。学习按页码、范围或特定条件拆分文件，以创建多个输出文档。

### [文本操作](./text-operations/)
高效操作基于文本的文档。发现处理文本文件的方式，包括合并、按行拆分和格式转换。

### [授权](./licensing/)
在项目中正确设置 GroupDocs.Merger。了解授权选项、配置方法和部署注意事项。

## 支持的文件格式

GroupDocs.Merger for Java 支持广泛的文档格式，包括：

- **文字处理**：DOCX、DOC、RTF、ODT、DOTX、DOTM、DOT  
- **电子表格**：XLSX、XLS、XLSM、XLSB、ODS、XLT、XLTX  
- **演示文稿**：PPTX、PPT、PPSX、PPS、ODP、POT  
- **可移植文档**：PDF、XPS  
- **Visio 图表**：VSDX、VSDM、VSTX、VSSX、VDX、VSX、VTX  
- **电子书**：EPUB  
- **图像**：BMP、JPG、PNG、TIFF  
- **网页**：HTML、MHT、MHTML  
- **文本**：TXT、CSV、TSV  
- **以及更多！**（共计超过 50 种格式）

## 入门指南

本节教程采用实用的代码优先方法，提供完整示例，您可以直接在应用中实现。每个教程包括：

- 对功能及其使用场景的清晰说明  
- 步骤化实现指南  
- 带注释的完整代码示例（代码位于链接的子教程中）  
- 配置选项和替代方案  
- 性能考量与最佳实践  

立即开始探索我们的教程，充分释放 GroupDocs.Merger for Java 在文档处理工作流中的全部潜能！

## 如何在 Java 中拆分 PDF？

只需三行 Java 代码即可将 PDF 拆分为单页或自定义范围。对 `Merger` 实例调用 `split()` 方法，传入源文件路径并指定所需的页面范围或大小。库会将每个片段写入单独文件，同时保留原始质量和元数据。

您还可以按大小（例如 5 MB 块）或页面列表拆分，这对于从单一主文档生成章节式 PDF 非常理想。该操作的时间复杂度与页面数量线性相关，适合大规模批处理。

## 如何在 Java 中合并多个 PDF？

使用 `Merger` 的 `addDocument()` 方法加载每个源 PDF，按所需顺序排列后调用 `merge()`。API 会自动统一页面尺寸，更新书签，并合并文档属性。您还可以将 PDF 与其他格式（如 Word 或 Excel）合并——在合并过程中即时转换，生成统一的 PDF 输出。

对于高吞吐场景，启用流式模式可避免将整个文件加载到内存中。处理数百页文档时，可将堆内存使用降低至 80 % 以上。

## 理解 Merger 类

`Merger` 类是 GroupDocs.Merger for Java 的核心组件，负责文档的合并、拆分和安全操作。它提供了流式方法，如 `addDocument()`、`split()`、`protect()` 和 `merge()`，以构建简洁的处理管道。

### 关键方法概览
- `addDocument(String path)`: 将源文件加入待合并队列。  
- `split(String source, SplitOptions options)`: 根据页面范围或大小限制拆分文档。  
- `protect(String output, ProtectionOptions options)`: 应用密码保护和权限限制。  
- `merge(String output)`: 执行队列中的操作并写入最终文档。

这些方法是线程安全的，可链式调用，实现表达式化、可读的代码。

## 常见问题及解决方案

| 问题 | 原因 | 解决方案 |
|-------|-------|----------|
| **大 PDF 导致内存溢出** | 将整个文件加载到内存 | 启用流式模式 (`Merger.setStreaming(true)`) 或在合并前将文件拆分为更小块。 |
| **页面方向不一致** | 源 PDF 包含混合的纵向/横向页面 | 在合并前使用 `rotatePage(int pageNumber, RotationAngle angle)` 标准化方向。 |
| **受密码保护的源文件无法打开** | 缺少解密密码 | 在添加文档时通过 `DocumentLoadOptions.setPassword("yourPwd")` 提供密码。 |
| **合并后元数据丢失** | 默认合并会丢弃自定义元数据 | 在 `Merger` 实例上调用 `setPreserveMetadata(true)` 以保留原始属性。 |

## 常见问答

**问：如何在 Java 中使用 GroupDocs.Merger 拆分 PDF？**  
答：实例化 `Merger`，调用 `split(sourcePath, new SplitOptions().setPageRanges("1-3,5,7-10"))`，并指定输出文件夹——每个范围会生成一个独立的 PDF 文件。

**问：我可以将 PDF 与 Excel 表格合并吗？**  
答：可以——GroupDocs.Merger 支持跨格式合并，允许您将 PDF 与 Excel 文件（`merge excel files java`）合并为单个 PDF 输出。

**问：合并后如何添加密码保护？**  
答：调用 `merge()` 后，使用 `protect(outputPath, new ProtectionOptions().setPassword("Secret123"))` 对最终文档进行加密。

**问：是否可以在不将整个文件加载到内存的情况下合并 PDF？**  
答：启用流式模式 (`Merger.setStreaming(true)`) 可以缓冲方式处理文件，大幅降低大文档的内存消耗。

**问：生产环境需要什么授权？**  
答：生产部署必须使用商业版 GroupDocs.Merger 许可证；提供 30 天免费试用供开发和测试使用。

---

**最后更新：** 2026-06-16  
**测试环境：** GroupDocs.Merger for Java 23.12（撰写时最新）  
**作者：** GroupDocs

## 相关教程

- [Efficiently Merge PDFs Using GroupDocs.Merger for Java: A Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [How to Merge DOCX Files Easily with GroupDocs.Merger for Java: Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-docx-files-groupdocs-merger-java/)
- [How to Merge PowerPoint Files in Java Using GroupDocs.Merger: A Step‑By‑Step Guide](/merger/java/format-specific-merging/merge-powerpoint-files-java-groupdocs-merger-guide/)