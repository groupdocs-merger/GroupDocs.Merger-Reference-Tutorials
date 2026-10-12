---
additionalTitle: GroupDocs API References
date: 2026-10-11
description: 探索 GroupDocs.Merger 文档合并 API，实现快速、跨平台的文档合并、拆分以及 PDF、Office 文件、图像等的处理。
is_root: true
keywords:
- groupdocs.merger document merging api
- document merging and splitting
- cross-platform document processing
lastmod: 2026-10-11
linktitle: GroupDocs.Merger 教程
og_description: GroupDocs.Merger 文档合并 API 让您能够在 50 多种格式之间合并、拆分、重新排序并保护文档。了解针对 .NET
  和 Java 的快速跨平台集成。
og_image_alt: Guide to using GroupDocs.Merger for merging and splitting documents
og_title: GroupDocs.Merger 文档合并 API – 完整指南
schemas:
- author: GroupDocs
  dateModified: '2026-10-11'
  description: Explore the GroupDocs.Merger document merging API for fast, cross‑platform
    document merging, splitting, and processing of PDFs, Office files, images and
    more.
  headline: GroupDocs.Merger document merging API – complete guide to merging & splitting
  type: TechArticle
- questions:
  - answer: Yes, with a valid GroupDocs license. A free trial is available for evaluation.
    question: Can I use the API in a commercial product?
  - answer: Absolutely. You can open, modify, and re‑secure encrypted PDFs using the
      same API calls.
    question: Does the API support password‑protected PDFs?
  - answer: .NET Standard 2.0, .NET Framework 2.0+, .NET Core 2.0+, Mono 1.2+; Java
      7, 8, and 10+ are fully supported.
    question: Which .NET and Java versions are compatible?
  - answer: It streams data and uses memory‑efficient algorithms, allowing you to
      process multi‑gigabyte documents without exhausting system resources.
    question: How does the API handle very large files?
  - answer: While the core merging API focuses on structural operations, you can combine
      it with GroupDocs.Parser for advanced text extraction and OCR needs.
    question: Is there built‑in support for OCR or text extraction?
  type: FAQPage
tags:
- document merging
- groupdocs.merger
- .net document processing
- java document processing
title: GroupDocs.Merger 文档合并 API – 完整的合并与拆分指南
type: docs
url: /zh/
weight: 11
---

# GroupDocs.Merger 文档合并 API – 完整的合并与拆分指南

**GroupDocs.Merger 文档合并 API** 为您提供一种快速、跨平台的方式，可直接在 .NET 或 Java 应用程序中合并、拆分和操作各种文档类型。无论是需要将多个 PDF 合并为单个报告、将大型合同拆分为单独页面，还是重新排序演示文稿中的幻灯片，此 API 只需几行代码即可完成。

## 快速答案
- **API 的功能是什么？** 它可以合并、拆分、重新排序并保护 50 多种格式的文档。  
- **支持哪些平台？** .NET（Standard、Framework、Core、Mono）和 Java（J2SE 7‑10）。  
- **需要外部软件吗？** 不需要——无需 Microsoft Office 或 Adobe 依赖。  
- **可以保护文档吗？** 可以，您可以添加、删除或更新密码和权限。  
- **文件大小有上限吗？** 该 API 针对大文件和批量操作进行了优化。  

## 什么是 GroupDocs.Merger 文档合并 API？

加载文件并调用相应的合并或拆分方法——这就是 GroupDocs.Merger 文档合并 API 的核心工作流。它提供了统一且一致的接口来处理 PDF、Office 文档、图像、压缩包等，同时保留布局、元数据和安全设置。

GroupDocs.Merger 文档合并 API 是面向开发者的库，抽象了处理多种文档格式的复杂性。它允许您以编程方式合并文件、按页面或范围拆分文件，并执行高级页面操作——所有操作均保留原始布局和元数据。

## 为什么选择 GroupDocs.Merger 文档合并 API？

您将获得跨平台的一致性、广泛的格式支持、无外部依赖、高性能以及内置安全——全部集于一体。API 采用流式处理，即使是多 GB 的文件也能以低内存占用进行处理，非常适合服务器端批量任务。

## 改变跨平台文档管理方式

GroupDocs.Merger 提供了强大且跨平台的文档操作解决方案，简化了开发者在应用中处理文件的方式。我们的完整 API 使您能够将多个文档合并为一个、将文档拆分为更小的组件、重新排序页面、应用安全选项等——只需极少的代码即可实现最高效率。

无论您在 .NET 还是 Java 环境中开发，GroupDocs.Merger 都提供一致的高性能文档处理能力，能够无缝支持包括 PDF、Office 文档、图像等在内的 50 多种流行文件格式。

## 关键特性与功能
- **全面的文档合并** – 将多个来源的整个文档或特定页面合并为单个完整文件。  
- **跨格式支持** – 将不同文件格式合并为统一文档（例如，将 DOC、XLSX 和图像合并为单个 PDF）。  
- **智能文档拆分** – 按页码、范围拆分文档，或将特定页面提取为单独文件。  
- **高级页面操作** – 精确控制页面的移动、删除、旋转、交换和提取。  
- **安全管理** – 添加、删除或更新文档密码和权限。  
- **OLE 对象支持** – 将文档作为 OLE 对象插入 Word、Excel、PowerPoint 和 Visio 文件中。  
- **无外部依赖** – 处理文档时无需 Microsoft Office 或 Adobe 软件。  
- **高性能** – 针对大文档和批量操作进行高效优化。

## 支持的文件格式
GroupDocs.Merger 支持超过 50 种文件格式，涵盖多个类别：

- **文档**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **电子表格**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **演示文稿**: PPT, PPTX, PPS, PPSX, ODP
- **图像**: JPG, PNG, BMP, GIF, TIFF, SVG
- **图表**: VSDX, VSDM, VSSX, VSTX, VDX, VSX, VTX
- **压缩包**: ZIP, TAR, 7Z
- **以及更多**

## [GroupDocs.Merger .NET 教程](./net)

了解如何将强大的文档处理功能集成到您的 .NET 应用程序中。我们的完整 .NET 教程将引导您了解 GroupDocs.Merger API 的各个方面，从基础操作到高级实现场景。

使用 GroupDocs.Merger for .NET，您可以创建在多个 .NET 框架（包括 .NET Standard 2.0、.NET Framework 2.0+、.NET Core 2.0+ 和 Mono Framework 1.2+）上运行的强大文档管理解决方案。

### 必备 .NET 教程
- [合并压缩文件](./net/merge-compress-files/) - 学习高效地合并和压缩归档格式（7z、TAR、ZIP）
- [图像合并](./net/image-merging/) - 掌握合并各种图像格式（BMP、GIF、PNG、SVG、TIFF）的技巧
- [文档合并](./net/document-merging/) - 无缝合并 DOC、DOCX、PDF 等文档格式
- [电子表格合并](./net/spreadsheet-merging/) - 合并 Excel 文件，同时保留数据、公式和格式
- [Visio 合并](./net/visio-merging/) - 精确控制地合并 Visio 图表和绘图
- [演示文稿合并](./net/presentation-merging/) - 合并 PowerPoint 演示文稿，同时保留幻灯片和动画  

### 高级 .NET 操作
- [文档加载](./net/document-loading/) - 探索从不同来源加载文档的各种技术
- [文档信息](./net/document-information/) - 提取并分析文档元数据和属性
- [文档合并](./net/document-joining/) - 学习高级文档合并选项和自定义
- [特定格式合并](./net/format-specific-merging/) - 探索针对特定文件格式的优化合并技术
- [高级合并选项](./net/advanced-joining-options/) - 掌握复杂的文档合并场景
- [文档安全](./net/document-security/) - 实现具有密码管理的强大文档保护
- [页面操作](./net/page-operations/) - 精确控制文档页面的操作
- [文档提取](./net/document-extraction/) - 从更大的文档中提取特定内容
- [文档导入](./net/document-import/) - 将外部内容导入文档
- [图像操作](./net/image-operations/) - 有效处理和操作图像文件
- [文档拆分](./net/document-splitting/) - 使用各种拆分策略划分文档（文档拆分）
- [文本操作](./net/text-operations/) - 高效处理基于文本的文档
- [授权](./net/licensing/) - 在项目中正确配置 GroupDocs.Merger  

## [GroupDocs.Merger Java 教程](./java)

为您的 Java 应用程序注入强大的文档处理能力。我们的 Java 教程提供了在 Java 环境中实现 GroupDocs.Merger 的详细指导，并附有可在 Windows、Linux、macOS 等主要平台上运行的完整示例。

GroupDocs.Merger for Java 支持 J2SE 7.0（1.7）、J2SE 8.0（1.8）和 Java 10，几乎兼容所有基于 Java 的开发项目。

### 必备 Java 教程
- [文档加载](./java/document-loading/) - 掌握从文件、流和 URL 加载文档的技术
- [文档信息](./java/document-information/) - 提取有价值的文档元数据和属性
- [文档合并](./java/document-joining/) - 精确控制地将多个文件合并为单个文档
- [特定格式合并](./java/format-specific-merging/) - 学习针对不同文件格式的优化方法
- [高级合并选项](./java/advanced-joining-options/) - 探索复杂的合并场景和自定义
- [文档安全](./java/document-security/) - 实现强大的文档保护和权限控制
- [页面操作](./java/page-operations/) - 操作文档中的单个页面
- [文档提取](./java/document-extraction/) - 从文档中提取特定内容
- [文档导入](./java/document-import/) - 将外部内容导入文档
- [图像操作](./java/image-operations/) - 处理图像文件及转换
- [文档拆分](./java/document-splitting/) - 使用各种拆分策略划分文档（文档拆分）
- [文本操作](./java/text-operations/) - 有效处理基于文本的文档
- [授权](./java/licensing/) - 在 Java 环境中配置 GroupDocs.Merger  

## 常见使用场景与收益
- **自动化报告生成：** 将基于数据的 PDF 和 Excel 表合并为单个报告以进行分发。  
- **法律文档管理：** 将大型合同拆分为单独章节，以便更容易审阅和签署。  
- **内容迁移：** 将来自多种格式的旧版文档转换并合并为标准化的 PDF 档案。  
- **安全文档交付：** 在向客户发送机密文件之前应用密码和权限。  

## 常见问题解答

**问：我可以在商业产品中使用该 API 吗？**  
答：可以，需拥有有效的 GroupDocs 许可证。提供免费试用供评估。

**问：API 是否支持受密码保护的 PDF？**  
答：当然。您可以使用相同的 API 调用打开、修改并重新加密受保护的 PDF。

**问：兼容哪些 .NET 和 Java 版本？**  
答：.NET Standard 2.0、.NET Framework 2.0+、.NET Core 2.0+、Mono 1.2+；Java 7、8 和 10+ 均得到完整支持。

**问：API 如何处理超大文件？**  
答：它采用流式数据和内存高效算法，能够在不耗尽系统资源的情况下处理多 GB 文档。

**问：是否内置 OCR 或文本提取支持？**  
答：核心合并 API 侧重于结构化操作，您可以将其与 GroupDocs.Parser 结合使用，以实现高级文本提取和 OCR 功能。

**问：如何快速入门？**  
答：为 .NET 安装 NuGet 包 (`GroupDocs.Merger`) 或为 Java 添加 Maven 依赖，然后按照 “文档加载” 教程加载第一个文件。

**问：我可以将不同文件类型合并为一个 PDF 吗？**  
答：可以——API 能将 PDF、Word、Excel、图像及其他多种格式合并为单个 PDF 输出。

---

**最后更新：** 2026-10-11  
**测试版本：** GroupDocs.Merger 23.12（最新稳定版）  
**作者：** GroupDocs