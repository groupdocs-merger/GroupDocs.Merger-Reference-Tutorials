---
date: '2026-09-21'
description: 了解如何使用 GroupDocs.Merger for .NET 将 PDF 嵌入 Excel 电子表格，提升数据展示和功能性。
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: 了解如何使用 GroupDocs.Merger for .NET 在 Excel 中嵌入 PDF。按照逐步说明，查看快速答案，避免常见陷阱。
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: 如何使用 GroupDocs.Merger for .NET 在 Excel 中嵌入 PDF
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: 如何使用 GroupDocs.Merger for .NET 在 Excel 中嵌入 PDF
type: docs
url: /zh/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# 如何在 Excel 中嵌入 PDF 使用 GroupDocs.Merger for .NET

## 介绍

在 Excel 中嵌入 PDF 可让您将支持文档（如合同、报告或规范）直接保存在数据所在的位置。使用 **GroupDocs.Merger for .NET**，您只需几行代码即可向单元格添加 OLE 对象，将普通电子表格转换为交互式、独立的工作簿。本教程将带您了解从安装到故障排除的全部内容。

**您将学习**

- 如何在 C# 项目中设置 GroupDocs.Merger for .NET  
- 将 PDF（或任何 OLE 兼容文件）嵌入 Excel 单元格的具体步骤  
- 配置选项、性能技巧以及常见陷阱  

在开始之前，让我们确认您已准备好所有必要条件。

## 快速答案
- **我可以嵌入任何文件类型吗？** 是的——任何作为 OLE 对象支持的格式（PDF、Word、图像等）。  
- **开发需要许可证吗？** 免费试用可用于测试；生产环境需要永久许可证。  
- **支持哪些 .NET 版本？** .NET Framework 4.5+、.NET Core 3.1+、.NET 5/6/7+。  
- **Excel 文件大小会显著增加吗？** 仅会增加嵌入文档的大小；为获得最佳性能，请将文件保持在几 MB 以下。  
- **OLE 对象的数量有限制吗？** 实际上没有限制，但非常大的工作簿可能会影响加载时间。

## 什么是将 PDF 嵌入 Excel？

在 Excel 中嵌入 PDF 会将整个 PDF 作为 OLE 对象插入，可直接从电子表格打开。用户点击图标即可在不离开 Excel 的情况下查看原始文档。此方法保留原始布局，便于快速引用，并消除管理单独文件的需求。嵌入的 PDF 像其他 OLE 对象一样工作，用户双击图标即可启动 PDF 查看器，同时仍在 Excel 环境中。

## 为什么在 Excel 中嵌入 OLE 对象？

GroupDocs.Merger 支持 **120 多种输入和输出格式**，并且可以在不将整个文件加载到内存中的情况下嵌入对象，从而实现对数百页 PDF 的快速处理。这减少了对单独文件仓库的需求，并将相关数据保持在一起。它还简化了版本控制，确保所有相关文档随工作簿一起传递，提升团队协作。

## 前提条件

- **GroupDocs.Merger for .NET**（最新 NuGet 包）  
- **.NET Framework** 4.5+ **或** **.NET Core/5+/6+**  
- Visual Studio 2022 或更高版本  
- 基本的 C# 知识以及对文件 I/O 的熟悉  

## 设置 GroupDocs.Merger for .NET

### 安装

使用以下任一方法添加包：

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
搜索 “GroupDocs.Merger” 并安装最新版本。

### 获取许可证

1. **免费试用** – 在不花费的情况下测试库。  
2. **临时许可证** – 在 [temporary‑license page](https://purchase.groupdocs.com/temporary-license/) 请求临时许可证。  
3. **购买** – 考虑在 [GroupDocs purchase page](https://purchase.groupdocs.com/buy) 购买许可证。  

### 基本初始化

`Merger` 是所有操作的入口点。  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## 如何在 Excel 中嵌入 OLE 对象？

加载源工作簿，配置 OLE 选项，然后让 `Merger` 插入对象。以下章节为您提供简洁、可直接运行的工作流。

### 功能概述
嵌入 OLE 对象可让您在单元格中存储完整的 PDF，保留原始布局，并实现 Excel 中的一键访问。

### 步骤实现

#### 1. 设置路径和页码
指定电子表格、要嵌入的文件以及目标单元格地址。

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. 配置 OleSpreadsheetOptions
`OleSpreadsheetOptions` 定义 OLE 对象在工作表中的放置位置以及其图标的显示方式。  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. 初始化 Merger 并执行嵌入
`Merger` 类负责实际插入。调用后，工作簿将包含 OLE 图标。

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### 常见故障排除提示
- 验证所有文件路径是绝对路径或相对于可执行文件正确解析。  
- 确保您指定的页码在源 PDF 中存在；否则会抛出异常。  
- 如果嵌入的对象未显示，请确认目标 Excel 版本支持 OLE（大多数现代版本都支持）。

## 实际应用

在 Excel 中嵌入 PDF 可用于：

1. **财务报告** – 将审计报表直接附加在汇总表旁边。  
2. **项目文档** – 在主跟踪器中保留设计规范、风险分析或合同。  
3. **培训仪表板** – 嵌入用户手册或政策 PDF，供员工快速参考。  

## 性能考虑因素

- **文件大小** – 将嵌入的 PDF 保持在 5 MB 以下，以避免工作簿膨胀。  
- **内存使用** – `GroupDocs.Merger` 使用流式处理数据，即使源文件很大，内存消耗也保持低。  
- **释放对象** – 始终对 `Merger` 实例调用 `Dispose()`，及时释放文件句柄。  

## 常见问题

**Q: 什么是 OLE 对象？**  
A: OLE（对象链接与嵌入）对象将另一个文件（PDF、Word、图像等）存储在宿主文档中，允许就地编辑或打开。

**Q: 我可以在其他 Office 格式中嵌入 OLE 对象吗？**  
A: 可以——GroupDocs.Merger 也支持 Word、PowerPoint 和 Visio 文件。

**Q: 如何处理受密码保护的 PDF？**  
A: 在创建 `OleSpreadsheetOptions` 实例时提供密码；库会自动解密文件。

**Q: 嵌入的 PDF 有大小限制吗？**  
A: 技术上没有硬性限制，但超过 10 MB 的文件可能显著增加工作簿加载时间。

**Q: 在哪里可以找到更多示例？**  
A: 访问官方 [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) 获取更多代码示例和 API 参考。

## 附加资源
- **文档**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **API 参考**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **下载**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **许可证购买**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **免费试用**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **临时许可证**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **支持论坛**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**最后更新：** 2026-09-21  
**测试环境：** GroupDocs.Merger 23.12 for .NET  
**作者：** GroupDocs

## 相关教程

- [在 PowerPoint 中使用 GroupDocs.Merger for .NET 将 PDF 作为 OLE 嵌入&#58; 一步一步指南](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [在 Word 中使用 GroupDocs.Merger for .NET 嵌入 PDF&#58; 一步一步指南](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [.NET 中使用 GroupDocs.Merger 从 URL 加载 PDF&#58; 综合指南](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}