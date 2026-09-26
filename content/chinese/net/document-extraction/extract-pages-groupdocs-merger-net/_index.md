---
date: '2026-09-26'
description: 了解如何使用 GroupDocs.Merger for .NET 提取特定页面的 PDF，包括从 Word 中提取页面以及高效处理大型文档。
keywords:
- extract specific pages pdf
- extract pages from word
- extract pages from large document
lastmod: '2026-09-26'
og_description: 了解如何使用 GroupDocs.Merger for .NET 提取特定页面的 PDF。本指南展示了逐步设置、免代码配置以及针对
  Word、PDF 和大型文档的性能技巧。
og_image_alt: Guide showing how to extract specific pages pdf using GroupDocs.Merger
  for .NET
og_title: 使用 GroupDocs.Merger for .NET 提取特定页面的 PDF
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  headline: Extract specific pages pdf with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET, including extracting pages from Word and handling large documents efficiently.
  name: Extract specific pages pdf with GroupDocs.Merger for .NET
  steps:
  - name: install the NuGet package
    text: 'Open a terminal in your project folder and run one of the following commands:
      **.NET CLI** **Package Manager Console** **NuGet Package Manager UI** – use
      the UI to search for “GroupDocs.Merger” and click **Install**.'
  - name: define file paths
    text: Specify absolute or relative paths for the input and the output document
      you want to create. **Definition anchor** `ExtractOptions` is the configuration
      object that tells the library which pages to pull out and how to treat them.
  - name: set extraction options
    text: Create an `ExtractOptions` instance, set `StartPageNumber`, `EndPageNumber`,
      and choose `RangeMode` (e.g., `Even`). This tells the engine to pick every second
      page within the range. **Definition anchor** `Merger` is the core class that
      orchestrates all document‑manipulation operations, including ext
  - name: extract and save
    text: Invoke the `Extract` method on the `Merger` instance, passing the options
      and the output path. The library writes the new file without loading the whole
      source into memory, which is ideal for large documents.
  type: HowTo
- questions:
  - answer: GroupDocs.Merger supports more than 30 formats, including PDF, DOCX, XLSX,
      PPTX, HTML, and image types like PNG and JPEG.
    question: What file formats can I extract pages from?
  - answer: Yes, you can pass a list of individual page numbers or multiple ranges
      to `ExtractOptions`.
    question: Can I extract non‑contiguous pages (e.g., 1, 3, 5)?
  - answer: Provide the password through `LoadOptions` when constructing the `Merger`
      instance; the extraction will then proceed normally.
    question: How do I work with password‑protected PDFs?
  - answer: No hard limit; the only practical constraint is the available memory,
      which remains low thanks to streaming.
    question: Is there a limit on the number of pages I can extract in one call?
  - answer: No external applications are needed; all processing happens inside the
      .NET runtime.
    question: Does the library require Microsoft Office or Adobe Acrobat to be installed?
  type: FAQPage
tags:
- extract specific pages pdf
- GroupDocs.Merger
- .NET document processing
title: 使用 GroupDocs.Merger for .NET 提取特定页面的 PDF
type: docs
url: /zh/net/document-extraction/extract-pages-groupdocs-merger-net/
weight: 1
---

# 使用 GroupDocs.Merger for .NET 提取特定页面 PDF

从多页文档中提取特定页面的 PDF 是一种常见需求，尤其在需要仅共享相关章节、减小文件大小或自动化审阅工作流时。本教程将展示 GroupDocs.Merger for .NET 如何让您提取精确的页面——无论这些页面来自 PDF、Word 文件或任何 30 多种受支持的格式——并提供清晰的编程方式。

## 快速回答
- **GroupDocs.Merger 能从 Word 文档中提取页面吗？** 是的，它支持 DOCX、DOC 以及其他 Office 格式。  
- **是否有文件大小限制？** 该库可以处理高达 2 GB 的文件，而无需将整个文档加载到内存中。  
- **开发阶段需要许可证吗？** 提供免费试用；生产环境需要许可证。  
- **它能在 .NET 6 上运行吗？** 当然——GroupDocs.Merger 支持 .NET Framework 4.5+、.NET Core 3.1+ 和 .NET 5/6+。  
- **一次可以提取多少页面？** 您可以在一次调用中指定单页、范围或奇偶页选择。  

## 什么是 GroupDocs.Merger for .NET？
GroupDocs.Merger for .NET 是一款服务器端库，可在无需 Microsoft Office 或 Adobe Acrobat 的情况下，对超过 30 种文档格式进行合并、拆分、旋转和提取页面。它以流式方式处理文件，即使是数百页的 PDF，也能保持低内存使用。

## 为什么要提取特定页面 PDF？
提取特定页面的 PDF 可以降低带宽消耗、加快协作速度，并确保机密章节不被泄露。量化收益：组织报告称，仅共享所需页面而非完整文件可使文档审阅周期提升最高 40 %。此外，较小的文件还能提升网页查看器的加载速度并降低存储成本。

## 前提条件
- Visual Studio 2022 或任何兼容 .NET 的 IDE。  
- .NET 6 SDK（或 .NET Framework 4.7.2+）。  
- 访问 NuGet 源以安装 **GroupDocs.Merger**。  
- 基本的 C# 知识和文件系统权限。  

## 如何一步步提取特定页面 PDF
加载源文件，定义所需页面，并保存结果——全部只需几行代码。

### 直接答案
`Merger` 是负责文档操作的核心类。`ExtractOptions` 指定要提取的页面以及处理方式。`Extract` 根据提供的选项执行提取并将结果写入新文件。要提取特定页面的 PDF，先使用源文件创建 `Merger` 实例，配置定义页面范围和模式（偶数、奇数或自定义）的 `ExtractOptions` 对象，然后调用 `Extract` 并保存输出文件。整个工作流在标准服务器上对常见的 100 页 PDF 运行时间不足一秒。

### 步骤 1：安装 NuGet 包
在项目文件夹中打开终端，运行以下任意命令：

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager Console**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – 使用 UI 搜索 “GroupDocs.Merger” 并点击 **Install**。

### 步骤 2：定义文件路径
为要创建的输入和输出文档指定绝对或相对路径。

**定义锚点**  
`ExtractOptions` 是配置对象，用于告知库要提取哪些页面以及如何处理它们。  
```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY\\Sample.docx"; // Input document path
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "ExtractedPages.docx"); // Output document path
```  

### 步骤 3：设置提取选项
创建 `ExtractOptions` 实例，设置 `StartPageNumber`、`EndPageNumber`，并选择 `RangeMode`（例如 `Even`）。这会指示引擎在范围内每隔一页提取一次。

**定义锚点**  
`Merger` 是负责所有文档操作（包括提取、合并和页面旋转）的核心类。  
```csharp
ExtractOptions extractOptions = new ExtractOptions(1, 3, RangeMode.EvenPages);
```  

### 步骤 4：提取并保存
在 `Merger` 实例上调用 `Extract` 方法，传入选项和输出路径。库会在不将整个源文件加载到内存的情况下写入新文件，非常适合处理大文档。

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ExtractPages(extractOptions);
    merger.Save(filePathOut); // Save the result to a specified path
}
```  

## 常见问题及解决方案
- **页面未提取** – 再次确认 `StartPageNumber` 和 `EndPageNumber` 使用的是从 1 开始的索引，并且源文件确实包含所请求的范围。  
- **大文件出现内存不足错误** – 确保使用流式 API（默认），并且进程拥有足够的虚拟内存；考虑在库配置中提升 `maxMemory` 设置。  
- **受密码保护的文件** – `LoadOptions` 允许在加载受保护文档时设置密码等参数。在创建 `Merger` 实例之前，通过 `LoadOptions` 提供密码。  

## 实际应用
1. **文档审阅** – 仅提取审阅者需要的条款，其余内容保持机密。  
2. **教育** – 通过提取讲义幻灯片或教材章节生成自定义讲义。  
3. **法律工作流** – 为法院提交单独提取展品页面，而不暴露整个案件文件。  

## 性能考虑因素
GroupDocs.Merger 以流式方式处理文档，能够处理高达 **2 GB** 的文件，同时将峰值内存保持在 **150 MB** 以下。为获得最佳效果，请将 `Merger` 对象放在 `using` 语句中以确保释放，并在从同一源提取多个范围时复用同一实例。

## 结论
现在，您已经掌握了使用 GroupDocs.Merger for .NET 提取特定页面 PDF 的完整、可投入生产的方法。通过配置 `ExtractOptions` 并利用库的流式引擎，您可以对任何受支持的格式实现文档切割自动化，提高协作速度，并对敏感信息进行有效控制。

**下一步** – 探索库的其他功能，如合并文档、旋转页面以及添加水印，以构建全自动化的文档流水线。

## 常见问题

**Q: 我可以从哪些文件格式中提取页面？**  
A: GroupDocs.Merger 支持超过 30 种格式，包括 PDF、DOCX、XLSX、PPTX、HTML，以及 PNG、JPEG 等图像类型。

**Q: 我可以提取非连续页面吗（例如 1、3、5）？**  
A: 可以，您可以向 `ExtractOptions` 传递单个页码列表或多个范围。

**Q: 如何处理受密码保护的 PDF？**  
A: 在构造 `Merger` 实例时通过 `LoadOptions` 提供密码；随后提取将正常进行。

**Q: 单次调用提取的页面数量有上限吗？**  
A: 没有硬性上限；唯一的实际限制是可用内存，由于流式处理，内存占用保持低水平。

**Q: 该库是否需要安装 Microsoft Office 或 Adobe Acrobat？**  
A: 不需要任何外部应用程序，所有处理都在 .NET 运行时内部完成。

## 资源
- [文档](https://docs.groupdocs.com/merger/net/)
- [API 参考](https://reference.groupdocs.com/merger/net/)
- [下载 GroupDocs.Merger for .NET](https://releases.groupdocs.com/merger/net/)
- [购买许可证](https://purchase.groupdocs.com/buy)
- [免费试用](https://releases.groupdocs.com/merger/net/)
- [临时许可证请求](https://purchase.groupdocs.com/temporary-license/)
- [支持论坛](https://forum.groupdocs.com/c/merger/)

---

**最后更新：** 2026-09-26  
**测试版本：** GroupDocs.Merger 23.11 for .NET  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Merger for .NET 合并特定 PDF 页面：综合指南](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [如何使用 GroupDocs.Merger for .NET 从文档中删除页面：分步指南](/merger/net/page-operations/groupdocs-merger-remove-pages-net-tutorial/)
- [如何使用 GroupDocs.Merger for .NET 在文档内移动页面：综合指南](/merger/net/page-operations/move-pages-groupdocs-merger-dotnet/)