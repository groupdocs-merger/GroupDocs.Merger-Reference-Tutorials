---
title: 合并 DOTX 文件
linktitle: 合并 DOTX 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 轻松合并 .NET 中的 DOTX 文件。增强您的文档处理能力。
type: docs
weight: 15
url: /zh/net/document-merging/merge-dotx-files/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Merger for .NET 合并 DOTX（Word 模板）文件。GroupDocs.Merger 是一个功能强大的 API，使开发人员能够在 .NET 应用程序中无缝操作各种文档格式。通过利用此 API，您只需几行代码即可将多个 DOTX 文件高效地合并为一个文档。
## 先决条件
在深入学习本教程之前，请确保您已具备以下条件：
- 您的机器上安装了 Visual Studio
- 已安装 .NET SDK（兼容版本）
- 已安装 GroupDocs.Merger for .NET（请参阅[安装指南](https://reference.groupdocs.com/merger/net/)了解详情）
- C# 编程基础知识

## 导入命名空间
首先，将必要的命名空间导入到你的 C# 项目中：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：设置输出目录和文件名
首先，定义合并后的DOTX文件的输出目录路径和名称。
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.dotx");
```
代替`"YourOutputDirectory"`与您想要保存合并的 DOTX 文件的路径。
## 第 2 步：合并 DOTX 文件
接下来，使用 GroupDocs.Merger 将多个 DOTX 文件合并为一个文档。
```csharp
//加载源 DOTX 文件
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    //添加另一个 DOTX 文件进行合并
    merger.Join("Your Sample File");
    
    //合并 DOTX 文件并保存结果
    merger.Save(outputFile);
}
Console.WriteLine("\nDOTX files merge completed successfully. \nCheck output in {0}", outputFolder);
```
在此代码片段中：
- `"Your Sample File"`和`"Your Sample File"`表示要合并的 DOTX 文件的路径。将其替换为您的实际文件路径。
- `merger.Join()`用于将额外的 DOTX 文件添加到合并中。
- `merger.Save()`合并 DOTX 文件并将合并结果保存到指定`outputFile`小路。

## 结论
在本教程中，我们介绍了如何使用 GroupDocs.Merger for .NET 合并 DOTX 文件。通过执行这些步骤并利用 GroupDocs.Merger 的强大功能，您可以在 .NET 应用程序中高效地操作 Word 模板文件。

## 常见问题解答
### GroupDocs.Merger 可以合并除 DOTX 之外的其他文档格式吗？
是的，GroupDocs.Merger 支持合并各种文档格式，如 DOCX、XLSX、PPTX、PDF 等。
### GroupDocs.Merger 与 .NET Core 兼容吗？
是的，GroupDocs.Merger 与 .NET Framework 和 .NET Core 兼容。
### 在哪里可以找到有关 GroupDocs.Merger 的其他支持或文档？
您可以参考[GroupDocs.Merge 文档](https://reference.groupdocs.com/merger/net/)详细的API参考和使用示例。
### GroupDocs.Merger 是否提供免费试用？
是的，您可以访问[免费试用版](https://releases.groupdocs.com/)评估 GroupDocs.Merger。
### 如何购买 GroupDocs.Merger 的许可证？
您可以从以下位置购买许可证[集团文档网站](https://purchase.groupdocs.com/buy)根据您的使用要求。