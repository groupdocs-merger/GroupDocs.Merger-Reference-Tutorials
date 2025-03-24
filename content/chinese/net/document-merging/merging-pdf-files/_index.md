---
title: 合并 PDF 文件
linktitle: 合并 PDF 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 在 .NET 中以编程方式合并 PDF 文件，以实现无缝文档管理。
weight: 19
url: /zh/net/document-merging/merging-pdf-files/
---
## 介绍
在文档管理和操作领域，合并 PDF 文件是开发人员遇到的常见任务。 GroupDocs.Merger for .NET 提供了一个强大的解决方案，可在 .NET 应用程序中无缝组合 PDF 文档。本教程将指导您完成使用 GroupDocs.Merger 合并 PDF 文件的过程，展示逐步实施和使用。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
- Visual Studio 安装在您的系统上。
- 对 C# 编程语言有基本了解。
- 访问 GroupDocs.Merger for .NET 库。

## 导入命名空间
首先在 C# 项目中导入必要的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 第 1 步：初始化输出文件夹
设置将保存合并的 PDF 文件的输出目录：
```csharp
string outputFolder = "Your_Output_Directory_Path";
```
## 第 2 步：定义输出文件路径
将输出文件夹路径与合并 PDF 文件的所需名称相结合：
```csharp
string outputFile = Path.Combine(outputFolder, "merged.pdf");
```
## 第 3 步：加载源 PDF 文件
使用 GroupDocs.Merger 加载要合并的源 PDF 文件：
```csharp
using (var merger = new GroupDocs.Merger.Merger("path_to_first_pdf"))
{
    //添加另一个 PDF 文件进行合并
    merger.Join("path_to_second_pdf");
    
    //合并 PDF 文件并保存结果
    merger.Save(outputFile);
}
```
## 步骤4：执行合并操作
通过使用 GroupDocs.Merger 合并并保存 PDF 文件来执行合并操作：
```csharp
Console.WriteLine("\nPDF files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Merger for .NET 合并 PDF 文件。通过遵循这些步骤，您可以在 .NET 应用程序中将多个 PDF 文档无缝合并为一个文件。

## 常见问题解答
### GroupDocs.Merger 能有效处理大型 PDF 文件吗？
是的，GroupDocs.Merger 经过优化，可以有效处理大型 PDF 文件，确保在文档操作任务期间获得最佳性能。
### GroupDocs.Merger 是否支持受密码保护的 PDF 文件？
是的，只要您拥有必要的权限，GroupDocs.Merger 支持合并受密码保护的 PDF 文件。
### 我可以使用 GroupDocs.Merger 合并非 PDF 文档格式吗？
不，GroupDocs.Merger 是专门为 PDF 操作和合并任务而设计的。
### GroupDocs.Merger 是否与 .NET Core 应用程序兼容？
是的，GroupDocs.Merger 与 .NET Framework 和 .NET Core 环境兼容。
### GroupDocs.Merger 在合并期间是否保留书签和注释？
是的，GroupDocs.Merger 可确保在合并 PDF 文件时保留书签、注释和其他文档属性。