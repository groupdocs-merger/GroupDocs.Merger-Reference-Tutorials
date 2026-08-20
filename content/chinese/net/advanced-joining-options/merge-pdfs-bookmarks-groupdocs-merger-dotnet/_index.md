---
date: '2026-08-20'
description: 了解如何使用 GroupDocs.Merger for .NET 合并带书签的 pdfs，包括设置、code examples 和 best
  practices，以合并 PDF documents。
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: 了解如何使用 GroupDocs.Merger for .NET 合并带书签的 pdfs。遵循 step‑by‑step code，将
  PDF documents 合并，同时保留 navigation。
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: 如何使用 GroupDocs.Merger for .NET 合并带书签的 pdfs
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
title: 如何使用 GroupDocs.Merger for .NET 合并带书签的 pdfs
type: docs
url: /zh/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# 如何使用 GroupDocs.Merger for .NET 合并带书签的 PDF

合并多个 PDF 文件并保持其原始书签完整可以为您节省数小时的手动重新组织工作。在本教程中，您将学习如何使用 GroupDocs.Merger for .NET **合并带书签的 PDF**，从项目设置到完整的生产就绪代码示例。

## 快速答案
- **哪个库支持保留书签的合并？** GroupDocs.Merger for .NET.  
- **我可以一次合并超过两个 PDF 吗？** 是的 – 根据需要添加任意数量的源文件。  
- **开发需要许可证吗？** 免费试用可用于测试；生产环境需要永久许可证。  
- **支持 .NET Core 吗？** 当然 – 该库兼容 .NET Core、.NET 5/6 以及完整的 .NET Framework。  
- **它能处理的最大文件大小是多少？** 每个文档最高可达 2 GB，处理时无需将整个文件加载到内存中。

## 什么是合并带书签的 PDF？

**合并带书签的 PDF** 是指将多个 PDF 文档合并为一个文件，同时保持每个源文档的书签层级结构完整。生成的 PDF 保留原始的导航结构，允许读者直接跳转到来自各个单独文件的章节，这对于大型报告或汇编手册至关重要。

## 为什么要合并带书签的 PDF？

在合并 PDF 时保留书签可提升合并文档的导航体验，让用户无需滚动整个文件即可快速定位特定章节或节段。GroupDocs.Merger 保持原始的大纲层级，减少手动重新组织的工作量，并支持高达 2 GB 的大文件且占用内存极少，使其非常适合企业级工作流。

## 前提条件
- **.NET Core SDK**（3.1 或更高）或 **.NET Framework**（4.6.1+）。  
- **Visual Studio 2022** 或任何支持 .NET 开发的 IDE。  
- 基础的 C# 知识以及对文件 I/O 的了解。  

## 为 .NET 设置 GroupDocs.Merger

### 安装
使用以下命令之一将库添加到您的项目中：

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
- 在 “GroupDocs.Merger” 中搜索并安装最新版本。

### 获取许可证
- **免费试用：** 从 [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) 页面下载。  
- **临时许可证：** 通过 [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/) 获取。  
- **正式许可证：** 在 [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) 购买。  

### 基本初始化
`Merger` 类是所有合并操作的入口点。  
```  
```csharp
using GroupDocs.Merger;
```  
```  
此命名空间让您能够访问完整的 PDF 操作功能集。

## 在 .NET 中合并带书签的 PDF

加载主 PDF，配置书签处理，添加其他文件，并保存结果 —— 只需几行简洁的代码。

**直接回答（40‑70 字）：**  
创建一个使用首个 PDF 的 `Merger` 实例，启用 `PdfJoinOptions.UseBookmarks`，通过 `Join` 添加每个后续 PDF，最后调用 `Save` 写入合并后的文件。此方法保留所有原始书签层级，并在一次遍历中完成，最小化内存消耗。

### 步骤 1：定义目录路径
设置源文件夹和输出文件夹，以便代码能够定位要合并的 PDF。  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### 步骤 2：加载主 PDF
`Merger` 代表您将向其追加其他文档的主文件。  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### 步骤 3：配置保留书签的选项
`PdfJoinOptions` 控制合并的行为；`UseBookmarks` 标志指示引擎保留现有书签。  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### 步骤 4：添加额外的 PDF
对每个额外文件调用 `Join`。库会自动将它们的书签树合并到主文档的大纲下。  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### 步骤 5：保存合并后的 PDF
指定输出路径和格式；库会写入一个保留所有书签条目的单一 PDF。  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## 常见问题及解决方案
- **缺少书签：** 确认在 `PdfJoinOptions` 中设置 `UseBookmarks = true`。  
- **路径错误：** 使用 `Path.Combine` 并在合并前检查文件是否存在。  
- **大文件导致内存激增：** 顺序处理 PDF，并在每次保存后释放 `Merger` 对象。  

## 实际应用场景
1. **合并财务报告** – 通过书签让季度章节即时可达。  
2. **课程材料包** – 合并讲义 PDF，同时为学生保留章节导航。  
3. **项目文档捆绑** – 将设计规范、测试计划和发布说明合并为单个可搜索的文件。  

## 性能考虑因素
- 合并超过 20 个 PDF 时一次处理一个文件，以保持低内存使用。  
- 使用最新的 .NET 运行时（例如 .NET 6）以获得最佳的 JIT 编译和垃圾回收效率。  
- 对于大于 500 MB 的 PDF，使用 `MergerSettings` 启用流式模式，以避免将整个文档加载到内存中。  

## 常见问答

**Q: 什么是 GroupDocs.Merger？**  
A: GroupDocs.Merger 是一个 .NET 库，允许您以编程方式合并、拆分、旋转以及其他方式操作 PDF 和其他文档格式。

**Q: 我可以一次合并超过两个 PDF 文件吗？**  
A: 可以 – 通过重复调用 `Join` 或传入文件路径集合，在一次操作中合并任意数量的 PDF。

**Q: 如何处理生产环境的许可证？**  
A: 从 GroupDocs 购买页面获取永久许可证；试用许可证仅用于评估，且在 30 天后过期。

**Q: 我的合并 PDF 没有书签——出了什么问题？**  
A: 确保在 `PdfJoinOptions` 中将 `UseBookmarks` 设置为 `true`，并且每个源 PDF 在合并前确实包含书签。

**Q: 该库兼容 .NET Core 和 .NET Framework 吗？**  
A: 完全兼容 – 支持 .NET Core 3.1+、.NET 5/6 以及完整的 .NET Framework 4.6.1+。

## 资源
- [文档](https://docs.groupdocs.com/merger/net/)  
- [API 参考](https://reference.groupdocs.com/merger/net/)  
- [下载 GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [购买许可证](https://purchase.groupdocs.com/buy)  
- [免费试用版](https://releases.groupdocs.com/merger/net/)  
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)  
- [支持论坛](https://forum.groupdocs.com/c/merger/)  

---

**最后更新：** 2026-08-20  
**测试环境：** GroupDocs.Merger 23.11 for .NET  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Merger for .NET 合并特定 PDF 页面：完整指南](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [如何使用 GroupDocs.Merger for .NET 轻松合并文档：完整指南](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [使用 GroupDocs.Merger for .NET 向 PDF 添加附件：分步指南](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)