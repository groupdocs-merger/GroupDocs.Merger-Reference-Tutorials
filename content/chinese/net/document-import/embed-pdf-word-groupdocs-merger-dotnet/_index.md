---
date: '2026-10-01'
description: 了解如何使用 GroupDocs.Merger for .NET 将 PDF 嵌入 Word。按照本指南将 PDF 文件作为 OLE 对象添加，提升文档交互性，并保持布局完整。
keywords:
- embed pdf in word
- add pdf to word
- ole object embedding
- insert ole object word
lastmod: '2026-10-01'
og_description: 使用 GroupDocs.Merger for .NET 在 Word 中嵌入 PDF。本教程逐步演示将 PDF 文件作为 OLE
  对象添加，涵盖 setup、code 和 best practices。
og_image_alt: Guide showing how to embed a PDF into a Word document using GroupDocs.Merger
  for .NET
og_title: 使用 GroupDocs.Merger for .NET 在 Word 中嵌入 PDF
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to embed pdf in word with GroupDocs.Merger for .NET. Follow
    this guide to add PDF files as OLE objects, boost document interactivity, and
    keep layouts intact.
  headline: 'Embed PDF in Word Using GroupDocs.Merger for .NET: A Step-by-Step Guide'
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Merger supports various file types. Check [documentation](https://docs.groupdocs.com/merger/net/)
      for the full list.
    question: Can I embed other file formats besides PDF?
  - answer: Use memory‑efficient practices such as processing in chunks and handling
      exceptions effectively.
    question: How do I handle large documents efficiently with GroupDocs.Merger?
  - answer: Absolutely, you can obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
    question: Is there a way to trial this library before purchasing?
  - answer: Ensure compatibility with .NET Core 3.1 or higher.
    question: What are the system requirements for using GroupDocs.Merger on .NET
      Core?
  - answer: Visit [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)
      for assistance.
    question: Where can I find support if I encounter issues?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET document processing
- OLE embedding
- PDF to Word
title: 使用 GroupDocs.Merger for .NET 在 Word 中嵌入 PDF：一步一步指南
type: docs
url: /zh/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/
weight: 1
---

# 在 Word 中嵌入 PDF 使用 GroupDocs.Merger for .NET：一步一步指南

在 Word 文件中嵌入 PDF 可以保持原始格式，同时让读者即时访问源文档。在本教程中，您将学习如何通过使用 GroupDocs.Merger for .NET 插入 OLE（对象链接与嵌入）对象来 **embed pdf in word**。我们将涵盖从安装库到所需代码的全部内容，并提供故障排除技巧和实际案例。

## 快速答案
- **嵌入 PDF 的最简方法是什么？** Use `Merger.ImportDocument` with `OleWordProcessingOptions`.
- **哪个库支持此功能？** GroupDocs.Merger for .NET.
- **我需要许可证吗？** A temporary license works for evaluation; a full license is required for production.
- **我可以添加其他文件类型吗？** Yes – the same method works for DOCX, XLSX, PPTX, and more.
- **它兼容 .NET Core 吗？** Fully supported on .NET Core 3.1+ and .NET 5/6/7.

## 什么是 Word 中的嵌入 PDF？
在 Word 中嵌入 PDF 意味着将 PDF 作为 OLE 对象插入，使文件以图标或预览形式出现在文档中，同时原始 PDF 保持不变。这种方式保留了源 PDF 的布局、字体和图形，读者可以直接从 Word 文档打开嵌入的文件进行参考或进一步编辑。

## 为什么使用 GroupDocs.Merger 的 OLE 对象嵌入？
GroupDocs.Merger 支持 **70+ 输入和输出格式**，并且能够在不将整个文档加载到内存中的情况下处理高达 **500 MB** 的文件，为大型企业工作负载提供快速、内存高效的操作。使用 OLE 嵌入可保持原始 PDF 完整，提供可点击的图标以便快速访问，并确保嵌入内容在不同设备和平台之间可移植。

## 介绍

在 Word 文档中嵌入 PDF 等丰富内容时是否感到困难？本教程将指导您使用 GroupDocs.Merger for .NET 将 OLE（对象链接与嵌入）对象（如 PDF）插入到 Microsoft Word 文档的特定页面。

嵌入对象可以为文档添加动态或外部内容，保持交互性。无论是需要嵌入数据集的报告，还是需要补充文件的演示文稿，此功能都能简化流程。

### 您将学习
- 如何设置并使用 GroupDocs.Merger for .NET  
- 在 Word 文档中嵌入 OLE 对象的逐步指南  
- 关键配置选项和故障排除技巧  

## 前提条件

在实现此功能之前，请确保开发环境已准备好所需的库和设置：

### 必需的库
- **GroupDocs.Merger for .NET** – 一个强大的库，用于操作文档格式。  
- **.NET Framework** 或 **.NET Core/5+** – 支持任何近期版本。

### 环境设置
- Visual Studio（2017 或更高）并支持 C#  
- 对 .NET 中的文件处理和对象操作有基本了解  

### 知识前提
- 熟悉 C# 编程语言  
- 了解如何在 .NET 中使用外部库  

## 设置 GroupDocs.Merger for .NET

要开始使用，您需要安装 GroupDocs.Merger。以下是步骤：

### 安装

**Using .NET CLI:**  
```bash
dotnet add package GroupDocs.Merger
```  

**Using Package Manager Console:**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI:**  
Search for "GroupDocs.Merger" and install the latest version.

### 许可证获取

要使用 GroupDocs.Merger，您可以通过以下方式获取许可证：
- **Free trial** – start with a temporary license to evaluate features.  
- **Temporary license** – obtain this from [此处](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase** – buy a full license for production use at [GroupDocs 购买](https://purchase.groupdocs.com/buy).

### 基本初始化

安装完成后，在 C# 项目中导入库：  
```csharp
using GroupDocs.Merger;
```  

## 实施指南

现在您已经准备就绪，让我们实现嵌入 OLE 对象的功能。

### 如何使用 GroupDocs.Merger for .NET 在 Word 中嵌入 PDF？

加载源 Word 文件 `new Merger("source.docx")`，配置 `OleWordProcessingOptions` 指定 PDF 路径、尺寸和页面位置，然后调用 `ImportDocument` 并 `Save`。此三步流程可在一行代码中将 PDF 作为 OLE 对象嵌入，并将结果写入输出路径。

#### 将 OLE 对象导入 Word 文档

`Merger` 类是 GroupDocs.Merger 用于操作文档的核心引擎，提供合并、拆分以及将外部文件导入为 OLE 对象的方法。

##### 步骤 1：准备文件路径并初始化选项

`OleWordProcessingOptions` 定义 OLE 对象的设置，如文件路径、图标大小和插入位置。定义源 Word 文档、要嵌入的 PDF 以及输出文件的路径，然后创建 `OleWordProcessingOptions` 实例以设置图标大小和页码。

```csharp
string sourceFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.docx");
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "embedded.pdf");
string outputFilePath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "output_sample.docx");

int pageNumberToEmbed = 2; // Page number for the OLE object
OleWordProcessingOptions oleOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumberToEmbed)
{
    Width = 300, // Set width in points
    Height = 300 // Set height in points
};
```  

##### 步骤 2：合并并保存文档

使用源文件创建 `Merger` 实例。调用 `ImportDocument` 方法添加 OLE 对象并保存文档。

```csharp
using (Merger merger = new Merger(sourceFilePath))
{
    merger.ImportDocument(oleOptions);
    merger.Save(outputFilePath); // Save the output document with embedded content
}
```  

### 参数和方法
- **ImportDocument** – adds an external file as an OLE object.  
- **Save** – writes changes to a specified path.  

## 实际应用

嵌入 OLE 对象在多种场景中极为有用：
1. **Business reports** – embed financial datasets for easy reference.  
2. **Technical documentation** – include detailed diagrams or schematics directly in the document.  
3. **Educational materials** – insert supplementary reading, quizzes, or lab instructions without leaving the main handout.  

## 性能考虑

使用 GroupDocs.Merger 时保持应用响应的建议：
- 通过仅嵌入必要的对象来最小化文件大小。  
- 优雅地处理异常，以避免文档操作期间崩溃。  
- 高效管理内存和资源，尤其是在大规模应用中。  

## 结论

您已经学习了如何使用 GroupDocs.Merger for .NET 将 OLE 对象无缝嵌入 Word 文档。此功能可通过直接在文档中集成各种内容类型，显著提升文档的价值。

### 下一步

进一步探索 GroupDocs.Merger 提供的功能，如文档拆分、合并或页面旋转，以在项目中充分利用此强大库。

## 常见问题

**Q: 我可以嵌入除 PDF 之外的其他文件格式吗？**  
A: Yes, GroupDocs.Merger supports various file types. Check [文档](https://docs.groupdocs.com/merger/net/) for the full list.

**Q: 如何使用 GroupDocs.Merger 高效处理大型文档？**  
A: Use memory‑efficient practices such as processing in chunks and handling exceptions effectively.

**Q: 在购买前是否可以试用此库？**  
A: Absolutely, you can obtain a temporary license [此处](https://purchase.groupdocs.com/temporary-license/).

**Q: 在 .NET Core 上使用 GroupDocs.Merger 的系统要求是什么？**  
A: Ensure compatibility with .NET Core 3.1 or higher.

**Q: 如果遇到问题，我可以在哪里获取支持？**  
A: Visit [GroupDocs 支持论坛](https://forum.groupdocs.com/c/merger) for assistance.

## 资源
- **Documentation**: [GroupDocs.Merger Docs](https://docs.groupdocs.com/merger/net/)  
- **API reference**: [GroupDocs API Ref](https://reference.groupdocs.com/merger/net/)  
- **Download GroupDocs.Merger**: [Latest Release](https://releases.groupdocs.com/merger/net/)  
- **Purchase license**: [Buy Now](https://purchase.groupdocs.com/buy)  
- **Free trial**: [Try It](https://releases.groupdocs.com/merger/net/)  
- **Temporary license**: [Acquire Temporary Access](https://purchase.groupdocs.com/temporary-license/)  
- **Additional temporary‑license link**: [此处](https://purchase.groupdocs.com/temporary-license/)  
- **Support and community forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-10-01  
**Tested with:** GroupDocs.Merger 24.2 for .NET  
**Author:** GroupDocs

## 相关教程

- [Embed Ole Objects Groupdocs Merger Net](/merger/net/document-import/embed-ole-objects-groupdocs-merger-net/)
- [Embed Pdf Ole Powerpoint Groupdocs Merger Net](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Add Attachments Pdf Groupdocs Merger Dotnet Tutorial](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)