---
title: 合并 XLS 文件
linktitle: 合并 XLS 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 在 .NET 中合并 Excel 文件以实现无缝文档操作。请按照我们的分步教程进行操作。
weight: 11
url: /zh/net/spreadsheet-merging/merging-xls-files/
---

# 合并 XLS 文件

## 介绍
在本教程中，我们将探讨如何合并 XLS（Excel）文件。GroupDocs.Merger 是一个功能强大的文档操作 API，使开发人员能够在其 .NET 应用程序中轻松合并、拆分、重新排列和操作文档。具体来说，我们将重点介绍如何使用 GroupDocs.Merger 的直观方法逐步合并 XLS 文件。
## 先决条件
在开始之前，请确保您已设置以下先决条件：
- Visual Studio：在您的机器上安装 Visual Studio。
-  GroupDocs.Merger for .NET：从以下网址下载并安装 GroupDocs.Merger for .NET[这里](https://releases.groupdocs.com/merger/net/).
- .NET Framework：确保您已安装.NET 框架。
- 示例 XLS 文件：准备您想要合并的 XLS 文件。

## 导入命名空间
首先导入在项目中使用 GroupDocs.Merger 所需的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：初始化输出目录
首先，指定要保存合并的 XLS 文件的目录：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## 第 2 步：加载并合并 XLS 文件
现在，让我们使用 GroupDocs.Merger 加载并合并 XLS 文件：
```csharp
//加载源 XLS 文件
using (var merger = new Merger("Your Sample File"))
{
    //添加另一个要合并的 XLS 文件
    merger.Join("Your Sample File");
    
    //合并 XLS 文件并保存结果
    merger.Save(outputFile);
}
```
## 步骤3：显示输出位置
最后，显示一条消息，指示合并的 XLS 文件的完成和位置：
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们学习了如何合并 XLS 文件。通过遵循提供的步骤，您可以在 .NET 应用程序中以编程方式有效地组合多个 Excel 文件。

## 常见问题解答
### GroupDocs.Merger 是否与其他文档格式兼容？
是的，GroupDocs.Merger 支持各种文档格式，例如 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Merger 拆分文档吗？
绝对地！ GroupDocs.Merger 允许您根据需要拆分文档。
### 在哪里可以找到有关 GroupDocs.Merger 的更多资源和支持？
您可以浏览文档并提出问题[集团文档论坛](https://forum.groupdocs.com/c/merger/32).
### GroupDocs.Merger 是否有免费试用版？
是的，你可以从[免费试用](https://releases.groupdocs.com/)来评估其功能。
### 如何购买 GroupDocs.Merger 的许可证？
参观[购买页面](https://purchase.groupdocs.com/buy)获取满足您需求的许可证。