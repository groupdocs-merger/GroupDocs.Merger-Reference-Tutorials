---
title: XLSM 文件合并指南
linktitle: XLSM 文件合并指南
second_title: GroupDocs.Merger .NET API
description: 使用 GroupDocs.Merger for .NET 无缝合并 XLSM 文件。以编程方式高效合并 Excel 工作簿。增强您的文档处理能力。
weight: 13
url: /zh/net/spreadsheet-merging/guide-merging-xlsm-files/
---
## 介绍
在本教程中，我们将探讨如何合并 XLSM（Excel 宏启用工作簿）文件。GroupDocs.Merger 是一个功能强大的库，允许开发人员操作文档格式，包括以编程方式合并、拆分和修改文件。
## 先决条件
在开始之前，请确保您具备以下条件：
-  GroupDocs.Merger for .NET：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/merger/net/).
- 开发环境：设置 Visual Studio 或任何兼容的 .NET 开发环境。
- XLSM 文件：准备您想要合并的 XLSM 文件。

## 导入命名空间
首先，在您的 .NET 项目中包含必要的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：定义输出文件夹和文件名
首先定义输出文件夹和合并的 XLSM 文件的名称：
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## 步骤 2：加载和合并 XLSM 文件
接下来，加载源 XLSM 文件并将它们合并为一个文件：
```csharp
//加载源 XLSM 文件
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    //添加另一个 XLSM 文件进行合并
    merger.Join("Your Sample File");
    //合并 XLSM 文件并保存结果
    merger.Save(outputFile);
}
```
## 步骤 3：检查合并完成
最后通知用户合并成功完成并显示输出路径：
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
您已经了解了如何以编程方式合并 XLSM 文件。此库简化了文档操作任务，从而能够在 .NET 应用程序中高效地合并文件。

## 常见问题解答
### GroupDocs.Merger 能处理大型 XLSM 文件吗？
是的，GroupDocs.Merger 可以有效处理大型 XLSM 文件，并且不会出现性能问题。
### 除了 XLSM，GroupDocs.Merger 还支持其他文件格式吗？
是的，GroupDocs.Merger 支持各种文档格式，如 DOCX、PDF、PPTX 等。
### GroupDocs.Merger 是否与 .NET Core 应用程序兼容？
是的，GroupDocs.Merger 与 .NET Framework 和 .NET Core 环境兼容。
### 我可以使用 GroupDocs.Merger 合并加密的 XLSM 文件吗？
是的，GroupDocs.Merger 支持使用正确的凭据合并加密的 XLSM 文件。
### GroupDocs.Merger 是否提供批处理功能？
是的，GroupDocs.Merger 允许批处理同时合并多个 XLSM 文件。