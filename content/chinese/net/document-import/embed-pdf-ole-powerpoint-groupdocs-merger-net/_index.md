---
date: '2026-09-21'
description: 了解如何使用 GroupDocs.Merger for .NET 将 pdf 嵌入 PowerPoint 作为 OLE 对象。本分步指南展示了确切的
  API 调用和最佳实践。
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: 使用 GroupDocs.Merger for .NET 在 PowerPoint 中嵌入 pdf。请遵循本简明教程添加 OLE 对象、配置选项并避免常见陷阱。
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: 在 PowerPoint 中嵌入 pdf – 使用 GroupDocs.Merger 将 PDF 嵌入为 OLE
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: 如何使用 GroupDocs.Merger for .NET 在 PowerPoint 中将 pdf 嵌入为 OLE
type: docs
url: /zh/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# 在 PowerPoint 中使用 GroupDocs.Merger for .NET 将 PDF 嵌入为 OLE

将 PDF 直接嵌入 PowerPoint 幻灯片可让您保持原始文档完整，同时为观众提供即时访问。在本教程中，您将学习 **如何将 PDF 嵌入 PowerPoint** 作为 OLE 对象，了解所需的 API 选项，并发现提升性能的技巧。

## 快速答案
- **哪个库处理 OLE 嵌入？** GroupDocs.Merger for .NET 提供 `OlePresentationOptions` 类用于此目的。  
- **我需要许可证吗？** 试用许可证可用于开发；生产环境需要完整许可证。  
- **我可以嵌入多个 PDF 吗？** 可以——对每个目标幻灯片重复导入步骤。  
- **支持哪些 .NET 版本？** .NET Framework 4.5+、.NET Core 3.1+、.NET 5/6/7。  
- **该过程内存高效吗？** API 采用流式处理文件，即使是数百页的 PDF 也能在不将整个文件加载到内存中的情况下嵌入。

## 什么是将 PDF 嵌入 PowerPoint？
**embed pdf in powerpoint** 指将 PDF 文件作为 OLE（对象链接与嵌入）对象插入，使幻灯片显示图标或预览，双击后在默认查看器中打开原始 PDF。此方式保留源文档的格式、超链接和安全设置。

## 为什么使用 OLE 嵌入而不是转换 PDF？
嵌入可保持原始文件大小和布局不变，消除转换错误，并且可以在不重新导出演示文稿的情况下更新源 PDF。GroupDocs.Merger 支持 **50+ 输入和输出格式**，并可在流式传输数据的同时将数百兆字节的 PDF 嵌入，内存使用保持在 100 MB 以下。

## 前提条件
- Visual Studio 2022（或任何兼容 .NET 的 IDE）  
- .NET Framework 4.5+ 或 .NET Core 3.1+ 运行时  
- 有效的 GroupDocs.Merger for .NET 许可证（试用或商业）  
- 一个 PowerPoint (.pptx) 文件以及您想要嵌入的 PDF  

## 设置 GroupDocs.Merger for .NET

### 如何安装库？
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – 搜索 “GroupDocs.Merger” 并点击 **Install** 以获取最新版本。

### 如何获取许可证？
- **Free trial** – 在 GroupDocs 网站注册以获取临时许可证密钥。  
- **Temporary license** – 如需超过 30 天的试用，可申请延长试用。  
- **Full purchase** – 购买商业许可证以实现无限制的生产使用。

### 如何初始化 API？
`Merger` 是提供文档操作（如导入、合并和转换）的主要类。  
在 C# 文件顶部添加所需的 `using` 指令，并使用许可证文件路径创建 `Merger` 实例：

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## 实施指南

### 如何将 PDF 嵌入 PowerPoint 作为 OLE？
加载演示文稿，配置 OLE 选项，然后调用导入方法——整个操作分为三个逻辑步骤完成。

**Step 1 – define file locations**  
指定源 PDF、目标 PowerPoint 文件以及保存修改后演示文稿的文件夹的绝对或相对路径。

**Step 2 – configure the OLE options**  
`OlePresentationOptions` 类告诉 GroupDocs.Merger 要嵌入哪个文件、在哪张幻灯片以及在何坐标。它还允许您设置嵌入对象的宽度、高度和显示模式。

**Step 3 – import the PDF**  
`ImportDocument` 是 Merger API 的调用，它使用提供的选项将 OLE 对象插入 PowerPoint 文件。该方法以流式方式将 PDF 写入幻灯片，无需将整个文档加载到内存中。

#### 定义锚点
- `OlePresentationOptions` 是定义嵌入文件、位置（X/Y）、大小以及目标幻灯片编号的选项容器。  
- `ImportDocument` 是 Merger API 的调用，它使用提供的选项将 OLE 对象插入 PowerPoint 文件。

## 常用配置参数
- **SlideNumber** – 将承载 OLE 对象的幻灯片的 1 基索引。  
- **XCoordinate / YCoordinate** – 从幻灯片左上角起以点为单位测量的位置。  
- **Width / Height** – OLE 占位符的尺寸；设为 0 可使用默认大小。  
- **ObjectName** – 在 PowerPoint 中选中对象时显示的可选友好名称。

## 实际应用
将 PDF 作为 OLE 对象嵌入在许多真实场景中大放异彩：

1. **Corporate briefings** – 附加最新的财务报告而不增加演示文稿的体积。  
2. **Academic lectures** – 在幻灯片摘要旁提供完整的研究论文全文。  
3. **Project status updates** – 嵌入实时项目计划，利益相关者可打开查看细节。  
4. **Sales decks** – 包含产品规格表，销售代表可按需打开。  
5. **Technical workshops** – 展示工程师可即时检查的原理图或数据表。

## 性能考虑
为了保持嵌入过程快速且内存友好：

- **Stream files** – GroupDocs.Merger 读取和写入流，即使是 200 页的 PDF 也只使用不到 100 MB 的 RAM。  
- **Batch process** – 在更新大量演示文稿时，复用单个 `Merger` 实例并及时关闭流。  
- **Resize large PDFs** – 如发现加载缓慢，可压缩或下采样源 PDF 中的图像。

## 常见问题

**Q: 我可以将多个 PDF 嵌入同一个演示文稿吗？**  
A: 可以。对每个 PDF 调用 `ImportDocument`，并指定不同的 `SlideNumber` 或同一幻灯片上的不同位置。

**Q: 我可以嵌入多大的 PDF？**  
A: 实际限制取决于服务器内存；已测试在流式处理时可嵌入高达 500 MB 的文件而无问题。

**Q: OLE 对象会保留超链接等交互元素吗？**  
A: 当然。嵌入的 PDF 在默认查看器中打开，保留所有内部链接和书签。

**Q: 如果 PDF 设置了密码怎么办？**  
A: 在调用 `ImportDocument` 前，通过 `OlePresentationOptions` 的 `Password` 属性提供密码。

**Q: 嵌入的对象能在所有 PowerPoint 版本上工作吗？**  
A: OLE 格式受 PowerPoint 2007 及以后版本（包括 Office 365）支持。

## 结论
您现在拥有使用 GroupDocs.Merger for .NET 将 **embed pdf in powerpoint** 作为 OLE 对象的完整、可投产工作流。通过流式文件、配置 `OlePresentationOptions` 并调用 `ImportDocument`，您可以在保持低内存占用的同时，为演示文稿添加原始 PDF 并保留所有交互功能。探索 Merger 的其他功能，如合并幻灯片、格式转换和水印，以进一步自动化文档流水线。

---

**Last Updated:** 2026-09-21  
**Tested With:** GroupDocs.Merger 23.12 for .NET  
**Author:** GroupDocs  

## 资源
- **Documentation:** [GroupDocs.Merger for .NET Documentation](https://docs.groupdocs.com/merger/net/)  
- **API reference:** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **Download:** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **Purchase:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Free trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Temporary license:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## 相关教程

- [Embed PDF in Word Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)  
- [Loading PDF from URL in .NET Using GroupDocs.Merger: A Comprehensive Guide](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)  
- [How to Retrieve Document Information Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)