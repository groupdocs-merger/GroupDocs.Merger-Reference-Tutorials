---
title: 合并 XLSX 文件
linktitle: 合并 XLSX 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 在 .NET 中轻松合并 XLSX 文件。按照此分步教程进行无缝文档管理。
weight: 14
url: /zh/net/spreadsheet-merging/merging-xlsx-files/
type: docs
---
# 合并 XLSX 文件

## 介绍
在 .NET 应用程序的文档操作和管理领域，GroupDocs.Merger 是一款功能强大的工具，可无缝合并各种文件格式。本教程深入探讨了 XLSX (Excel) 文件的合并，并提供了有关如何在 .NET 环境中有效合并电子表格文件的分步指南。无论您是经验丰富的开发人员还是刚开始使用 .NET，本教程都将为您提供将文件合并功能集成到项目中所需的知识。
## 先决条件
在深入学习本教程之前，请确保您已设置以下先决条件：
1. Visual Studio：安装 Visual Studio，一个用于 .NET 开发的综合集成开发环境 (IDE)。
2. GroupDocs.Merger for .NET：下载并安装 GroupDocs.Merger for .NET。您可以从以下位置获取该库[此链接](https://releases.groupdocs.com/merger/net/).
3. 示例 XLSX 文件：准备几个您打算在本教程中合并的 XLSX 文件。

## 导入命名空间
首先导入访问 GroupDocs.Merger 功能所需的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：设置输出目录
定义合并的 XLSX 文件将保存的输出目录：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xlsx");
```
## 步骤 2：加载并合并 XLSX 文件
初始化合并器并加载源 XLSX 文件以开始合并：
```csharp
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    //添加另一个 XLSX 文件进行合并
    merger.Join("Your Sample File");
    //合并 XLSX 文件并保存结果
    merger.Save(outputFile);
}
```
## 第 3 步：显示完成消息
合并过程成功完成后，显示一条指示输出目录的消息：
```csharp
Console.WriteLine("\nXLSX files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们探讨了如何合并 XLSX 文件。通过遵循概述的步骤，您可以将文件合并功能无缝集成到 .NET 应用程序中，从而提高文档管理效率。

## 常见问题解答
### GroupDocs.Merger 除了处理 XLSX 之外还能处理其他文件格式吗？
是的，GroupDocs.Merger 支持合并各种文件格式，例如 DOCX、PPTX、PDF 等。
### GroupDocs.Merger 是否与 .NET Core 应用程序兼容？
是的，GroupDocs.Merger 可以与 .NET Framework 和 .NET Core 项目一起使用。
### 在哪里可以找到 GroupDocs.Merger 的详细文档？
提供详细文档[这里](https://tutorials.groupdocs.com/merger/net/).
### GroupDocs.Merger 是否提供免费试用？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).
### 我如何获得 GroupDocs.Merger 的支持？
如需支持和讨论，请访问[GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger/32).