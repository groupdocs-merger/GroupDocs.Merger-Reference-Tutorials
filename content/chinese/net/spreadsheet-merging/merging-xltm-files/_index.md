---
title: 合并 XLTM 文件
linktitle: 合并 XLTM 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何以编程方式合并 XLTM 文件。带有代码示例的分步指南。
weight: 16
url: /zh/net/spreadsheet-merging/merging-xltm-files/
---

# 合并 XLTM 文件

## 介绍
在本教程中，我们将探讨如何合并 XLTM（Excel 启用宏的模板）文件。 GroupDocs.Merger for .NET 是一个功能强大的库，使开发人员能够以编程方式操作和合并各种文档格式。本指南将引导您使用 C# 逐步完成合并 XLTM 文件的过程。
## 先决条件
在开始之前，请确保您具备以下先决条件：
- Visual Studio 安装在您的系统上。
- C# 编程基础知识。
- 安装了 .NET 库的 GroupDocs.Merger。您可以从以下位置下载：[这里](https://releases.groupdocs.com/merger/net/).
- 访问要合并的 XLTM 文件。

## 导入命名空间
首先将必要的命名空间导入到您的 C# 项目中。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

现在，让我们深入研究合并 XLTM 文件。
## 步骤 1：初始化输出目录
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xltm");
```
代替`"Your Output Directory"`以及要保存合并的 XLTM 文件的路径。
## 第 2 步：合并 XLTM 文件
```csharp
//加载源 XLTM 文件
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    //添加另一个 XLTM 文件进行合并
    merger.Join("Your Sample File");
    //合并 XLTM 文件并保存结果
    merger.Save(outputFile);
}
```
在此代码片段中：
- “您的示例文件”和“您的示例文件”代表输入 XLTM 文件的路径。确保将它们替换为实际的文件路径。
## 步骤3：显示输出位置
```csharp
Console.WriteLine("\nXLTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
此代码将显示一条消息，指示合并操作已成功完成以及输出目录路径。

## 结论
通过学习本教程，您已经了解了如何合并 XLTM 文件。该库提供了广泛的文档操作功能，为开发人员提供了强大的工具集，用于以编程方式处理文档相关任务。

## 常见问题解答
### GroupDocs.Merger 可以合并除 XLTM 之外的其他文档格式吗？
是的，GroupDocs.Merger 支持合并各种文档格式，例如 DOCX、XLSX、PPTX、PDF 等。
### GroupDocs.Merger 用于商业用途需要许可证吗？
是的，您需要有效的许可证才能在商业环境中使用 GroupDocs.Merger。您可以获得许可证[这里](https://purchase.groupdocs.com/buy).
### GroupDocs.Merger 是否有免费试用版？
是的，您可以免费试用 GroupDocs.Merger[这里](https://releases.groupdocs.com/).
### 在哪里可以找到 GroupDocs.Merger 的文档？
您可以参考 GroupDocs.Merger 的完整文档[这里](https://tutorials.groupdocs.com/merger/net/).
### 我可以在哪里获得 GroupDocs.Merger 的技术支持？
如需技术帮助和支持，请访问 GroupDocs.Merger 论坛[这里](https://forum.groupdocs.com/c/merger/32).